### Documentation Referred:

https://www.consul.io/docs/discovery/checks

#### Step 1: Enabling Service Health Checks:
```sh
{
  "service": {
    "name": "web",
    "port": 80,
    "check": {
    "args": [
        "curl",
        "127.0.0.1"
      ],
      "interval": "10s"
    }
  }
}
```
```sh
consul validate /etc/consul.d
consul reload
```
#### Step 2: Enable Local Script Checks:
```sh
nano /etc/consul.d/consul.hcl
enable_local_script_checks = true
systemctl restart consul
```
#### Step 3: Enable your application:
```sh
yum -y install nginx
systemctl start nginx
netstat -ntlp
```
#### Step 4: Health Check Verification
```sh
yum -y install bind-utils
dig @CONSUL-SERVER-IP -p 8600 web.service.consul
```
```sh
systemctl stop nginx
dig @CONSUL-SERVER-IP -p 8600 web.service.consul
```
