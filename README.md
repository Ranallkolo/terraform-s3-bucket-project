<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-terraform1)

**Author:** Abdulrahman Abdulkadir  
**Email:** abdabdulkadir62@gmail.com

---

![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create S3 buckets using Terraform. The goal is to automate the provisioning of AWS S3 storage by writing Infrastructure as Code, ensuring consistency, repeatability, and easy management of bucket configurations such as versioning, access policies, and lifecycle rules.


### Tools and concepts

Services I used were AWS S3 for storage and the AWS CLI for managing credentials and verifying resources. Key concepts I learnt include infrastructure as code, Terraform providers, resource blocks, state management, the sequence of terraform init, plan, and apply, as well as automating the creation and configuration of cloud resources, applying access controls, and uploading objects to S3 buckets in a repeatable and consistent way.


### Project reflection

This project took me approximately 3 to 4 hours to complete. The most challenging part was correctly configuring AWS credentials and ensuring Terraform had the proper access to create and manage resources. It was most rewarding to see the S3 bucket and objects successfully deployed and managed automatically through Terraform, demonstrating the power of infrastructure as code.


I did this project today to gain hands-on experience with Terraform and understand how to automate the creation and management of AWS resources like S3 buckets. This project met my goals by allowing me to practice writing infrastructure as code, setting up providers and resources, applying configurations safely, and verifying that the infrastructure was deployed correctly, giving me confidence in using Terraform for real-world cloud management.


---

## Introducing Terraform

Terraform is an open-source infrastructure as code (IaC) tool that allows you to define, provision, and manage cloud and on-premises resources using declarative configuration files. It enables automation, consistency, and version control of infrastructure, making it easier to deploy, modify, and maintain resources like AWS S3 buckets, EC2 instances, networking components, and more across multiple environments.


Terraform is one of the most popular tools used for infrastructure as code (IaC), which is the practice of managing and provisioning computing infrastructure through machine-readable configuration files rather than manual processes. IaC allows for automation, consistency, and repeatability in deploying resources such as servers, storage, and networks, enabling teams to version-control their infrastructure, reduce human errors, and scale environments efficiently across cloud platforms.


Terraform uses configuration files to define the desired state of infrastructure resources in a declarative way. main.tf is the primary configuration file where you write the core Terraform code for your project, specifying resources, providers, variables, and other settings needed to create and manage infrastructure such as AWS S3 buckets. It serves as the central file that Terraform reads when planning and applying changes to your environment.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

The configuration is structured in blocks that define providers, resources, variables, outputs, and modules. The advantage of doing this is that it makes the infrastructure code organized, readable, and reusable, allowing Terraform to understand the desired state of resources, manage dependencies automatically, and apply changes consistently across different environments.


### My main.tf configuration has three blocks

The first block indicates the provider configuration, specifying that AWS is the cloud platform to use and defining the region where resources will be created. The second block provisions an S3 bucket with a unique name, telling Terraform to create and manage this storage resource. The third block manages the public access settings for the S3 bucket, ensuring that all public access is blocked and the bucket remains secure.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_ljvh9876)

---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to gain a deeper understanding of how to define and manage AWS resources using Terraform. The documentation shows detailed examples of provider configurations, resource definitions, and best practices, including how to create S3 buckets, set up access controls, manage state files, and use modules and variables for more scalable and maintainable infrastructure code.


I chose to customise my bucket by adding tags because tags help organize and identify resources, making it easier to manage and filter them in AWS. When I launch my bucket, I can verify my customization by checking the bucket properties in the AWS Management Console or using the AWS CLI to confirm that the tags have been applied correctly.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_ffe757cd3)

---

## Terraform commands

I ran 'terraform init' to initialize my Terraform project, download the necessary provider plugins, and set up the backend for storing the state file. This step prepares the working directory so that Terraform can plan and apply the configuration correctly.


Next, I ran 'terraform plan' to preview the changes Terraform will make to my infrastructure without actually applying them. This command shows which resources will be created, modified, or destroyed, allowing me to verify that my configuration behaves as expected before making any changes in AWS.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

When I tried to plan my Terraform configuration, I received an error message that says authentication failed because I had not yet set up AWS credentials. Terraform requires valid access keys and secret keys to communicate securely with the AWS API, verify permissions, and determine what resources can be created or modified. Without these credentials, Terraform cannot authenticate my account, so it cannot generate a plan or apply any changes, preventing any interaction with AWS services until proper authentication is configured.


To resolve my error, first I installed AWS CLI, which is a command-line tool that allows users to interact with and manage AWS services directly from the terminal. It enables tasks such as configuring credentials, creating and managing resources, and automating workflows, providing a way for Terraform and other tools to authenticate and communicate securely with an AWS account.


I set up AWS access keys to provide Terraform with the necessary credentials to authenticate and interact with my AWS account. These keys allow Terraform to securely create, modify, and manage resources such as S3 buckets, ensuring that all infrastructure changes are applied under my authorized account.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

I ran 'terraform apply' to execute the planned changes and create the AWS resources defined in my Terraform configuration. Running 'terraform apply' will affect my AWS account by actually provisioning the S3 bucket and any associated settings, such as access controls and tags, making the infrastructure changes live and managed through Terraform.


The sequence of running terraform init, plan, and apply is crucial because each command prepares and validates the infrastructure in a specific order. First, terraform init initializes the working directory, downloads necessary provider plugins, and sets up the backend for the state file. Next, terraform plan reviews the configuration and shows a preview of the changes Terraform will make, allowing verification before applying any modifications. Finally, terraform apply executes the planned changes, creating or updating resources in the cloud. Following this order ensures that Terraform can manage infrastructure safely, consistently, and without errors.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I created a new resource block to define the S3 object I want to upload because Terraform needs explicit instructions for each resource it manages. This block specifies the bucket, the file to upload, and any relevant settings, ensuring that the object is provisioned and tracked as part of my infrastructure code.


We need to run terraform apply again because adding a new resource block only updates the configuration file, and Terraform has not yet applied these changes to the AWS environment. Running terraform apply ensures that the new S3 object is actually created and uploaded to the bucket, making the infrastructure changes live and managed under Terraform.


To validate that I've updated my configuration successfully, I checked the S3 bucket in the AWS Management Console or used the AWS CLI to confirm that the object was uploaded correctly. This ensures that Terraform applied the changes as intended and that the file exists in the designated bucket with the proper settings.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
