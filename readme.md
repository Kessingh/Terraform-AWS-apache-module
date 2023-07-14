terraform modules to provision an ec2 that runs an apache webserver


for learing purpose only, just showcasing the concept of module and file provisioner

```hcl

terraform {

}

provider "aws" {
  region = "ap-south-1"
}

module "apache" {
  source          = ".//terraform-aws-apache-example"
  vpc_id          = "vpc-xxxxxxxxxxxxxxxxxx"
  my_ip_with_cidr = "YOUR_IP"
  public_key      = file("~/.ssh/id_rsa.pub")
  private_key     = file("~/.ssh/id_rsa")
  instance_type   = "t2.micro"
  server_name     = "apache-modules"
}

output "public_ip" {
    value = module.apache.public_ip
  
}
```
