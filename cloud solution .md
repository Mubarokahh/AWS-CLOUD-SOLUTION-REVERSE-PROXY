# SET UP VPC

* I created a VPC named "mbarokah" as an isolated network environment 
## Note
* By default,the DNS hostname is disabled. 
* I enabled the DNS hostname.
 ![vpc settings](Images/vpc-settings.jpg)
 ![Dns-Hostname](Images/Dns-Hostname.JPG)


 # CREATE SUBNETS
 * subnets were added to the vpc to enable range of AWS resources to be deployed in the VPC
 * For context, 6 subnets were added [2 Public Subnets] [4 Private Subnets]
 * These subnets will exist within 2 avaialbiltiy zones [A and B]. That is, 3 subnets in each availabilty zone.
 * 10.0.0.0/16 CIDR consists of 65,536 IP V4 addresses [2^(32-x)]. Where x=cidr notation.
 * I randomly picked 6 IPV4 addresses within the 10.0.0.0/16 CIDR block.
  ![Subnets](Images/Subnets.JPG)

  ## CREATE ROUTE TABLES FOR THE SUBNETS
  * 2 Route Tables were created. 1 for each group of subnets [Private and Public]
  
    ![Route-Table](Images/Route-Table.JPG)

   ## CREATE INTERNET GATEWAY

   * I created internet gateway and it was enabled and attached to the VPC

     ![Igw](Images/Igw.JPG)

     ## CONFIGURE A PUBLIC ROUTE TABLE

     * I edited the public route table created from ealier.
     * I associated the Internet Gateway to this route table.
     * The purpose of this is to be able to route the subnets in these group to the internet.
     * These action is not done for the Private RT.

      ![Public-RT](Images/Public-RT.JPG)

      ## CREATE ELASTIC IP ADDRESSES

      * I created 3 Elastic IPS .
      
     ![Elastic-IP](Images/Elastic-IP.JPG)
      
      ## CREATE NAT GATEWAY

      * I configured a NAT Gateway for connectivity to the internet
      * An elastic IP address was attached to this NAT Gateway at creation.
      * One of the public Subnets created earlier was also attached.

       ![NAT](Images/NAT.JPG)

       ## CREATE SECURITY GROUP
        ## 1. Nginx Server
        * Traffic will only be allowed from external load balancer from port 80 and 443 
        * It will allow SSH access from our Bastion

       
        ![NginxSG](Images/NginxSG.JPG)

        ## 2. External Application Load Balancer
        * ALB will be available from the internet
        * This will allow traffic from any IP addreas

**
         ![External-lb](Images/External-lb.JPG)


 **
           ![External-SG](Images/External-SG.JPG)

  ![]()

  ![]()

  ![]()


  ![]()



