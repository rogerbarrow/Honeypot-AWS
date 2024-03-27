# Honeypot-AWS

A honeypot is a security mechanism used in cybersecurity to detect, deflect, or counteract attempts at unauthorized use of information systems. It typically consists of a computer, data, or network site that appears to be part of a legitimate network but is actually isolated and monitored, with the intention of attracting and observing malicious activity. The term "honeypot" comes from the idea of a pot of honey used to attract and catch bears. Similarly, in the digital realm, a honeypot is designed to lure attackers and malware, allowing security professionals to study their tactics, understand their methods, and gather information to better protect the real systems from such threats. Honeypots can be valuable tools for studying the behavior of hackers and developing strategies to defend against them.

# Prerequisites
* An [AWS](https://aws.amazon.com/)  account
* Basic understanding of the AWS console
* Basic understanding of Github and git
* Gitbash terminal.  [Here](https://gitforwindows.org/) 

# Step 1: Create an instance; choose an Amazon Machine Image (AMI)
* 1. Open the AWS Management Console and navigate to the EC2 service.
* 2. Click on Launch Instance. Name it. I will call mine “HoneyPotServer”.
* 3. Select an AMI from the list based on your requirements. For this guide, we'll use the Debian 11 AMI.
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/147f7bc8-d950-4e7f-a6e1-da6115764bbb)

# Step 2: Configure the Instance
Configure the following settings for your EC2 instance:

* Instance Type: Determine the CPU, memory, and storage resources for your workload. Choose t2.xlarge
* Network Settings: Specify the subnet and security group for your instance. Leave this as default.
* Key Pair: Create or use an existing key pair for SSH authentication. I will call my key “honeypot”. This key when created will be downloaded to you downloads folder.
* Configure Storage: Specify 128gb gp2. This is the requirement for the TPOT, the storage is needed for log collection. Your screen should look like this:
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/00ec51b3-f178-44ee-a926-8185c9699337)
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/b6ef4bd6-6a23-4c98-af45-b49d0843a073)
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/157c3062-e932-4195-a969-23a63e9cf972)
* Additional configuration options include storage and tags.

# Step 3: Launch the Instance
* Click on Launch after configuring your settings. The instance will take a few minutes to launch.
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/7f1a6489-b132-4da3-9ca7-78a4c232722d)
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/cc04ee8d-b678-4b64-b94f-b9a3e35b3b94)


# Step 4: Connect to your Instance
* Connect to your instance using SSH (Linux). Click on instance id to the right of screen click connect. Then click “ssh client”.
* Open Gitbash terminal, right click and run as administrator. Navigate to your path where your key pair is i.e. “cd Downloads”.
* Head back to the AWS console and copy the code from line 3, paste that into the terminal, enter that and then do the same thing for line 5.
* You will be asked to continue. Enter “yes”
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/502fa5c3-d8e6-4697-9970-b650a7bf52cc)
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/c350e8d3-365e-4dd1-b416-da9f488fd984)
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/6547939b-6e30-43a0-85c7-5252bbd64e5d)

# Step 5: Update and upgrade OS
We want to ensure that the proper patches are up to date on this instance, so we will run this command in the terminal first.
* sudo apt update && sudo apt upgrade
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/98c3d0a5-d3fb-47f8-ac7b-c973850aa138)

  # Step 6: Install Git
  We will need git to pull files from github so let’s run this command.
 * ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/9f807dc7-9ae2-4b2c-98c3-d741668af187)

 * Now we need to download the software for TPOT. To do this we will navigate to github to get the link for the honeypot. Once you get there click the green button labeled “Code” and copy the .git link. Repo is here [repository](https://github.com/telekom-security/tpotce/) .
 * This link will be used alongside the “git clone” command in our terminal like so:
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/f9375fcb-71de-4396-9f96-f6d0f528a1da)

# Step 7 Navigate to folder:
Once the repo has been successfully cloned, in the terminal enter “ls” to view the folder “tpotce” and “cd” into it and “ls” again like so:
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/02a1c01a-c226-47f5-b85c-5f1785e3c56c)




