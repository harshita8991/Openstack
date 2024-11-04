# OPENSTACK
# To Install openstack on VM and create a VM on it

**STEP 1**. Create an instance  in  AWS  , using operating system *UBUNTU* then make some changes 

• Take Amozon Machine Image (AMI)

•Instance type-> t3.xlarge

•Storage-> 50GB

In Network setting 
i). SSH

ii). HTTP

iii). HTTPS

iv). ALL TRAFFIC



**STEP 2.** Launch instance

**STEP 3.** Then copy the IP address and paste it on *Putty* , now browse the Key as usual then click on OPEN , to create your *Virtual Machine*.

**STEP 4.**  Install the openstack snap:-

```sudo snap install openstack --channel 2024.1/beta```


**STEP 5.** Prepare the machine

_Sunbeam can generate a script to ensure that the machine has all of the required dependencies installed and is configured correctly for use in OpenStack - you can review this script using:_

```sunbeam prepare-node-script```


```sunbeam prepare-node-script | bash -x && newgrp snap_daemon```

_This will directly execute it_

**STEP 6**  Now, deploy the OpenStack cloud using the cluster bootstrap command and accept software defaults:-


```sunbeam cluster bootstrap --accept-defaults```

_It will take around 30 minutes._

**STEP 7.** To configure the deployed cloud:-

```sunbeam configure --accept-defaults --openrc demo-openrc```

 **STEP 8.** To open the VM which ead created on OpenStack

```sunbeam launch ubuntu --name test```







To check the distribution of  trafficking over two servers:-

**STEP-1** For this first of all we need to create the following--->

• Two Availability zones



• creating Virtual private cloud

AWS Console-->Services ---> Networking & Content Delivery -->VPC--> Your VPCs




• Creating four subnets 2 for public and 2 for private




• Create Internet gateway and attach to VPC






• Create Virtual Private Gateway and Attach to VPC





• Create two route tables and attach to subnets



Now edit R1-IGW and add routing rule as mentioned below

One route for Internet gateway, another for Virtual private gateway (R1-IGW and R2-VGW)
• Route - 0.0.0.0/0 to IGW
• Route - 192.168.0.0/16 to VGW





**STEP-2** Launch two instances for load balancing

 then,Install Web Server 

If you need a web server (e.g., Apache) on each instance to serve web content:

1. SSH into each EC2 instance.


2. Install a web server like Apache
3. Add sample content on each instance, as usual we do....







**STEP-3** : Create an Application Load Balancer

1. Go to the EC2 Dashboard > Load Balancers > Create Load Balancer.


2. Select Application Load Balancer.


3. Configure Load Balancer settings:

Choose a name for the load balancer.

Set the Scheme to Internet-facing or Internal (choose based on your requirement).

Select the IP address type (e.g., IPv4).





**STEP-4** : Set Up Target Group

1. Create a Target Group:

In the Load Balancer Configuration, select Target Groups.

Choose a target type (usually Instance for EC2 instances).

Configure Health Checks






2. Register EC2 Instances:

Add the two EC2 instances to the target group.

Save the target group settings.






**STEP-5** : Attach Target Group to Load Balancer

1. Go back to the Load Balancer Configuration.


2. Add a listener rule to forward traffic from port 80 to the target group you created.


3. Review and create the load balancer.





**STEP-6** : Test the Application Load Balancer

1. After the load balancer is created, go to Load Balancer > Description to find its DNS name.


2. Access the DNS name in your browser:

The load balancer should distribute traffic between the two instances.

Refresh the browser multiple times to see requests being routed to different instances.

