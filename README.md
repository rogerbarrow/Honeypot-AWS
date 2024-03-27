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


