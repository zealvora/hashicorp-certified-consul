### Pre-Requisite: A running Consul Server and Consul Client.

#### Step 1: Create Service Definiton
```sh
cd /etc/conusl.d/
```
```sh
nano web.json
```
```sh
{
  "service": {
    "name": "web",
    "port": 80
  }
}
```
```sh
chown consul.consul web.json
consul validate /etc/consul.d
consul reload
```

#### Step 2: Finding a service via DNS:
```sh
yum -y install bind-utils
```
```sh
dig @SERVER-IP -p 8600 web.service.consul
dig @SERVER-IP -p 8600 web.service.consul SRV
```
