Project Overview:

Virtual Private Cloud (VPC):
The foundation of the infrastructure started with the creation of a dedicated VPC (aws_vpc.myvpc). This VPC, with a CIDR block of 10.0.0.0/16, provides an isolated network environment, ensuring that all resources deployed within it are secure and have controlled access.

Subnets and Availability Zones:
To ensure high availability and fault tolerance, I deployed two public subnets (aws_subnet.subnet1 and aws_subnet.subnet2) across different availability zones (us-east-1a and us-east-1b). This distribution of resources across zones helps in mitigating the impact of potential outages in a single zone.

Internet Gateway and Route Tables:
To enable internet connectivity, an Internet Gateway (aws_internet_gateway.igw) was integrated into the VPC. I also meticulously configured route tables, associating them with the public subnets to manage and route traffic between the internet and instances securely.

Security Groups:
Security is paramount in any cloud environment, and I implemented a robust security group (aws_security_group.webSg) to manage and control inbound and outbound traffic. This group allows HTTP and SSH access, enabling secure management and communication with the deployed instances.

EC2 Instances:
Two EC2 instances (aws_instance.webserver1 and aws_instance.webserver2) were deployed within the subnets, each configured with Apache servers. Using Terraform’s user data scripts, I automated the setup of the web servers, allowing for dynamic content delivery as soon as the instances launch.

Application Load Balancer:
To enhance the responsiveness and availability of the application, I set up an Application Load Balancer (aws_lb.myalb). This ALB efficiently distributes incoming traffic across the EC2 instances, ensuring seamless access to the application even under varying loads.

S3 Bucket Integration:
An S3 bucket (aws_s3_bucket.example) was utilized for storage, showcasing the integration of multiple AWS services. This bucket can be used for storing application assets, backups, or logs, further extending the functionality of the infrastructure.

Outputs for Easy Access:
To facilitate easy access to the application, I configured Terraform to output the DNS name of the load balancer (output.loadbalancerdns). This provides a single, consistent endpoint for accessing the deployed web application.
