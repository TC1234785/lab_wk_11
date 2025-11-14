# 4640-ansible-roles-lab

## Run the Ansible configuration

Prereqs (first time only):

```shell
pip install boto3 botocore
```
If pip does not work, run these commands:
```shell 
sudo apt install python
sudo apt install pip
pip install boto3 botocore
```

## Ansible Configuration
Ensure that the name of the playbook is actually playbook. 
If not, the run this command: 
```shell
cp <filename> playbook.yml
```

Once that is complete, run the command: 
```shell 
ansible-playbook -i inventory/aws_ec2.yml playbook.yml
```



### Screenshot: 
<img width="446" height="258" alt="image" src="https://github.com/user-attachments/assets/eb1b607c-1c4e-4b38-9ce4-8bf9aec02b03" />

