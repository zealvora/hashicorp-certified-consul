### Documentation:

https://www.consul.io/commands/license
https://www.hashicorp.com/products/consul/trial


#### Step 1 Install Consul Enterprise:
```sh
wget https://releases.hashicorp.com/consul/1.8.6+ent/consul_1.8.6+ent_linux_amd64.zip
yum -y install unzip
unzip consul_1.8.6+ent_linux_amd64.zip
which consul
rm -f /usr/bin/consul
mv consul /usr/bin
```

#### Step 2: Add a license
```sh
cd /etc/consul.d
systemctl start consul
systemctl status consul
consul license get
nano consul.lic
consul license put @consul.lic
```
