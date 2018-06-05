# himanshu-qloyalcodetest-docker-aws

## 1 - Postman Collection (lightbulb-api) : docker on AWS EC2 Instance <br/>

### step 1: Connect to EC2 Instance using keys present in awk_login_keys folder <br/>
         #### Instruction for Windows
         a. Download putty from https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
         b. Use the following credentials on putty window :
         ##### - HostName (or IP address): ec2-13-236-117-253.ap-southeast-2.compute.amazonaws.com 
         ##### - Port                    : 22
         ##### - Connection type         : SSH
         ##### - Using the left panel (Category) go to "Connection" >> "SSH" and click on "Auth"
         ##### - On the window that shows on clicking "Auth" , under "Private key file for authentication" specify the path of "ec2keypair2.ppk"
         ##### - Go to Session using left panel, under Saved Sessions type "linux-aws" and click save. This will save the connection for future reference
         c. Open the connection and login use the following username (password not required)
         ##### - username: ec2-user
         
         

## 2 - jmeter jmx execution (lightbulb) : on AWS EC2 Instance using CLI and GUI <br/>

## 3 - Selenim docker grid setup on AWS EC2 <br/>
