
# AWS Scalable Infrastructure with Terraform

This project demonstrates the deployment of a highly available and scalable infrastructure on AWS using **Terraform**. It automates the creation of a Virtual Private Cloud (VPC), with subnets, EC2 instances, an Application Load Balancer (ALB), and Auto Scaling for dynamic traffic handling, ensuring high availability and fault tolerance.

## Features

- **VPC**: A secure, isolated network with public and private subnets spread across two availability zones.
- **EC2 Instances**: Auto-scaled instances to handle varying loads, with front-end (public) and back-end (private) configurations.
- **Application Load Balancer (ALB)**: Distributes incoming traffic across EC2 instances for better load distribution and fault tolerance.
- **Auto Scaling Group**: Automatically adjusts the number of EC2 instances based on traffic demand, ensuring optimal performance and cost efficiency.
- **Security Groups**: Configured for secure communication, restricting access to necessary ports and services.

## Architecture Overview

![Architecture Diagram](architecture_diagram.png)

1. **VPC**: The VPC has public and private subnets in two availability zones (us-east-1a, us-east-1b), ensuring high availability and fault tolerance.
2. **Public Subnets**: Hosts front-end instances (EC2-FE) that are accessible from the internet via the Internet Gateway.
3. **Private Subnets**: Hosts back-end instances (EC2-BE) that are not directly exposed to the internet.
4. **ALB**: Balances incoming HTTP traffic across EC2 instances in the public subnets.
5. **Auto Scaling Group**: Automatically scales the number of EC2 instances to handle traffic spikes.
6. **Security Groups**: Only allow necessary inbound and outbound traffic, securing the instances and internal communications.

## Prerequisites

Before deploying this infrastructure, ensure you have the following:

- **AWS CLI** configured with appropriate permissions.
- **Terraform** installed on your local machine.
- An **SSH key** pair for accessing EC2 instances.
  
## Getting Started

Follow these steps to deploy the infrastructure:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/aws-infrastructure-terraform.git
   cd aws-infrastructure-terraform
   ```

2. **Initialize Terraform**:
   ```bash
   terraform init
   ```

3. **Review and apply the Terraform plan**:
   ```bash
   terraform plan
   terraform apply
   ```

4. **Access the deployed resources**:
   - You can access the EC2 frontend instances via the ALB DNS.
   - Backend instances are isolated in private subnets and are not directly accessible from the internet.

## Project Structure

- `main.tf`: Contains the main Terraform configuration for the AWS resources.
- `variables.tf`: Defines input variables for customizing the infrastructure.
- `outputs.tf`: Defines the outputs for accessing essential details like the ALB DNS.

## Contributing

Feel free to contribute by submitting issues or pull requests if you have any improvements or suggestions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
