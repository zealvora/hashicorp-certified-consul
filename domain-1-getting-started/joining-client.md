

### Pre-Requisite: Consul Server should be up and running with following syntax
```sh
consul agent -dev -client=0.0.0.0 -bind [SERVER-IP]
```
### Client:
```sh
consul agent -join [SERVER-IP] -bind [CLIENT-IP] -data-dir [PATH-TO-FOLDER]
```
### Example Used during video:
```sh
consul agent -join 134.209.155.89 -bind 165.22.222.190 -data-dir /root/consul
