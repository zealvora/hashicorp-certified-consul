#### Consul 01:
```sh
data_dir =  "/root/consul"
bind_addr = "172.17.0.2"
client_addr = "0.0.0.0"
bootstrap_expect = 3
server = true
node_meta {
  zone = "zone1"
}
```
```sh
consul agent --config-dir /etc/consul.d/
```
#### Consul 02:
```sh
data_dir =  "/root/consul"
bind_addr = "172.17.0.3"
client_addr = "0.0.0.0"
bootstrap_expect = 3
start_join = ["172.17.0.2"]
server = true
node_meta {
  zone = "zone2"
}
```
```sh
consul agent --config-dir /etc/consul.d/
```
#### Consul 03:
```sh
data_dir =  "/root/consul"
bind_addr = "172.17.0.4"
client_addr = "0.0.0.0"
bootstrap_expect = 3
start_join = ["172.17.0.2"]
server = true
node_meta {
  zone = "zone3"
}
```
```sh
consul agent --config-dir /etc/consul.d/
```
#### Update Autopilot configuration to reflect node_meta:
```sh
consul operator autopilot set-config -redundancy-zone-tag=zone
consul operator autopilot get-config
consul operator raft list-peers
```
#### Consul 04:
```sh
data_dir =  "/root/consul"
bind_addr = "172.17.0.5"
client_addr = "0.0.0.0"
bootstrap_expect = 3
server = true
start_join = ["172.17.0.2"]
node_meta {
  zone = "zone1"
}
autopilot {
  redundancy_zone_tag = "zone"
}
```
```sh
consul agent --config-dir /etc/consul.d/
```
#### Consul 05:
```sh
data_dir =  "/root/consul"
bind_addr = "172.17.0.6"
client_addr = "0.0.0.0"
bootstrap_expect = 3
start_join = ["172.17.0.2"]
server = true
node_meta {
  zone = "zone2"
}
autopilot {
  redundancy_zone_tag = "zone"
}
```
```sh
consul agent --config-dir /etc/consul.d/
```
#### Consul 06:
```sh
data_dir =  "/root/consul"
bind_addr = "172.17.0.7"
client_addr = "0.0.0.0"
bootstrap_expect = 3
start_join = ["172.17.0.2"]
server = true
node_meta {
  zone = "zone3"
}
autopilot {
  redundancy_zone_tag = "zone"
}
```
```sh
consul agent -config-dir /etc/consul.d/
```
