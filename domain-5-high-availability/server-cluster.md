
#### Server 1:
```sh
consul agent -server=true -client=0.0.0.0 -bind [NODE-IP] -bootstrap-expect 3 -data-dir /tmp/consul
```
#### Server 2:
```sh
consul agent -server=true -client=0.0.0.0 -bind [NODE-IP]  -data-dir /tmp/consul
consul join [FIRST-SERVER-IP]
```
#### Server 3:
```sh
consul agent -server=true -client=0.0.0.0 -bind [NODE-IP]  -data-dir /tmp/consul
consul join [FIRST-SERVER-IP]
```
#### Verification:
```sh
consul members
```
#### API Endpoint:
```sh
http://SERVER-IP:8500/v1/status/leader
```
