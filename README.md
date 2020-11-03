# terraform-packer
Packer is used to build AMI's
This project will help you build Nginx Image using Packer & Terraform in AWS environment.
Advantage of creating Images this way is that it is much easier to maintain those images because this is much closer to the immutable infrastructure.

# Packer
- Pre requisites - [Install packer](https://learn.hashicorp.com/tutorials/packer/getting-started-install)

- The "build-and-launch.sh" script is used to <br />
> 1st) Build an image with a snapshot <br />
> 2nd) Extract the Image_Id from the image <br />
> 3rd) Put the extracted Image Id in "amivar.tf" <br />
> 4th) Finally run "terrafom apply" <br />
- 'terraform apply' will build <br />
> 1st) A VPC with 6 subnets (3 private & 3 public), Internet Gateway, Route Table, <br />
> 2nd) A Security group with inbound rule port 22 open for ssh <br />
> 3rd) Public key called 'mykey'. ** make sure to run "ssh-keygen -f mykey' <br />
> 4th) EC2 Instance will use the image id from 'amivar.tf' <br />
> 5th) Nginx and Docker should be installed <br />


# To delete
- After you run "terraform destroy" make sure the new Snapshot and AMI image are deleted. You manually need to delete them.
