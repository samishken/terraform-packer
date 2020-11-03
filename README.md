# terraform-packer
Packer is used to build AMI's <br /> 
Packer is a command line tool that can build AWS AMIs based on templates.<br /> 
Instead of installing the software after booting up an instance, you can create an AMI with all the necessary software on <br />
This can speed up the boot times of instances. Instead of booting up a default image that is installing a software on it <br />
We can already boot the AMI with all the software installed on the AMI <br />
So, you first build a customized AMI, then you boot it. <br />

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
