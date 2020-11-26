### Our Setup:

#### consul-server
```sh
data_dir =  "/etc/consul.d/consul-dir"
client_addr = "0.0.0.0"
bind_addr   = "159.65.145.160"
bootstrap_expect = 1
node_name = "consul-server"
ui = true
server = true
```
#### consul-client:
cat consul.hcl
```sh

data_dir =  "/etc/consul.d/consul-dir"
bind_addr = "134.209.154.246"
node_name = "consul-02"
start_join = ["159.65.145.160"]
enable_local_script_checks = true
```

##### Service Definition

cat web.hcl
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

Make sure nginx is running or you can disable script checks .

### Our sample key:

ER5awGvrbkd25fO67Q4SktzZwSwR/F2SFQMExXmFlUE=
OR
consul keygen


#### Step 1: Set both flags to false
```sh
encrypt = "ER5awGvrbkd25fO67Q4SktzZwSwR/F2SFQMExXmFlUE=",
encrypt_verify_incoming = false,
encrypt_verify_outgoing = false
```
```sh
systemctl restart consul
```
#### Step 2: Set outgoing to true
```sh
encrypt = "ER5awGvrbkd25fO67Q4SktzZwSwR/F2SFQMExXmFlUE=",
encrypt_verify_incoming = false,
encrypt_verify_outgoing = true
```
```sh
systemctl restart consul
```
#### Step 3: Set incoming to true
```sh
encrypt = "ER5awGvrbkd25fO67Q4SktzZwSwR/F2SFQMExXmFlUE=",
encrypt_verify_incoming = true,
encrypt_verify_outgoing = true
```
```sh
systemctl restart consul
```
