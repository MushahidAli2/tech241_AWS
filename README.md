# Launching and Terminating an EC2 Instance in AWS

## AWS Introduction

Amazon Web Services (AWS) is a cloud computing platform that provides a wide range of services, including the Elastic Compute Cloud (EC2). EC2 allows you to create virtual servers in the cloud, known as instances, to run your applications.

## Launching an EC2 Instance

1. **Sign in to the AWS Management Console**: Go to the [AWS Management Console](https://console.aws.amazon.com/) and sign in to your AWS account.

2. **Navigate to EC2**: From the AWS Management Console, search for and select "EC2" to access the EC2 Dashboard.

3. **Choose an AMI (Amazon Machine Image)**: Select the desired AMI, which is a pre-configured operating system and software package for your instance.

4. **Choose an Instance Type**: Select the instance type that best suits your application's requirements in terms of computing power, memory, and storage.

5. **Configure Instance Details**: Set various configuration options such as the number of instances, network settings, and storage configurations.

6. **Add Storage**: Specify the size and type of storage volumes attached to the instance.

7. **Configure Security Group**: Define inbound and outbound traffic rules using security groups. Security groups act as virtual firewalls to control inbound and outbound traffic at the instance level.

   > Note: In AWS, you can save security groups separately and reuse them for other instances.

8. **Review and Launch**: Review the configuration details and make any necessary changes. Finally, click "Launch" to create the instance.

## SSH into an EC2 Instance

1. **Obtain the Public IP Address**: Once the instance is launched, note the Public IP address associated with it. In AWS, the Public IP address may change if you stop and start the instance.

2. **Set Up SSH Key Pair**: In the EC2 Dashboard, navigate to "Key Pairs" and create or import an SSH key pair. This key pair is used for authentication when connecting to the instance.

3. **Connect to the EC2 Instance**: Open a terminal or command prompt and use the following command to establish an SSH connection to the instance:

```bash
ssh -i <path_to_key_pair_file> <user>@<public_ip_address>
```

Replace `<path_to_key_pair_file>` with the path to your private key file, `<user>` with the appropriate username (e.g., `ec2-user` for Amazon Linux, `ubuntu` for Ubuntu instances), and `<public_ip_address>` with the instance's Public IP address.

## Terminating an EC2 Instance

1. **Navigate to EC2**: Access the EC2 Dashboard in the AWS Management Console.

2. **Select the Instance**: Locate the instance you want to terminate and select it from the list.

3. **Terminate the Instance**: Right-click on the instance and choose "Instance State" > "Terminate". Confirm the termination when prompted.

4. **Review Termination Warning**: Read the termination warning carefully, as terminating an instance permanently deletes its data and cannot be undone.

---

## Differences with Azure

- **Security Groups**: In AWS, security groups are used to control inbound and outbound traffic at the instance level. They act as virtual firewalls. Azure uses a similar concept called "Network Security Groups" (NSGs), which provide similar functionality.

- **Saving Security Groups**: AWS allows you to save security groups independently and reuse them for other instances. Azure does not have this exact feature, but you can create network security group templates and apply them to multiple resources.

- **Dynamic Public IP Address**: In AWS, the Public IP address associated with an instance may change if you stop and start the instance. This behavior is different from Azure, where the Public IP address remains the same unless explicitly released or changed.

---

Please note that this document provides a high-level overview, and it's always recommended to refer to the official documentation or consult appropriate resources for detailed instructions and best practices.

