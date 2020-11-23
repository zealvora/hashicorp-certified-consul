### Documentation Referred:

https://www.consul.io/docs/security/acl/acl-system

#### Step 1: Create following policy
```sh
node_prefix "" {
  policy = "write"
}
service_prefix "" {
   policy = "read"
}
```
#### Step 2: Add token within configuration file:

```sh
acl = {
  enabled = true
  default_policy = "deny"
  enable_token_persistence = true
  tokens {
    "agent" = "f1f30bb8-af83-ac3e-8944-efe03d782ac6"
  }
}
```
#### Step 3: Verification:
```sh
systemctl restart consul
journalctl -u consul
```
#### Step 4: DNS Check:
```sh
dig @localhost -p 8600 consul.service.consul
```
#### Anonymous Policy:
```sh
node_prefix "" {
  policy = "read"
}
service_prefix "" {
  policy = "read"
}
query_prefix "" {
  policy = "read"
}
```
```sh
dig @localhost -p 8600 consul.service.consul
```
