#### Step 1: Enabling ACLs
```sh
cd /etc/consul.d
```
```sh
nano agent.hcl
```
```sh
acl = {
  enabled = true
  default_policy = "deny"
  enable_token_persistence = true
}
```
#### Step 2: Create Bootstrap Token
```sh
consul acl bootstrap
```
#### Approach 1: Using Tokens with CLI Command
```sh
consul members -token "TOKEN-HERE"
```
#### Approach 2: Using Environement Variables
```sh
export CONSUL_HTTP_TOKEN=3a2c3d17-a6db-03db-a89b-15419aab68b1
```
