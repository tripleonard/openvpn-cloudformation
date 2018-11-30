Build EC2 Instance with OpenVPN
===============================

Here be dragons: All of this is as of this writing (Nov 29 2018), and things evolve quickly in AWS.

This cloudformation creates a personal OpenVPN server in AWS.  I mostly used [this guide](https://medium.com/@tatianaensslin/how-to-create-a-free-personal-vpn-in-the-cloud-using-ec2-openvpn-626c40e96dab) as my reference, and assume a cursory understanding of AWS and EC2.

You will need the following:

* An ssh key for accessing your EC2 instance
* An Elastic IP (you will need the AllocationID)
    - I added this for convenience so that if I needed to rebuild, I could attach the new EC2 instance to the same IP address.
* Your VPC's default security group ID

The AMI is the free tier 2 licence OpenVPN image which is running Ubuntu LTS 16.04.  I have it running on a t2.nano and is about $4/month.

After the VPN is up and running (no need to document the setup here, you can use the link above), I manually remove the inbound security group rules for port 22 and 943 for increase security.