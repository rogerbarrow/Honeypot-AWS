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

# Step 8 Install bash script:
* We need to run the bash script “install.sh” to do so run this command:
  
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/93063c98-dc58-4c29-a218-7dc550a7f9a9)
* You will eventually see this screen enter “y”

* # Step 9 Choose TPOT Edition:
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/7f127d1d-4ebc-4224-b835-14fb5a225a82)
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/efa04882-04fc-445b-b790-8cfbfe5882ab)

* You will be taken to a dialog box to choose your edition.
*  Choose standard and press enter.
*  ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/e5219107-1ba4-475d-ac34-248161f2ade1)

You then will create a username and password.
After this installation will continue.
# Step 10 Reconfigure Security Group:
Once the installation is complete you will notice that you will be kicked off the server. This is a good thing as TPOT has made some new configuration to your security group and now for security purposes you are no longer allowed to connect to the server via ssh port 22. So, here’s how we fix this:
* Go back to the AWS console. Go EC2>click Your instance id>security
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/1af28988-aafa-415a-a494-4954843d2422)
* Click on your security group and then edit inbound rules.
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/c060afd3-4aa4-4d16-9053-7eec98fad8b1)
* Change ssh to custom TCP port range for port 64297, for source choose my ip and for description label it whatever you like, I named mine “This is for web portal”. Note that in the following image my port is different, however I’ve found that the above configuration works best.
* Now click, add rule choose custom TCP port range for port 64295, for source choose my ip and for description I labelled it “This is to SSH in”
* Lastly, add another rule. This is also custom TCP, for the port range 1-64000, for source choose anywhere ipv4 and for description I put “For the bad guys”.
* 
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/b5436f85-9162-4c4f-814f-899e87eab475)

# Step 11 SSH with new port:
* Now we initially used the code in line 5 of the ssh client from AWS console to ssh into the instance, however since our configuration we must enter in through our new port. Therefore, we will need to make a modification to that code.

* Go to your terminal and press the up arrow the last code that you entered into it (which should be line 5 should populate. On the end of it type -p 64295 (this is our ssh) like so:
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/beaf916e-99d1-4efd-8d36-cd34454d23b8)

# Step 12 Enter path:


* Let’s again, ensure that we can access our “tpotce” folder
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/e83557b4-23e7-48d0-9fd1-daf674675808)

# Step 13 Enter web portal:
* Go back to the console, click instance id and copy your public IPv4 address
* Open a new window and in the browser enter: https:// then paste your address behind it.
* Then behind your address type “:” and then the port number you configured for the web portal in your security group. Which is 64297 and press enter.
* ![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/2237eb3f-1b03-4213-8bae-68d142b5f091)

* You will see a warning message. Click advanced and proceed. After that you will be prompted to enter the username and password that you created.
![image](https://github.com/rogerbarrow/Honeypot-AWS/assets/46138186/6469a343-5ed2-4bb1-8a2f-fe791b3d83f4)



