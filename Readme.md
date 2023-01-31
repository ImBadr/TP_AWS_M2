# TP AWS : Architecture & WEB Server integration

Authors : Badr TADJER | Adrien PLOT

## Introduction

TP Architecture & WEB Server integration

## Part 1 : Lab Connection

Region : Ireland
Group : Lab_Student_3

## Part 2 : Lab Connection

### Architecture

![Architecture](./assets/part_1/architecture.png)

### 2.1 : Create a VPC

name : my_vpc_ab

![VPC_Creation](./assets/part_1/VPC_Creation.png)

### 2.2 : Create a Gateway

name : my_igw_ab

![Gateway_Creation](./assets/part_1/internet_gateway_creation.png)

### 2.3 : Create a Subnet

names :

- my_private_subnet_ab-01
- my_private_subnet_ab-02
- my_public_subnet_ab-01
- my_public_subnet_ab-02

![Subnet_Creation](./assets/part_1/subnets_creation.png)

### 2.4 : Create a Route Table

names :

- my_route_table_private_subnet_ab-01
- my_route_table_private_subnet_ab-02
- my_route_table_public_subnet_ab-01
- my_route_table_public_subnet_ab-02

![Route_Table_Creation](./assets/part_1/route_tables_creation.png)

### 2.5 : Create ACL

- my_private_acl_ab
![ACL_Creation](./assets/part_1/acl_public_creation.png)

- my_public_acl_ab
![ACL_Creation](./assets/part_1/acl_private_creation.png)

### 2.6 : Create a Security Group

names :

- my_private_security_group_ab
- my_public_security_group_ab

![Security_Group](./assets/part_1/security_group_creation.png)

### 2.7 : Create a AMI

name : serveur-web-instance-ab

![AMI_Creation](./assets/part_1/web_server_instance_creation.png)

ssh connection to the AMI :
![AMI_Creation](./assets/part_1/web_server_ssh_connection.png)

Pages result (test.html & ping.html) :

![AMI_Creation](./assets/part_1/http_test.png)
![AMI_Creation](./assets/part_1/http_ping.png)

### 2.8 : Create a NAT Group

![AMI_Creation](./assets/part_1/security_group_NAT_creation.png)

### 2.9 : Create a NAT Instance

A bastion is a server that is accessible from the internet and that is used to access a private network. It is a security best practice to use a bastion to access a private network.

Ping resutl :

![AMI_Creation](./assets/part_1/nat_instance_ping.png)

## Part 3 : Load Balancer & Auto Scaling

### AWS Architecture

![Architecture](./assets/part_1/architecture.png)

### 3.1 : Create a AMI

Create a AMI from the web server instance created in part 2.7

![AMI_Image_Creation](./assets/part_2/ami_image_creation.png)

### 3.2 : Create a configuration template

name : autoscaling_launch_configuration_ab

![AMI_Image_Creation](./assets/part_2/autoscaling_launch_configuration.png)

### 3.3 : Create a Auto Scaling Group

name : autoscaling_group_ab

Configuration with 2 instances MIN/MAX

![AMI_Image_Creation](./assets/part_2/autoscaling_group.png)

Instance creation verification :

![AMI_Image_Creation](./assets/part_2/autoscaling_group_instance_creation_1.png)
![AMI_Image_Creation](./assets/part_2/autoscaling_group_instance_creation_2.png)

Try to delete one instance :

a new instance has been created

![AMI_Image_Creation](./assets/part_2/autoscaling_group_instance_deletion.png)

### 3.4 : Create a Load Balancer

name : load_balancer_ab

![AMI_Image_Creation](./assets/part_2/load_balancer_creation.png)

target group creation :

![AMI_Image_Creation](./assets/part_2/target_group_creation.png)

### 3.5 : Add Target Group to Load Balancer

![AMI_Image_Creation](./assets/part_2/load_balancer_target_group.png)

Health check :

![AMI_Image_Creation](./assets/part_2/load_balancer_health_check.png)

### 3.6 : Test Load Balancer

After customizing the test.html page, we can test the load balancer :

![AMI_Image_Creation](./assets/part_2/load_balancer_test_1.png)
![AMI_Image_Creation](./assets/part_2/load_balancer_test_2.png)
