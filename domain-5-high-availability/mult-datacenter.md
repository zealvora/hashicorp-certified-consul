
#### Server 1:
```sh
data_dir =  "/etc/consul.d/consul-dir"
bind_addr = "134.209.155.89"
client_addr = "0.0.0.0"
bootstrap_expect = 1
node_name = "consul-server"
ui = true
server = true
datacenter = "India"
```
#### Server 2:
```sh
data_dir =  "/etc/consul.d/consul-dir"
bind_addr = "165.22.222.190"
client_addr = "0.0.0.0"
bootstrap_expect = 1
node_name = "consul-server-2"
ui = true
server = true
datacenter = "Singapore"
```
#### Join WAN:
```sh
consul members -wan
consul join -wan [SERVER-1-IP]
consul catalog datacenters
```
#### Verification:
```sh
curl  http://127.0.0.1:8500/v1/kv/dc
curl  http://127.0.0.1:8500/v1/kv/dc?dc=singapore
```
```sh
echo U2luZ2Fwb3Jl | base64 -d
```
