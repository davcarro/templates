# Infrastructure Diagram

| Component            | Description                    |
| -------------------- | ------------------------------ |
| **VPC**              | CIDR Block: `10.0.0.0/16`       |
| - **Public Subnet 1**| CIDR Block: `10.0.0.0/24`       |
| - **Public Subnet 2**| CIDR Block: `10.0.1.0/24`       |
| - **Private Subnet 1**| CIDR Block: `10.0.2.0/24`      |
| - **Private Subnet 2**| CIDR Block: `10.0.3.0/24`      |
| - **Private Subnet 3**| CIDR Block: `10.0.4.0/24`      |
| - **Private Subnet 4**| CIDR Block: `10.0.5.0/24`      |
| **AMI Version**      | `ami-0fa1ca9559f1892ec`        |
| **Internet Gateway** |                               |
| **Public Route Table**|                               |
| **Private Route Table**|                              |
| **NAT Gateway**       | Allocation ID: (ID)            |
| **EIP for NAT Gateway**| Domain: vpc                   |
| **ELB Security Group**| Allow web access               |
| **EC2 Security Group**| Allow ALB and SSH access       |
| **RDS Security Group**| Allow RDS access               |
| **Load Balancer**     | Subnets: Public Subnet 1, 2    |
| **ELB Listener**      | Port: 80, Protocol: HTTP       |
| **Launch Configuration**| AMI: AMI Version, Type: t2.micro|
| **Target Group**      | Port: 80, Protocol: HTTP       |
| **Auto Scaling Group**| Min: 2, Max: 4, Desired: 2      |
| **RDS Subnet Group**  | Subnets: Private Subnet 3, 4   |
| **RDS Instance**      | Engine: MySQL, Version: 8.0.23  |

## Outputs

- Load Balancer DNS Name: (DNS Name)


```bash
aws cloudformation create-stack --stack-name V3 --template-body file://master.yaml --region us-east-1 --capabilities CAPABILITY_AUTO_EXPAND
```