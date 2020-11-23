### Use-Case 2 Static Failover Policy:

#### Singapore DC:
```sh
cd /etc/consul.d
nano db.json
```
```sh
{
  "service": {
    "name": "database",
    "port": 5080,
    "tags": ["v1"]
  }
}
```
```sh
consul reload
```
#### India DC:
```sh
cd /tmp
nano failover.json
```
```sh
{
  "Name": "failover",
  "Service": {
    "Service": "database",
    "Tags": ["v1"],
    "Failover": {
      "Datacenters": ["singapore"]
    }
  }
}
```
```sh
curl --request POST --data @failover.json http://127.0.0.1:8500/v1/query
```

#### Verification:

India DC:
```sh
dig @localhost -p 8600 failover.query.consul SRV
```
