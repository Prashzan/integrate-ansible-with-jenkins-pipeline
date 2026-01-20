## Integrate-ansible-with-jenkins-pipeline. How to execute ansible playbooks from jenkins pipeline

### Steps we are doing 

#### 1. We have jenkins server running on digital ocean droplet (we can installed the tools inside jenkins container/server to be available on the pipeline)

#### 2. Create dedicated server for Ansible and Install ansible on that server. We can either run ansible locally on our own laptop or jenkins server or as a common practice you will have a dedicated server for ansible and install it on a different server and execute ansible commands from that server.So we gonna create another dropet of ubuntu distro for ansible server

#### 3. Now we have seperate jenkins server and server server both running on digital ocean

#### 4. Once we have this setup we would want to execute ansible playbook from a jenkins pipeline that configures two ec2 instances.

#### 5. We are basically creating 2 ec2 instances and configure everything from scratch with Ansible

#### 6. There is a sample java maven project to which we connect the pipeline and finally we create Jenkinsfile that basically executes ansible playbook on the remote ansible server from jenkins server and that playbook will configure 2 ec2 instances by installing docker and docker compose on them.


#### Ansible server will need boto3 and botocore libraries and also we need aws credentials when we need to use dynamic inventory cuz plugin need to authenticate with aws

### Dynamic Inventory (we need aws credentials)
#### a. Instead of hard coding ec2 instances IP_address. We need aws credentials for that dynamic inventory to work.
#### b. The "aws_ec2" inventory plugin will try to connect to aws to fetch all the ec2 instances from our aws account and we need to authenticate, and thats why we need aws credentials
#### c. The default location for aws credentials is .aws in user home directory. lets create 
``` mkdir .aws ```
``` cd .aws ```
``` vim credential ```

#### From your home directory just get the credentials that we have and copy inside ansible server
``` cat .aws/credentials ```

### Create 2 ec2 instances from the console. (amazon-linux) and create a new key pair, and this is the key we need to provide ansible so that it can connect to and configure ec2 instances. Now we don't need to do ssh to instances cuz ansible will do it all.

## ------------------------------*********************--------------------------

### Now we will write jenkinsfile that copies all the necessary files to the remote ansible server and executes ansible playbook commands on the ansible remote server.






 
