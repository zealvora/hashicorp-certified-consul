### Documentation Referred:

https://www.consul.io/docs/connect/intentions

#### Allow Service Communication
```sh
consul intention create frontend-service backend-service
```
#### Deny Service Communcation
```sh
consul intention create -deny frontend-service "*"
```
#### Verify the Authorization
```sh
consul intention check frontend-service backend-service
```
#### Match Intentions
```sh
consul intention match backend-service
```
