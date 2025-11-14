# 4640-ansible-roles-lab



## Getting started

See D2L for lab instructions.

## Run the Ansible configuration

Prereqs (first time only):

```powershell
pip install boto3 botocore
ansible-galaxy collection install amazon.aws
```

Run (from repo root):

```powershell
$env:ANSIBLE_CONFIG = "ansible/ansible.cfg"

# Inspect dynamic inventory from AWS EC2 plugin
ansible-inventory -i ansible/inventory/aws_ec2.yml --graph

# Sanity checks
ansible-playbook -i ansible/inventory/aws_ec2.yml ansible/playbook.yml --syntax-check
ansible-playbook -i ansible/inventory/aws_ec2.yml ansible/playbook.yml --list-hosts

# Dry run with diffs
ansible-playbook -i ansible/inventory/aws_ec2.yml ansible/playbook.yml --check --diff

# Apply changes (optionally limit to one group first)
ansible-playbook -i ansible/inventory/aws_ec2.yml ansible/playbook.yml --limit server_role_frontend_server -vv
ansible-playbook -i ansible/inventory/aws_ec2.yml ansible/playbook.yml
```

Notes:
- The dynamic groups come from EC2 tags via `ansible/inventory/aws_ec2.yml`.
- Nginx reloads via handlers when `index.html` or `default.conf` changes.
- Files and templates are located under roles, e.g. `ansible/roles/frontend/...`.
