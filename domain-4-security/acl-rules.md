### Documentation:

https://www.consul.io/docs/security/acl/acl-rules

#### Step 1: Writing Demo Policies:
```sh
key_prefix "mobiles/" {
  policy = "read"
}
```

#### Step 2: Add an Explict Deny:
```sh
key_prefix "mobiles/samsung" {
  policy = "deny"
}
```

#### Step 3: Wildcard based access
```sh
key_prefix "" {
  policy = "read"
}
```
