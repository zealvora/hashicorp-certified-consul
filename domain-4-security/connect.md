

#### Pre:Requisite: Selinux to Permissive:
```sh
setenforce 0
nano /etc/selinux/config
systemctl stop consul
```
#### Step 1: Configure Nginx
```sh
yum -y install nginx
```
```sh
cd /etc/nginx/conf.d/
nano services.conf
```
```sh
server {
    server_name _;
    listen 8080;
    location / {
         proxy_pass http://127.0.0.1:5000;
}
  }

server {
    server_name _;
    listen 9080;
    root /usr/share/nginx/html/backend-service;
}
```
```sh
cd /usr/share/nginx/html
mkdir backend-service
cd backend-service
echo "Backend Service" > index.html
nginx -t
systemctl start nginx
```
#### Step 2: Create Service Definition:

Definition for Backend Service:
```sh
cd /tmp
```
```sh
nano backend-service.hcl
```
```sh
service {
  name = "backend-service"
  id = "backend-service"
  port = 9080

  connect {
    sidecar_service {}
  }

  check {
    id       = "backend-service-check"
    http     = "http://localhost:9080"
    method   = "GET"
    interval = "1s"
    timeout  = "1s"
  }
}
```
```sh
consul services register backend-service.hcl
```
```sh
nano frontend-service.hcl
```
```sh
service {
  name = "frontend-service"
  port = 8080

  connect {
    sidecar_service {
      proxy {
        upstreams = [
          {
            destination_name = "backend-service"
            local_bind_port  = 5000
          }
        ]
      }
    }
  }

  check {
    id       = "backend-service-check"
    http     = "http://localhost:8080"
    method   = "GET"
    interval = "1s"
    timeout  = "1s"
  }
}
```
```sh
consul agent -dev --client=0.0.0.0
```
```sh
consul services register frontend-service.hcl
consul services register backend-service.hcl
```
#### Step 3: Start Sidecar Proxy:
```sh
consul connect proxy -sidecar-for frontend-service > /tmp/frontend-service.log &
consul connect proxy -sidecar-for backend-service > /tmp/backend-service.log &
netstat -ntlp
```
#### Step 4: Verification:
```sh
curl localhost:8080
less /tmp/backend-service.log
```
