# Terraform backend Cloudformation script
This is a simple Cloudformation template which initializes a remote backend to be used with Terraform.

## S3 bucket creation
This template will create an S3 bucket and user will be prompted for the bucket name. To adhere to the Terraform state file best practices the following options are going to be set:
* The bucket will be encrypted by the default AWS KMS key (so key rotation can be easily implemented)
* File versioning is enabled so the previous state files can be restored
* Public access of the bucket is completely restricted

## DynamoDB table creation
DynamoDB table will be created according to the Terraform specs. The purpose of this table is for state locking and consistency. Provisioned read and write is set to minimum since Terraform does not require high database throughput.