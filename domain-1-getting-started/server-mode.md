
#### Start Consul in Server Mode
```sh
consul agent -server -bootstrap-expect=1 -node=consul-server -bind=[SERVER-IP] -data-dir=/tmp/consul -client=0.0.0.0 -ui=true
```
#### Making use of Configuration Directory
```sh
data_dir =  "/root/consul"
bind_addr = "SERVER-IP"
client_addr = "0.0.0.0"
bootstrap_expect = 1
node_name = "consul-server"
ui = true
server = true
```

#### Start Consul Agent
```sh
consul agent --config=dir /root/consul-server-config/
```
