# Honeypot-AWS

A honeypot is a security mechanism used in cybersecurity to detect, deflect, or counteract attempts at unauthorized use of information systems. It typically consists of a computer, data, or network site that appears to be part of a legitimate network but is actually isolated and monitored, with the intention of attracting and observing malicious activity. The term "honeypot" comes from the idea of a pot of honey used to attract and catch bears. Similarly, in the digital realm, a honeypot is designed to lure attackers and malware, allowing security professionals to study their tactics, understand their methods, and gather information to better protect the real systems from such threats. Honeypots can be valuable tools for studying the behavior of hackers and developing strategies to defend against them.

# Prerequisites
* An [AWS](https://aws.amazon.com/)  account
* Basic understanding of the AWS console
* Basic understanding of Github and git
* Gitbash terminal.  [Here](https://gitforwindows.org/) 

# Step 1: Create an instance; choose an Amazon Machine Image (AMI)
* 1. Open the AWS Management Console and navigate to the EC2 service.
* 2.Click on Launch Instance. Name it. I will call mine “honey_im_home”.
* 3. Select an AMI from the list based on your requirements. For this guide, we'll use the Debian 11 AMI.
