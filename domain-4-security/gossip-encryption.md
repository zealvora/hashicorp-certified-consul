
#### Step 1: Generate Cryptographic Key:
```sh
consul keygen
```
#### Step 2: Add appropriate paremeter within configuration

##### Approach 1 (DEV Agent Mode):
```sh
systemctl stop consul
consul agent -dev -client=0.0.0.0 -bind 134.209.155.89 -encrypt [KEY-HERE]
consul agent -bind 165.22.222.190 -join 134.209.155.89  -data-dir /root/consul -encrypt [KEY-HERE]
```
##### Approach 2 (Configuration File) - Run both on server and client :
```sh
cd /etc/consul.d
nano consul.hcl
```
```sh
encrypt = "KEY-HERE"
```
#### Step 3: Start & Verify Agent
```sh
systemctl start consul
```
#### Miscellenous Commands:
```sh
yum -y install tcpdump
tcpdump -i any port 8301
tcpdump -i any port 8301 -vv -X
```
