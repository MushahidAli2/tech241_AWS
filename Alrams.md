# CPU Usage Alarm Documentation

## Introduction

This document provides instructions on how to set up a CPU usage alarm for an EC2 instance using Amazon CloudWatch. The CPU usage alarm helps monitor the performance and resource utilization of the EC2 instance, allowing timely response to abnormal CPU usage patterns.

## Prerequisites

Before setting up the CPU usage alarm, ensure the following:

- You have access to an AWS account with permissions to manage CloudWatch alarms.
- An EC2 instance is running and accessible in your AWS environment.

## Step-by-Step Instructions

### 1. Accessing the CloudWatch Console

1. Sign in to the AWS Management Console.

2. Open the CloudWatch service by navigating to the "Management & Governance" category and selecting "CloudWatch."

### 2. Creating the CPU Usage Alarm

1. In the CloudWatch console, click on "Alarms" in the left navigation pane.

2. Click on the "Create Alarm" button to start creating a new alarm.

3. Select the EC2 namespace from the "Create Alarm" wizard.

4. Choose the "By metric" tab and search for the desired EC2 instance in the "Search for resources" field.

5. Under the "Conditions" section, select the "Static" option for the CPU utilization metric.

6. Define the threshold value for the CPU utilization. For example, set it to 80% to trigger an alarm when CPU usage exceeds this threshold.

7. Configure the alarm settings, such as the period (e.g., 5 minutes) and the number of evaluation periods.

8. Specify the actions to perform when the alarm state is triggered. For email notifications, select the "In alarm" state and enter the recipient email address.

9. Review the alarm configuration and click on the "Create alarm" button to create the CPU usage alarm.

### 3. Testing the CPU Usage Alarm

To test the CPU usage alarm, follow these steps:

1. SSH into the EC2 instance associated with the CPU usage alarm.

2. Execute commands that increase CPU usage. For example, run the following commands:

   ```bash
   apt update
   apt upgrade
   ```
these commands simulate CPU-intensive operations.

3. Monitoring and Notifications
Once the CPU usage exceeds the defined threshold, the CPU usage alarm will enter the "ALARM" state. An email notification will be sent to the specified recipient email address.

Include a screenshot of the email notification received when the CPU usage alarm is triggered. The screenshot should showcase the relevant details, such as the alarm name, timestamp, and the alarm state.
## Conclusion

Setting up a CPU usage alarm using CloudWatch allows proactive monitoring of CPU utilization for EC2 instances. By following the steps outlined in this documentation, you can effectively configure the alarm and receive timely notifications when CPU usage exceeds the defined threshold.