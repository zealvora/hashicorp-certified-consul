Older consul.hcl file in /root/consul-new-config

start_join = ["134.209.155.89"]
bind_addr = "165.22.222.190"
data_dir = "/root/consul"

cd /etc/consul.d
mv consul.hcl consul.hcl.bak
cp /root/consul-new-config/consul.hcl .
chown consul.consul consul.hcl

systemctl start consul
systemctl status consul
journalctl -u consul

Updating the consul.hcl file with new data directory

start_join = ["134.209.155.89"]
bind_addr = "165.22.222.190"
data_dir = "/etc/consul.d/consul-dir"

Verification Stage:

systemctl restart consul
systemctl status consul
systemctl enable consul
reboot
systemctl status consul
