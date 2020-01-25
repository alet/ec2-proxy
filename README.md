# EC2 as socks proxy by ansible playbook

## Installing

Suppose you use Ubuntu, so you should install git, python, boto and ansible
```sh
sudo apt install boto git
pip install --user ansible
git clone git@github.com:alet/ec2-proxy.git
cd ec2-proxy
```
## Configuring

After that you should conigure scripts. You may change values in group_vars/all or you may copy that file to host_vars/localhost and make changes there. Brief meaning for vars and where they values are:
- keypair: aws (ssh key name. The key pairs can be generated on EC2 console)
- instance_type: t2.nano
- security_group: (can be created in EC2 console)
- subnet: (can be created in VPC console on AWS)
- image: ami-062f7200baf2fa504
- region: us-east-1
- access_key: (this and next variable you may get in IAM console of AWS)
- secret_key:

## Using

When you complete vars with values you may run scripts to create virtual server:
```sh
ansible-playbook site.yml
```
After successful runing there are two files will appear: connect.sh and delete.yml. To make socks proxy listen on 127.0.0.1:3128 run `./connect.sh` and conigure your browser use proxy. Then you don't need proxy anymore execute:
```sh
ansible-playbook delete.yml
```
