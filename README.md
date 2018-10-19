# Company Infrastructure

## Building provisioned aws AMI using Packer + Ansible

1.Execute packer:

```bash
packer build -var-file=packer/amazon/credentials.json -var-file=packer/amazon/variables.json packer/amazon/ubuntu/frontend/base_ami.json
```

2.Create manually an EC2 instance using the created AMI.

3.Access to EC2 instance via SSH using .pem to test installation

```bash
ssh -i ansible/ansible.pem ubuntu@<ip-instance>
```

