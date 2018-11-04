# Company Infrastructure

## Install Ansible roles

```bash
$ ansible-galaxy install -r ansible/galaxy/requirements.yml
```

## Building provisioned aws AMI using Packer + Ansible

* Create the `credentials.json` file under `packer/amazon` with the following format:

```json
{
  "aws_access_key": "<your-aws-access-key>",
  "aws_secret_key": "<your-aws-secret-key>"
}

```

* Execute packer:

```bash
packer build -var-file=packer/amazon/credentials.json -var-file=packer/amazon/variables.json packer/amazon/ubuntu/frontend/base_ami.json
```

* Create an EC2 instance manually using the created AMI.

* Access to EC2 instance via SSH using .pem to test installation

```bash
ssh -i aws.pem ubuntu@<ip-instance>
```

