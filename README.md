
 ## Deployed high availability web application using CloudFormation
    This project creates and deploys infrastructure and application called Udagram. The application code is deployed from s3 bucket using read only IAM role. Deployment begins with networking components such as vpc, subnets, availability zones, internet gateway, NAT gateway, route tables. Followed by server components such as launch configuration, auto scaling group, load balancer, security groups, target groups.


### Prerequisite
    1. A knowledge of basic commands in Unix terminal.
    2. Understanding of yml file and json file.
    3. AWS account.

### Summary of working of project
    •	In this project, I deployed 4 Apache web servers, two in each private subnet. 
    •	I used instance profile to create IAM role which allowed my server instances to read JavaScript and html files from s3 bucket and deploy it in appropriate web servers.  
    •	I used network address translation (NAT) gateway in public subnet to allow my servers in private subnets to connect with the internet.
    •	I used internet gateway to enable VPC to communicate with internet traffic. 
    •	I used public route table to direct traffics from internet gateway to NAT gateway which resides on public subnets. I used private route tables to direct traffics from NAT gateway to my servers which resides on private subnets.
    •	I used security groups to limit inbound and outbound traffic to and from my servers and load balancer. 
    •	I used load balancer to evenly distribute server traffics.
    •	I used auto scaling group to scale my servers up/down as per need.
    •	I used launch configuration to provide auto scaling group necessary meta data to create and launch servers.

### Architecture: 
![GitHub Logo](/images/architecture.png)
Format: ![Alt Text](url)

### Files included are
    1) Udagram-Network.yml: YML file for Udagram Networks.
    2) Network-Parameters.json: JSON file for Network Parameters.
    3) Udagram-Server.yml: YML file for Udagram Servers.
    4) Udagram-Parameters.json: JSON file for Udagram Server Parameters.
    5) /Application code: Application code for Udagram.
    6) create.sh: CloudFormation create stack script.
    7) delete.sh: CloudFormation delete stack script.
    8) Screenshot: Screenshot of application being deployed. 
    9) Udagram.pdf: Udagram project diagram.

### Instruction to deploy

#### Dependencies
    Deploy Udagram network stack first. 
    `Run` ./create.sh udagram-network Udagram-Network.yml Network-Parameters.json
Deploy Udagram server stack.
`Run` ./create.sh udagram-server Udagram-Server.yml Udagram-Parameters.json 

### Output
    Go to output section of `Server stack`. Click on `website URL` to display web page. 







