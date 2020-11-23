https://www.consul.io/docs/agent/options.html#_join

mkdir /root/consul-new-config
cd /root/consul-new-config
yum -y install nano
nano consul.hcl

data_dir =  "/root/consul"
start_join = ["SERVER-IP-HERE"]
bind_addr = "CLIENT-IP-HERE"

consul agent -config-dir=/root/consul-new-config/
