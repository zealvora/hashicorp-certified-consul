
### Pre-Requisite: Create two namespaces named alice-team and bob-team
##### i) Create First Namespace:
```sh
nano alice-team.hcl
```
```sh
name = "alice-team"
```
```sh
consul namespace write alice-team.hcl
```
##### ii) Create Second Namespace:
```sh
nano bob-team.hcl
```
```sh
name = "bob-team"
```
```sh
consul namespace write bob-team.hcl
```
#### Step 1 Create Service for Bob Team:
```sh
nano web-bob.hcl
```
```sh
service {
  name = "web-service"
  port = 8080
  namespace = "bob-team"
}
```
#### Step 2 Create Service for Alice Team:
```sh
nano web-bob.hcl
```
```sh
service {
  name = "web-service"
  port = 9080
  namespace = "alice-team"
}
```
```sh
rm -f alice-team.hcl bob-team.hcl
consul reload
```
#### Step 3 Create Service for Default Namespace:
```sh
web-default.hcl
```
```sh
service {
  name = "web-service"
  port = 1080
}
```


#### DNS Interface:

Following is the syntax for the DNS query:
```sh
<service-name>.service.<datacenter>.consul  << Default
<service-name>.service.<namespace>.<datacenter>.consul
```
Actual Query Command:
```sh
dig @localhost -p 8600 web-service.service.consul SRV
dig @localhost -p 8600 web-service.service.alice-team.dc1.consul SRV
dig @localhost -p 8600 web-service.service.bob-team.dc1.consul SRV
```
