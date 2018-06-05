# himanshu-qloyalcodetest-docker-aws

## 1 - Postman Collection (lightbulb-api) : docker on AWS EC2 Instance <br/>

Steps to execute the Postman Collection on EC2 : <br/>

### step 1: Connect to EC2 Instance using keys present in awk_login_keys(*.ppk, *.pem) folder in this repo<br/>
         #### 1.1 Instruction for Windows
         a. Download putty from https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
         b. Use the following credentials on putty window :
         ###### - HostName (or IP address): ec2-13-236-117-253.ap-southeast-2.compute.amazonaws.com 
         ###### - Port                    : 22
         ###### - Connection type         : SSH
         ###### - Using the left panel (Category) go to "Connection" >> "SSH" and click on "Auth"
         ###### - On the window that shows on clicking "Auth" , under "Private key file for authentication" specify the path of "ec2keypair2.ppk"
         ###### - Go to Session using left panel, under Saved Sessions type "linux-aws" and click save. This will save the connection for future reference
         c. Open the connection and login use the following username (password not required)
         ###### - username: ec2-user
         
         #### 1.2 Instruction for Mac/Linux Terminal
         a. chmod 400 ec2keypair2.pem
         b. ssh -i "ec2keypair2.pem" ec2-user@ec2-13-236-117-253.ap-southeast-2.compute.amazonaws.com
         c. Type "yes" when it prompts "Are you sure you want to continue connecting (yes/no)?"

### Step 2: After login Go the folder lightbulb-project <br/>
         cd ~/lightbulb-project

### Step 3: Execute Following commands to run the collection on docker:
         #### 3.1 Command to execute scenario for POST /api/allmethods/on with valid range 1-60 , reading data from external source data/post-200-valid.json. Execution logs will be stored in logs/light-post-200-va_<timestamp>.log
          command> docker run -v ~/collections:/etc/newman -t postman/newman_ubuntu1404:2.1.2 --collection=lightbulb-quantasTest.json.postman_collection --folder post-200-valid -d data/post-200-valid.json | tee -a logs/light-post-200-va_`date +%Y%m%d%H%M%S`.log
         
         #### 3.2 Command to execute scenario for all GET requests including /api/allmethods/on, /api/allmethods/off, /api/allmethods. Execution logs will be stored in logs/light-get-all_<timestamp>.log
         command> docker run -v ~/collections:/etc/newman -t postman/newman_ubuntu1404:2.1.2 --collection=lightbulb-quantasTest.json.postman_collection --folder get-ALL | tee -a logs/light-get-all_`date +%Y%m%d%H%M%S`.log

         #### 3.3 Command to execute scenario for POST /api/allmethods/on with invalid range , reading data from external source data/post-200-invalid.json. Execution logs will be stored in logs/light-post-200-in_<timestamp>.log_
         command> docker run -v ~/collections:/etc/newman -t postman/newman_ubuntu1404:2.1.2 --collection=lightbulb-quantasTest.json.postman_collection --folder post-200-invalid -d data/post-200-invalid.json | tee -a logs/light-post-200-in_`date +%Y%m%d%H%M%S`.log

         #### 3.4 Command to execute scenario for POST /api/allmethods/on with invalid header info, reading data from external source data/post-400.json. Execution logs will be stored in logs/light-post-400_<timestamp>.log_a
         command> docker run -v ~/collections:/etc/newman -t postman/newman_ubuntu1404:2.1.2 --collection=lightbulb-quantasTest.json.postman_collection --folder post-400 -d data/post-400.json | tee -a logs/light-post-400_`date +%Y%m%d%H%M%S`.log
         


## 2 - jmeter jmx execution (lightbulb) : on AWS EC2 Instance using CLI and GUI <br/>

### step 1: Connect to EC2 Instance using keys present in awk_login_keys(*.ppk, *.pem) folder in this repo<br/>
         #### 1.1 Instruction for Windows
         a. Download putty from https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
         b. Use the following credentials on putty window :
         ###### - HostName (or IP address): ec2-52-65-110-111.ap-southeast-2.compute.amazonaws.com 
         ###### - Port                    : 22
         ###### - Connection type         : SSH
         ###### - Using the left panel (Category) go to "Connection" >> "SSH" and click on "Auth"
         ###### - On the window that shows on clicking "Auth" , under "Private key file for authentication" specify the path of "ec2keypair3.ppk"
         ###### - Go to Session using left panel, under Saved Sessions type "ubuntu-aws" and click save. This will save the connection for future reference
         c. Open the connection and login use the following username (password not required)
         ###### - username: ubuntu
         
         #### 1.2 Instruction for Mac/Linux Terminal
         a. chmod 400 ec2keypair3.pem
         b. ssh -i "ec2keypair3.pem" ec2-user@ec2-13-236-117-253.ap-southeast-2.compute.amazonaws.com
         c. Type "yes" when it prompts "Are you sure you want to continue connecting (yes/no)?"
         
### Step 2: After login Go the folder lightbulb-project <br/>
         cd ~/lightbulb-jmeter

### Step 3: Execute Following commands to run the jmeter script via CLI: (logfile will be create in log folder with timestamp)
         command> jmeter -n -t lightbulb_demo.jmx -j log/jmeter_`date +%Y%m%d%H%M%S`.log

### Step 4: To view the jmeter script configuration on the GUI from AWS instance, you would need to do the following: 
            note: Although the following instructions are valid for windows and mac, however these have been tested only on windows
            #### 4.1 Download xming server from https://xming.en.softonic.com/ and Install and launch it
            #### 4.2 On the putty, before clicking connect after you have entered all the login info, do the following:
                   ##### On the left panel expand Connection >> SSH 
                   ##### Click on X11
                   ##### Under X11 forwarding , click on "Enable X11 forwarding" and
                   ##### Under X11 forwarding, in "X display location" box type localhost:0.0
            #### 4.3 type 'jmeter' on the prompt, this will open the jmeter GUI
            #### 4.4 Go to file open and browse to open lightbulb-jmeter/lightbulb_demo.jmx

## 3 - Selenim docker grid setup on AWS EC2 <br/>
### step 1: Connect to EC2 Instance using keys present in awk_login_keys(*.ppk, *.pem) folder in this repo<br/>
        Note: follow instructions of ##1 ### Step 1 to connect to EC2 Instance

### Step 2: To view the Selenium grid using the following command:
     command> docker ps
