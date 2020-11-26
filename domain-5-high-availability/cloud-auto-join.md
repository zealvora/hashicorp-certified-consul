### Documentation Referred:

https://www.consul.io/docs/install/cloud-auto-join


#### IAM Role Associated with EC2 Instance:
```sh
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        }
    ]
}
```

Make sure that security group allows connections between consul-server and consul-client.

#### consul-server:
```sh
consul agent -dev -bind 172.31.87.159
```
#### consul-client:
```sh
consul agent -retry-join "provider=aws tag_key=Name tag_value=consul-server" -data-dir /root/consul -retry-interval 5s
```
