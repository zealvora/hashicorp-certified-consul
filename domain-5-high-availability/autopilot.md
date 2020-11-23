
#### First Server (consul-01):
```sh
consul agent -server -bootstrap-expect=3 -node=consul-server -bind=134.209.155.89 -data-dir=/tmp/consul -client=0.0.0.0 -ui=true
```
#### Second Server (consul-02):
```sh
consul agent -server=true -client=0.0.0.0 -bind 165.22.222.190 -data-dir /tmp/consul
consul join 134.209.155.89
```
#### Third Server (demo-02):
```sh
consul agent -server=true -client=0.0.0.0 -bind 165.22.222.190 -data-dir /tmp/consul
consul join 134.209.155.89
```
#### See Details of Servers & Verify Autopilot settings (consul-01):
```sh
consul operator raft list-peers
consul operator autopilot get-config
```
#### Modify Autopilot Settings (leader node):
```sh
consul operator autopilot set-config -server-stabilization-time=60s
```
#### Leave and Join consul-02 node:
```sh
consul leave
consul agent -server=true -client=0.0.0.0 -bind [NODE-IP]  -data-dir /tmp/consul
consul join [FIRST-SERVER-IP]
```
Monitor the data to see how much time it takes for it to be added as Voter (consul-01):
```sh
consul operator raft list-peers
```
