# Setup EC2 Collection and Authentication

## Install boto3

```
pip install boto3
```

## Install AWS Collection

```
ansible-galaxy collection install amazon.aws
```

## Setup Vault 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```
3. To edit the vault file, use

```
ansible-vault edit group_vars/all/pass.yml --vault-password-file vault.pass
```

### Notes:
- In this class we are learning about creating resources in AWS. So here we creates an EC2 instance, but upto now we are connecting to an instance and doing our work. But here in this case, there is no target VM itself. So, we need to use the collections concept in Ansible.
- These collections are like we are talking with APIs of the AWS to create the services.
- There are many Collections already exists which can be used, the same way we have it for AWS/Azure also.
- So, before starting the creating yaml script using collections, do above pre-requisites.
- If anything kept inside double curly brackets then it is considered as a variable in ansible.
- Let say in script there is a variable for access keys like aws_access_key = "{{ec2_access_key}}", whatever that is stored in double curly brackes this variable name should be used in vault file for placing access keys. Like in vault file do ec2_access_key: shdjsdhsjdhsj.



