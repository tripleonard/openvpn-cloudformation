Launch EC2 Instance with OpenVPN
================================

Here be dragons: All of this is as of this writing, and things evolve quickly in AWS.

This cloudformation creates a personal OpenVPN server in AWS.  I mostly used [this super helpful guide](https://medium.com/@tatianaensslin/how-to-create-a-free-personal-vpn-in-the-cloud-using-ec2-openvpn-626c40e96dab) as my reference, and a bit from the [offical ec2 openvpn guide](https://openvpn.net/vpn-server-resources/amazon-web-services-ec2-tiered-appliance-quick-start-guide/).  I also assume a cursory understanding of AWS, Cloudformation and EC2.

You will need the following:

* Launch the `eip-master.json` template first. It will export the elastic IP used in the `openvpn-master.json` template.
    - I added this for convenience (and is in the guide above) so that if I needed to rebuild, I can attach the new EC2 instance to the same IP address.
* Your VPC's default security group ID

The AMI is the free-tier, 2 licence OpenVPN image (ami-0abbb3ceae54aa9fa us-west-2) which is running Ubuntu LTS 18.04.  I have it running on a t2.nano.

After the VPN is up and running (no need to document the setup here, you can use the links above if interested), I manually remove the inbound security group rules for port 943 for increased security.

Post deploy:
1) Log into the admin portal via the link in the output of the template and accpet the license agreement
2) Go to VPN Setting and add the DNS severs (I used Google's 8.8.8.8 and 8.8.4.4), Save settings and click the reload the server button
3) Profit

Todo:
* Add a new VPC, maybe? Overkill?
