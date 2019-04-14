Launch EC2 Instance with OpenVPN
================================

Here be dragons: All of this is as of this writing (Nov 29 2018), and things evolve quickly in AWS.

This cloudformation creates a personal OpenVPN server in AWS.  I mostly used [this super helpful guide](https://medium.com/@tatianaensslin/how-to-create-a-free-personal-vpn-in-the-cloud-using-ec2-openvpn-626c40e96dab) as my reference, and assume a cursory understanding of AWS, Cloudformation and EC2.

You will need the following:

* Launch the `eip-master.json` template first. It will export the elastic IP used in the `openvpn-master.json` template.
    - I added this for convenience (and is in the guide above) so that if I needed to rebuild, I can attach the new EC2 instance to the same IP address.
* An ssh key for accessing your EC2 instance
* Your VPC's default security group ID

The AMI is the free-tier, 2 licence OpenVPN image which is running Ubuntu LTS 18.04.  I have it running on a t2.nano and is about $4/month, but you can choose any instance and ymmv.

After the VPN is up and running (no need to document the setup here, you can use the link above), I manually remove the inbound security group rules for port 22 and 943 for increased security.

If you need to ssh in and rerun the configuration script ```sudo ovpn-init –ec2``` is the command to execute.

Todo:
* Add a prestep to run a template to create a VPC