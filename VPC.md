# VPCs (Virtual Private Cloud) - What, why, benefits

A Virtual Private Cloud (VPC) is a virtual network infrastructure provided by cloud service providers, such as Amazon Web Services (AWS), that allows users to create their own isolated network environments within the cloud. It provides several benefits to businesses and DevOps teams by offering control, flexibility, and security over their cloud resources.

## What is a VPC?
A VPC allows users to define and manage their virtual network within the cloud. It provides features such as IP address ranges, subnets, routing tables, and security groups to create an isolated and customizable network environment. With a VPC, users can launch resources like virtual machines, databases, load balancers, and more within their private network space.

## Why is VPC important for businesses?
1. **Isolation and Security**: VPCs provide network isolation, allowing businesses to separate their cloud resources from other users' resources. This isolation enhances security by ensuring that only authorized traffic can access the resources within the VPC.
2. **Customizable Networking**: VPCs allow businesses to define their own IP address ranges (CIDR blocks) and subnets within the cloud. This flexibility enables them to design their network architecture to align with their specific requirements and existing on-premises infrastructure.
3. **Connectivity**: VPCs can be connected to on-premises networks or other VPCs using secure VPN connections or dedicated network connections like AWS Direct Connect. This connectivity facilitates hybrid cloud setups and seamless communication between cloud and on-premises environments.

## How does VPC benefit DevOps?
1. **Infrastructure as Code**: VPCs can be created, configured, and managed using Infrastructure as Code (IaC) tools like AWS CloudFormation or Terraform. DevOps teams can define VPC resources as code, making it easier to version control, deploy, and automate the setup of their network infrastructure.
2. **Scalability and High Availability**: VPCs enable DevOps teams to scale their infrastructure by launching resources in different subnets across multiple availability zones (AZs). This allows for high availability and fault tolerance, ensuring that applications remain accessible even if one AZ or subnet experiences issues.
3. **Controlled Deployment**: With VPCs, DevOps teams can launch resources with specific configurations, security groups, and routing rules. This level of control helps in standardizing deployments, ensuring consistent setups, and reducing manual configuration tasks.

## Why did AWS introduce VPCs?
AWS introduced VPCs to address the need for more control and isolation within cloud environments. Prior to VPCs, AWS used the EC2-Classic model, where instances were launched into a shared, flat network. However, as the demand for more secure and customized network environments grew, AWS introduced VPCs to provide customers with dedicated and isolated virtual networks. VPCs offered enhanced security, increased flexibility, and improved networking capabilities for businesses using AWS.

## Diagram
```python
                                  +------------------+
                                  |     Internet     |
                                  |      Gateway     |
                                  +------------------+
                                           |
                                  +------------------+
                                  |   Public Subnet  |
                                  |  (CIDR: X.X.X.X) |
                                  |                  |
                                  +------------------+
                                           |
                                  +------------------+
                                  |  Private Subnet  |
                                  |  (CIDR: Y.Y.Y.Y) |
                                  |                  |
                                  +------------------+

```

In the diagram above, a VPC is depicted with a public subnet and a private subnet. The VPC is connected to the internet via an Internet Gateway. The public subnet has a CIDR block of X.X.X.X, while the private subnet has a CIDR block of Y.Y.Y.Y.

## Subnets
Subnets are smaller address ranges within a VPC. They allow for further network segmentation and resource organization. Subnets are associated with a specific availability zone (AZ) and can be either public or private.

## Public + Private Subnets
Public subnets are accessible from the internet, while private subnets are not directly accessible. Instances in the public subnet can have public IP addresses and can communicate with the internet. Instances in the private subnet can access the internet through NAT gateways or bastion hosts.

## CIDR Blocks
CIDR blocks (Classless Inter-Domain Routing) are used to define IP address ranges for a VPC and its subnets. CIDR notation specifies the network's IP address and the number of significant bits used for the network identifier.

## Internet Gateway
An Internet Gateway is a horizontally scalable and highly available AWS service that allows VPC instances to connect to the internet. It provides a route for incoming and outgoing internet traffic from the public subnet.

## Route Tables
Route tables are used to control the traffic between subnets within a VPC and to the internet. They define the rules for routing network traffic within the VPC and specify the destination for different types of traffic.

## How Security Groups Work on Instance Level
Security groups act as virtual firewalls for instances within a VPC. They control inbound and outbound traffic at the instance level. Security groups are stateful, which means that if an inbound rule allows traffic, the corresponding outbound traffic is automatically allowed, regardless of outbound rules. Security groups can be assigned to instances and are governed by user-defined rules that specify allowed protocols, ports, and source/destination IP ranges.
