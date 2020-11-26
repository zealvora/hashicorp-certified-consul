### Pre-Requisite:

Make sure that consul is stopped via systemd
Data-Dir path should be empty in the client .

#### Server:
```sh
consul agent -dev -client=0.0.0.0 -bind 159.65.145.160
```
#### Client:
```sh
consul agent -retry-join 159.65.145.160 -bind  134.209.154.246 -data-dir /root/consul -retry-interval 5s
```
