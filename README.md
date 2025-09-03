# Terraform Challenges

![Terraform](https://img.shields.io/badge/Terraform-HCL-844FBA?logo=terraform)
![Providers](https://img.shields.io/badge/Providers-AWS_|_GCP_|_Azure-orange.svg)
![Concept](https://img.shields.io/badge/Concept-Infrastructure_as_Code-blue.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

A repository dedicated to a collection of hands-on Terraform challenges forked from Zeal Vora at [this repo](https://github.com/zealvora/kplabs-terraform-challenges). There are a total of 4 challenges related to IaC skills, from basic resource provisioning to complex, multi-provider setups.

## <a name="toc"></a>Table of Contents
- [Challenge 1](#c1)
- [Challenge 2](#c2)
- [Challenge 3](#c3)
- [Challenge 4](#c4)

## <a name="c1"></a>Challenge 1
### Situation
The developer at Sample Small Corp had created a Terraform File for creating certain resources and the code was written a few years back based on the old Terraform version.

### Task
My responsibility was to review the existing Terraform code, modernise it to align with current best practices, and ensure compatibility with the latest Terraform version.

### Action
1. **Access/Secret Keys**: There are hardcoded AWS Access and Secret keys with the code. This must be fixed.
2. **Provider Block**: Provider Block is used to define provider version along with 3rd party providers. We need to use the new required_provider block to define provider and constraints.
3. **Terraform Core Versioin requirement**: The original version `0.12.31` is old version and we should use the latest version of Terraform, I have removed the original one to set the latest version in use.

### Result
The Terraform scripts were modernised, security vulnerabilities were eliminated, and the code became compliant with current Terraform standards. This ensured smoother deployments, better maintainability, and reduced risks for future infrastructure changes.

## <a name="c2"></a>Challenge 2
### Situation
The sample code has been provided that creates certain resources. I need to optimise the code following the best practices. Also, I need to demonstrate ability to modify veriable `splunk` from `8088` to `8089` without modifying the Terraform code.

### Task
My responsibility was to ensure the code is working and resource gets created without deleting the existing terraform.lock.hcl file. File is free to be modified based on requirements and I need to demonstrate the ability to modify veriable `splunk` as mention.

### Action
1. **Indentation issues**: These are present in the code and the code has been updated to ensure proper indention.
2. **Hard-coded issues**: Many values are found in hard-coded as part of the code. This makes it difficult to modify and review if code bse becomes larger. We need to use Variables and TFVars.
3. **Use of Tags**: For easy identification of the resources among all others, all resources are properly tagged.
4. **Variable Precedence**: The appropriate variable precedence must be used to override variables from Terraform code.
5. **Create Right Folder Structure**: We should not put everything in one single file named `main.tf`. `eip.tf`, `providers.tf`, `sg.tf` and `variables.tf` are created.

### Result
The Terraform configuration was optimised for readability, scalability, and maintainability. Resources could be deployed smoothly, and the splunk variable was successfully overridden to `8089` without modifying the Terraform code, demonstrating flexibility in handling infrastructure changes.

## <a name="c3"></a>Challenge 3
### Situation
I got .tf file containing varible named `instance_config` in map. Based on the values specified in map, EC2 instances should be created accordingly. If key/value is removed from map, EC2 instances should be destoryed accordingly.

### Task
My responsibility was to review the existing Terraform code, modernise it to align with current best practices, and ensure compatibility with the latest Terraform version.

### Action
1. **Use of Loops**: We need to use the loops to achieve this because the requirement indicates that based on key/value specified in map, the resources should be created and estoryed accordingly.
2. **Use for_each**: If a resource block includes a `for_each` argument whose value is a map or a set of strings, Terraform creates one instance for each member of that map or set.

### Result
The Terraform code was modernised and optimised for maintainability. EC2 instances could now be created and destroyed dynamically based on instance_config, reducing manual intervention, improving scalability, and ensuring the code aligned with Terraform best practices.

## <a name="c4"></a>Challenge 4
### Situation
Client wants a code that can create IAM user in AWS account with following syntax: `admin-user-{account-number-of-aws}`.
Client wants to have a logic that will show names of ALL users in AWS account in the output.
Client also wants Terraform to show Total number of users in AWS along with the list of users in AWS.

### Task
My responsibility was to review the existing Terraform code, modernise it to align with clientt's requirement and current best practices, and ensure compatibility with the latest Terraform version.

### Action
1. **Data Sources**: Data Sources allows us to dynamically fetch information from the infrastructure resource / othe state backends. I can fetch information dynamically like AWS Account ID, User names using Data Sources.
2. **Functions**: I make use of Terraform Function that can calculate total number of users and output it.

### Result
The Terraform code was successfully modernised to meet the client’s specifications. IAM users were created with the required naming convention, and Terraform outputs now provided both the complete list of users and the total count, giving the client greater visibility and automation in managing IAM users.

[Back to Table of Contents](#toc)
