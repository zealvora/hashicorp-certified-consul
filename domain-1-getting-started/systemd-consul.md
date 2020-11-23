
#### Backing up the default consul config:
```sh
cd /etc/consul.d
mv consul.hcl consul.hcl.bak
```
#### Add new consul configuration:
```sh
nano consul.hcl
```
```sh
start_join = ["SERVER-IP"]
bind_addr = "CURRENT-NODE-IP"
data_dir = "/etc/consul.d/consul-dir"
```
```sh
chown consul.consul consul.hcl
```

#### Verification Stage:
```sh
systemctl start consul
systemctl status consul
systemctl enable consul
reboot
systemctl status consul
```

### To check the logs:
```sh
journalctl -u consul
```
