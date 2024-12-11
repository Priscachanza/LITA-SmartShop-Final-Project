# LITA-SmartShop-Final-Project
 a project designing and deploying a smartshop infrastructure on aws environment

 ### A BRIEF DESCRIPTION OF HOW I SET UP AN EC2 INSTANCE AND DEPLOYED AN APACHE WEB SERVER
    This document explains how i configured and set up an EC2 instance and deployed an apache web server on it. i'll walk you through every step i took starting from scratch.

### below is my step by step process

1. created the security group
Set Up Security Groups
i went to the Security Group and create a new group. 
the new created group was allowing inbound HTTP (port 80) from anywhere 
and SSH (port 22) access from your IP for the web and admin access.
and the security group was attached to the EC2 instances.

below is an image of the successfully created security group.

![alt text](<Screenshot (47).png>)

2. Launch an EC2 Instance
In the EC2 Dashboard, an instance was launch and it was named “priscachanza_lita”
i Selected Amazon Linux 2 as the Operating System and a t2.micro instance type
and then i configured the instance with the public subnet and assign the Security Group 
that i created.
    about the key pair i created the new key pair i named it "priscachanzaSG_lita"
    I choose the Key Pair Type: RSA (default)
    The private key file (.pem ) will be downloaded automatically to your computer.
    Save it securely; you cannot download it again.

below is an image of the successfully launched instance that is up and running.

![alt text](<Screenshot (49).png>) 

Note: under the network settings, for the vpc, I used the VPC created by the LITA "lita_project_vpc"
 I then select the subnet to the public subnet
 the “Auto-assign Public IP” i set it to “Enabled”
 and then i selected the already existing security group earlier created
 and then i launched the instance.

3. Installing Apache Web Server
under the SSH into the instance there's the key pair that i used to install the apache,
i went to the location where you downloaded my keypair "in downloads" and i Right click on 
any space and select the “git bash here”
i entered the below code in the new window opened in git and run the command 
"chmod 400 "priscachanzaSG_lita.pem""
![alt text](<Screenshot (50).png>) 

the key successfully passed and below is the code in git. later on i pasted another command
"ssh -i "priscachanzaSG_lita.pem" ec2-54-224-237-128.compute-1.amazonaws.com" it passed successfullyas well.
check on the image below:
![alt text](<Screenshot (51).png>) 

i runned the following command to install the apache:
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
installation complete
![alt text](<Screenshot (52).png>) 

the apache was successfully installed the SmartShop infrastructure of vpc, instance 
and security group was connected successfully, the public ip address is: 54.224.237.128
below is the test page
![alt text](<Screenshot (53).png>) 
