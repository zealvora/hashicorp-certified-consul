
# Start Consul in Server Mode

consul agent -server -bootstrap-expect=1 -node=consul-server -bind=134.209.155.89 -data-dir=/tmp/consul -client=0.0.0.0 -ui=true

# Making use of Configuration Directory

data_dir =  "/root/consul"
bind_addr = "134.209.155.89"
client_addr = "0.0.0.0"
bootstrap_expect = 1
node_name = "consul-server"
ui = true
server = true

consul agent --config=dir /root/consul-server-config/
