# Company Infrastructure

## Ansible

### Example: Variables merging order:

Files to review:
* `inventories/example`
* `group_vars/first_group.yml`
* `group_vars/second_group.yml`
* `host_vars/first.host.com.yml`
* `host_vars/second.host.com.yml`

Run this playbook:

```bash
$ ansible-playbook playbook_example.yml -i inventories/example --connection=local
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

