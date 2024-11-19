## EX.NO.4
 # SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
 ## NAME:Soundarya J
 ## REG NO:212223220108
 ## AIM
To  setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones. 
## PROBLEM STATEMENT
This experiment demonstrates how to configure Amazon EFS to provide a shared storage solution for two Linux EC2 instances across different availability zones, enabling easy data sharing. The aim is to ensure both instances can mount and access the EFS file system and validate data consistency across instances.

## ALGORITHM
#### Step 1: Launch Two EC2 Instances in Different Availability Zones
Go to the EC2 service in the AWS Management Console.</BR>
Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.</BR>
Assign each instance a security group that allows NFS access on port 2049.</BR>

### Step 2: Set Up Security Group for EFS
Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.</BR>
Attach this security group to the EFS file system to permit access from both instances.</BR>

#### Step 3: Create an EFS File System
In the AWS Console, navigate to the EFS service and select Create file system.</BR>
Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.</BR>
Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).</BR>

#### Step 4: Configure EC2 Instances to Access EFS

##### Instance 1</BR>
SSH into the first EC2 instance.</BR>
Switch to superuser</BR>
Install the HTTP server and EFS utilities</BR>
Mount the EFS file system to the web server's root directory</BR>
Navigate to the mounted directory and create a sample file:

##### Instance 2
SSH into the second EC2 instance.</BR>
Switch to superuser</BR>
Install the HTTP server and EFS utilities</BR>
Mount the EFS file system to the web server's root directory</BR>
Navigate to the mounted directory, list files, and view the content of the file created on Instance 1</BR>

## COMMANDS :

### EC2 Instance 1
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
```
### EC2 Instance 2
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file  # Verify shared access by reading content created in Instance 1
```
## OUTPUT
## Creation two EC2 instances in different availability zones:
![Screenshot 2024-09-13 104227](https://github.com/user-attachments/assets/32e9e06a-be89-41d6-9b93-d7d01e0070ca)

![Screenshot 2024-09-13 104550](https://github.com/user-attachments/assets/2be77c54-e611-4c70-bd8a-b969bfff3c04)

![Screenshot 2024-09-13 104909](https://github.com/user-attachments/assets/31f81fdd-ba3c-4740-9469-8c29b6580ba3)

## Set up of a security group that allows necessary communication between the instances and EFS:

![Screenshot 2024-09-13 110159](https://github.com/user-attachments/assets/9d1a2153-fef3-4c72-b9df-d2a662c47817)

## EC2 instances can access the file system and share data between them :
## OUTPUT AT INSTANCE 1:
![Screenshot 2024-09-13 140900](https://github.com/user-attachments/assets/4a99c467-83a2-48c9-ac1a-36fbb334d659)
## OUTPUT AT INSTANCE 2:
![Screenshot 2024-09-13 140849](https://github.com/user-attachments/assets/da9a47c5-1ece-44ad-a95b-1cb113485058)




## RESULT
Successfully set up a scalable file storage system using Amazon EFS shared between two Linux EC2 instances in different availability zones, enabling consistent data sharing.
  

  


