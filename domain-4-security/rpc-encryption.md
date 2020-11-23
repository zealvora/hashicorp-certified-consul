
#### Step 1: Initialize Built-In CA
```sh
consul tls ca create
```
#### Step 2: Create Server Certificates:
```sh
consul tls cert create -server
```
#### Step 3: Copy the CA Certificate to client
```sh
base64 -i consul-agent-ca.pem (server)
cd /tmp (client)
nano tmp.txt (Paste the base64 encoded and save)
cat tmp.txt | base64 -d > /etc/consul.d/consul-agent-ca.pem
```
#### Step 4: Configure Server Configuration:
```sh
cd /etc/consul.d
nano consul.hc
```
```sh
verify_incoming = true,
verify_outgoing = true,
verify_server_hostname = true,
ca_file = "/etc/consul.d/consul-agent-ca.pem",
cert_file = "/etc/consul.d/dc1-server-consul-0.pem",
key_file = "/etc/consul.d/dc1-server-consul-0-key.pem",
auto_encrypt {
  allow_tls = true
}
```
```sh
chown -R consul.consul .
systemctl start consul
```
#### Step 5: Configure Client  Configuration:
```sh
cd /etc/consul.d
nano consul.hc
```
```sh
verify_incoming = false,
verify_outgoing = true,
verify_server_hostname = true,
ca_file = "consul-agent-ca.pem",
auto_encrypt = {
  tls = true
}
```
```sh
chown -R consul.consul .
systemctl start consul
```
#### Step 6: Verfication:
```sh
tcpdump -i any port 8300 -vv -X
consul kv get sensitive-data
```
