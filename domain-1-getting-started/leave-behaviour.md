
#### Start Consul Agent in DEV Mode (consul-01):
```sh
consul agent -dev -client=0.0.0.0 -bind=134.209.155.89
```
#### Start Consul Agent in Client Mode (consul-02)
```sh
consul agent -join 134.209.155.89 -bind 165.22.222.190 -data-dir /root/consul
```
#### To forcefully exit:
```sh
killall -s 9 consul
```
#### To gracefully exit:
```sh
killall -s 2 consul
```
