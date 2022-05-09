# terraform-on-aws-repo
Sample Terraform files to create S3 bucket in AWS
# terraform-on-aws-repo

Pre-requistes:
Install Terraform on your EC2 instance or Windows or Mac machine. 
I installed Terraform in a macbook pro host machine. https://learn.hashicorp.com/tutorials/terraform/install-cli

You can provision resources in AWS cloud using Terraform by two ways as mentioned below:
1) AWS Access keys + secret keys (un-secure way)
2) Create an IAM Role with AmazonS3FullAccess Policy. (more secure way) --> I did this.
3) Clone this repo, then, in the project folder, run the next two commands, terraform init, terraform apply.

output:

zsh 5330 main% terraform init 

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/aws...
- Installing hashicorp/aws v4.13.0...
- Installed hashicorp/aws v4.13.0 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.

(base) [lun 22/05/09 10:50 CEST][s000][x86_64/darwin21.0/21.4.0][5.8]
<aironman@MacBook-Pro-de-Alonso:~/git/terraform-on-aws-repo
terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_s3_bucket.my-s3-bucket will be created
  + resource "aws_s3_bucket" "my-s3-bucket" {
      + acceleration_status         = (known after apply)
      + acl                         = "private"
      + arn                         = (known after apply)
      + bucket                      = (known after apply)
      + bucket_domain_name          = (known after apply)
      + bucket_prefix               = "my-s3bucket-"
      + bucket_regional_domain_name = (known after apply)
      + force_destroy               = false
      + hosted_zone_id              = (known after apply)
      + id                          = (known after apply)
      + object_lock_enabled         = (known after apply)
      + policy                      = (known after apply)
      + region                      = (known after apply)
      + request_payer               = (known after apply)
      + tags                        = {
          + "environment" = "DEV"
          + "terraform"   = "true"
        }
      + tags_all                    = {
          + "environment" = "DEV"
          + "terraform"   = "true"
        }
      + website_domain              = (known after apply)
      + website_endpoint            = (known after apply)

      + cors_rule {
          + allowed_headers = (known after apply)
          + allowed_methods = (known after apply)
          + allowed_origins = (known after apply)
          + expose_headers  = (known after apply)
          + max_age_seconds = (known after apply)
        }

      + grant {
          + id          = (known after apply)
          + permissions = (known after apply)
          + type        = (known after apply)
          + uri         = (known after apply)
        }

      + lifecycle_rule {
          + abort_incomplete_multipart_upload_days = (known after apply)
          + enabled                                = (known after apply)
          + id                                     = (known after apply)
          + prefix                                 = (known after apply)
          + tags                                   = (known after apply)

          + expiration {
              + date                         = (known after apply)
              + days                         = (known after apply)
              + expired_object_delete_marker = (known after apply)
            }

          + noncurrent_version_expiration {
              + days = (known after apply)
            }

          + noncurrent_version_transition {
              + days          = (known after apply)
              + storage_class = (known after apply)
            }

          + transition {
              + date          = (known after apply)
              + days          = (known after apply)
              + storage_class = (known after apply)
            }
        }

      + logging {
          + target_bucket = (known after apply)
          + target_prefix = (known after apply)
        }

      + object_lock_configuration {
          + object_lock_enabled = (known after apply)

          + rule {
              + default_retention {
                  + days  = (known after apply)
                  + mode  = (known after apply)
                  + years = (known after apply)
                }
            }
        }

      + replication_configuration {
          + role = (known after apply)

          + rules {
              + delete_marker_replication_status = (known after apply)
              + id                               = (known after apply)
              + prefix                           = (known after apply)
              + priority                         = (known after apply)
              + status                           = (known after apply)

              + destination {
                  + account_id         = (known after apply)
                  + bucket             = (known after apply)
                  + replica_kms_key_id = (known after apply)
                  + storage_class      = (known after apply)

                  + access_control_translation {
                      + owner = (known after apply)
                    }

                  + metrics {
                      + minutes = (known after apply)
                      + status  = (known after apply)
                    }

                  + replication_time {
                      + minutes = (known after apply)
                      + status  = (known after apply)
                    }
                }

              + filter {
                  + prefix = (known after apply)
                  + tags   = (known after apply)
                }

              + source_selection_criteria {
                  + sse_kms_encrypted_objects {
                      + enabled = (known after apply)
                    }
                }
            }
        }

      + server_side_encryption_configuration {
          + rule {
              + bucket_key_enabled = (known after apply)

              + apply_server_side_encryption_by_default {
                  + kms_master_key_id = (known after apply)
                  + sse_algorithm     = (known after apply)
                }
            }
        }

      + versioning {
          + enabled    = true
          + mfa_delete = false
        }

      + website {
          + error_document           = (known after apply)
          + index_document           = (known after apply)
          + redirect_all_requests_to = (known after apply)
          + routing_rules            = (known after apply)
        }
    }

Plan: 1 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + s3_bucket_name   = (known after apply)
  + s3_bucket_region = (known after apply)
╷
│ Warning: Argument is deprecated
│ 
│   with aws_s3_bucket.my-s3-bucket,
│   on main.tf line 5, in resource "aws_s3_bucket" "my-s3-bucket":
│    5: resource "aws_s3_bucket" "my-s3-bucket" {
│ 
│ Use the aws_s3_bucket_versioning resource instead
│ 
│ (and 3 more similar warnings elsewhere)
╵

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_s3_bucket.my-s3-bucket: Creating...
aws_s3_bucket.my-s3-bucket: Creation complete after 2s [id=my-s3bucket-20220509085126125300000001]
╷
│ Warning: Argument is deprecated
│ 
│   with aws_s3_bucket.my-s3-bucket,
│   on main.tf line 5, in resource "aws_s3_bucket" "my-s3-bucket":
│    5: resource "aws_s3_bucket" "my-s3-bucket" {
│ 
│ Use the aws_s3_bucket_versioning resource instead
│ 
│ (and one more similar warning elsewhere)
╵

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

Outputs:

s3_bucket_name = "my-s3bucket-20220509085126125300000001"
s3_bucket_region = "eu-west-3"
(base) [lun 22/05/09 10:51 CEST][s000][x86_64/darwin21.0/21.4.0][5.8]
<aironman@MacBook-Pro-de-Alonso:~/git/terraform-on-aws-repo>
zsh 5333 main% 


