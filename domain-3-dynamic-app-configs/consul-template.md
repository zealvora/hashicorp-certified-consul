
### Documentation:

https://releases.hashicorp.com/consul-template/

#### Installation Steps :
```sh
mkdir /root/template
cd /root/template
yum -y install wget
wget https://releases.hashicorp.com/consul-template/0.25.1/consul-template_0.25.1_linux_amd64.tgz
tar -xzvf consul-template_0.25.1_linux_amd64.tgz
mv consul-template /usr/local/bin
rm -f consul-template_0.25.1_linux_amd64.tgz
```
#### Example 1:
```sh
nano course.tpl
```
```sh
{{ key "course" }}
```

```sh
consul-template -template "course.tpl:course_name.txt"
consul-template -template "course.tpl:course_name.txt" -once
```
#### Configuration File:
```sh
consul {
 address = "127.0.0.1:8500"
}
template {
 source = "/root/template/course.tpl"
 destination = "/root/template/course-newname.txt"
 command = "echo Modified > /root/template/delta.txt"
}
```

```sh
consul-template -config "/root/template/template.hcl"
```
