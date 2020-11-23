#### Basic Watch Command:
```sh
consul watch -type=key -key=max_memory
```

#### Invoking an Handler:
```sh
mkdir /root/tmp-consul
cd /root/tmp-consul
```
```sh
nano myscript.sh
```
```sh
#!/usr/bin/env sh
while read watch
do
    echo $watch
done
```
```sh
chmod +x myscript.sh
consul watch -type=key -key=max_memory ./myscript.sh
echo MTAyNE1C | base64 -d
```
#### Checks Critical Checks:
```sh
consul watch -type checks -state critical
```
