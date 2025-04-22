
---
## Installation:

---
### 🪟 Windows

>  Download [link](https://awscli.amazonaws.com/AWSCLIV2.msi)

### 🐧 Linux (Ubuntu/Debian)

```sh
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### 🍎 macOS
 
```sh
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /
```

---
### Setup 

---

> Sets up AWS access keys, region, and output format.

```bash
aws configure
```

>  Shows the current configuration (key, region, output, etc.)

``` bash
aws configure list
```

---
### IAM

---

> Lists all IAM users.

```bash
aws iam list-users
```

> Lists all IAM roles in the account.

```bash
aws iam list-roles
```

> Shows the currently authenticated IAM identity.

```bash
aws sts get-caller-identity
```

---
### S3 (Simple Storage Service)

---

>  Lists all S3 buckets.

```bash
aws s3 ls
```

> Lists contents inside a specific bucket.

```bash
aws s3 ls s3://your-bucket-name
```

> Uploads a file to a bucket.

```bash
aws s3 cp file.txt s3://your-bucket-name/
```

> Deletes a file from the bucket.

```bash
aws s3 rm s3://your-bucket-name/file.txt
```

---
### EC2

---

> Lists all EC2 instances.

```sh
aws ec2 describe-instances
```

>Starts an EC2 instance

```sh
aws ec2 start-instances --instance-ids i-xxxxxxxxxxxxxxxxx
```

>Stops an EC2 instance.

```sh
aws ec2 stop-instances --instance-ids i-xxxxxxxxxxxxxxxxx
```

>Shows the status of running instances.

```sh
aws ec2 describe-instance-status
```

---
### RDS (Relational Database Service)

---
>Lists all RDS databases.

```sh
aws rds describe-db-instances
```

>Deletes a specific RDS DB (careful ⚠️)

```sh
aws rds delete-db-instance --db-instance-identifier your-db-name --skip-final-snapshot
```

---
### VPC (Virtual Private Cloud)

---

>Lists all VPCs in the region.

```sh
aws ec2 describe-vpcs
```

>Lists all subnets.

```sh
aws ec2 describe-subnets
```

>Lists all security groups.

```sh
aws ec2 describe-security-groups
```

---
### Security Groups

---

```sh
aws ec2 describe-security-groups
```

>show all the security groups.

---
### CLI Utilities

---

```sh
aws help  ## help command

aws ec2 help  ## EC2 help command

aws s3api help  ## S3 help command 
```
