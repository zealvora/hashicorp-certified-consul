#### Documentation Referred:

https://www.consul.io/api-docs/query

#### Step 1: Create two services
```sh
cd /etc/consul.d
```
##### Service 1:
```sh
nano web-1.json
```
```sh
{
  "service": {
    "name": "web",
     "id": "web1",
    "port": 8080,
    "tags": ["v1"]
  }
}
```
##### Service 2:
```sh
nano web-2.json
```
```sh
{
  "service": {
    "name": "web",
    "id":   "web2",
    "port": 9080,
    "tags": ["v2"]
  }
}
```
```sh
consul reload
```

#### Use-Case 1: Creating a basic prepared query:
```sh
cd /tmp
nano prepared-query.json
```
```sh
{
  "Name": "web-service",
  "Service": {
    "Service": "web",
    "Tags": ["v2"]
  }
}
```
```sh
curl --request POST --data @prepared-query.json http://127.0.0.1:8500/v1/query

dig @localhost -p 8600 web-service.query.consul SRV
```
#### List Prepared Query:
```sh
curl http://127.0.0.1:8500/v1/query
```
#### Update Prepared Query:
```sh
curl --request PUT --data @prepared-query.json http://127.0.0.1:8500/v1/query/4de2cfbc-7c58-c4d4-8b39-ba39a7f765c8
```
Deleted Prepared Query:
```sh
curl --request DELETE http://127.0.0.1:8500/v1/query/:uuid
```
