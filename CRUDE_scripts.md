# AWS CLI Scripts Documentation

This document provides an overview and explanations for a set of AWS CLI scripts for managing S3 buckets. These scripts demonstrate how to create buckets, upload files, download files, delete files, and delete buckets using the AWS CLI and the Boto3 library.

## Create Bucket Script
```python
# Import boto3 library
import boto3

# Set up an S3 connection
s3 = boto3.client("s3")

# Create a bucket, in the eu-west-1 region
bucket_name = s3.create_bucket(Bucket="tech241-mushahid-python-bucket", CreateBucketConfiguration={"LocationConstraint":"eu-west-1"})

# Print the bucket name to confirm working script
print(bucket_name)
```

This script creates an S3 bucket in the specified region. It uses the `boto3.client` method to create an S3 client and then calls the `create_bucket` method to create the bucket. The script prints the bucket name to confirm the successful creation of the bucket.

## Upload File Script
```python
# Import boto3 library
import boto3

# Set up an S3 connection
s3 = boto3.client('s3')

# Upload the file to the bucket
bucketCont = s3.upload_file("test.txt", "tech241-mushahid-python-bucket", "uploadedFile.txt")

# Print the response
print(bucketCont)

```
This script uploads a file to an S3 bucket. It uses the `boto3.client` method to create an S3 client and then calls the `upload_file` method to upload the file. The script takes the local file path, the bucket name, and the destination object key as parameters. It prints the response returned by the `upload_file` method.

## Download File Script
```python
# Import boto3 library
import boto3

# Create an S3 client
s3 = boto3.client('s3')

# Set the bucket name and file path
bucket_name = 'tech241-mushahid-python-bucket'
file_path = 'uploadedFile.txt'
local_file_path = 'downloadedFile.txt'

# Download the file from the bucket
s3.download_file(bucket_name, file_path, local_file_path)

# Print a message indicating successful download
print(f'{file_path} downloaded successfully to {local_file_path}')

```

This script downloads a file from an S3 bucket. It uses the `boto3.client` method to create an S3 client and then calls the `download_file` method to download the file. The script takes the bucket name, the source object key (file path in the bucket), and the local file path as parameters. It prints a success message after the download is completed.

## Delete File Script
```python
# Import boto3 library
import boto3

# Create an S3 client
s3 = boto3.client('s3')

# Delete the file from the bucket
response = s3.delete_object(Bucket="tech241-mushahid-python-bucket", Key="test.txt")

# Print the response
print(response)

```

This script deletes a file from an S3 bucket. It uses the `boto3.client` method to create an S3 client and then calls the `delete_object` method to delete the file. The script takes the bucket name and the object key (file path in the bucket) as parameters. It prints the response returned by the `delete_object` method.

## Delete Bucket Script
```python
# Import boto3 library
import boto3

# Set up an S3 connection
s3 = boto3.resource('s3')

# Specify the bucket name
bucket_name = 'tech241-mushahid-python-bucket'

# Create a bucket resource
bucket = s3.Bucket(bucket_name)

# Delete all objects in the bucket
bucket.objects.all().delete()

# Delete the bucket
bucket.delete()

# Print a message indicating successful deletion
print(f'Bucket {bucket_name} has been deleted')

```
This script deletes an S3 bucket. It uses the `boto3.resource` method to create an S3 resource and then accesses the bucket using the specified bucket name. The script first deletes all objects in the bucket and then deletes the bucket itself. It prints a success message after the deletion is completed.

Please note that these scripts assume you have already installed and configured the AWS CLI with your AWS credentials.
