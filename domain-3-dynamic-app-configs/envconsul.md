### Documentation Referred:

https://github.com/hashicorp/envconsul

#### Pre-Requisite:
```sh
yum -y install golang git make
```
#### Compile:
```sh
git clone https://github.com/hashicorp/envconsul.git
cd envconsul
make dev
cp /root/go/bin/envconul /usr/local/bin
```
#### Write Data to KV Store
```sh
consul kv put my-app/address 1.2.3.4
consul kv put my-app/port 80
consul kv put my-app/max_conns 5
```

#### Run envconsul

```sh
envconsul -prefix my-app env
```
