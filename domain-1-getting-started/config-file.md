#### Documentation Referred:

https://www.consul.io/docs/agent/options.html#_join

#### Custom Configuration Directory:
```sh
mkdir /root/consul-new-config
cd /root/consul-new-config
yum -y install nano
nano consul.hcl
```
```sh
data_dir =  "/root/consul"
start_join = ["SERVER-IP-HERE"]
bind_addr = "CLIENT-IP-HERE"
```

#### Start the Agent:

```sh
consul agent -config-dir=/root/consul-new-config/
```
