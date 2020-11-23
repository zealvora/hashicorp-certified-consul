
#### Step 1 Run following command in consul-01 (Agent in Dev Mode):

```sh
consul agent -dev -client=0.0.0.0 -client=0.0.0.0 -bind [SERVER-IP] -hcl 'disable_remote_exec=false'
```
#### Step 2: Run following command in consul-02 (Client)
```sh
consul agent -join [DEV-AGENT-IP] -bind [CURRENT-NODE-IP] -data-dir /root/consul -hcl 'disable_remote_exec=false'
```
#### Step 3: Verification:
```sh
consul exec ping -c1 google.com
```
