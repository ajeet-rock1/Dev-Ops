# Create infra with CFT and automation to copy file through ansible


1) Create VPC and Subnet
```
aws cloudformation create-stack --stack-name DevOpsDemo-dev-vpc --template-body file://DevOpsDemo-VPC.json --parameters file://DevOpsDemo-VPC-Parameters.json
```
2) Create Public EC2 instance with Jenkins and ansible
```
aws cloudformation create-stack --stack-name DevOpsDemo-dev-PublicInstance --template-body file://Public-Subnet1-EC2-instance-CFT.json --parameters file://Public-Subnet1-EC2-instance-Parameters.json
```
3) Create Private EC2 instance
```
aws cloudformation create-stack --stack-name DevOpsDemo-dev-PrivateInstance --template-body file://Private-Subnet1-EC2-instance-CFT.json --parameters file://Private-Subnet1-EC2-instance-Parameters.json
```
4) setup login details for Jenkins , You can find jenkinURL from output of Publicinstance stack
5) Keep ssh Key of PrivateInstabce in /etc/ansible to run ansible-playbook
6) configure inventroy file on PublicInstance in /etc/ansible ( you can find IP of PrivateInstance from Privateinstance stack)
```

