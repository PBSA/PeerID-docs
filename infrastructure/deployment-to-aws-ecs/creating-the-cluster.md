# Creating the Cluster

After creating the Task Definition, we can now create a Cluster.

## Creating a Fargate Cluster

Select the `Networking only` cluster template.

### Configure cluster

Enter the cluster name.

### Networking

If you don't already have a VPC setup, it's good practice to create one.

 An example VPC would have 4 subnets, 2 meant to be private, and 2 meant to be public. 

Example:

CIDR block `10.0.0.0/16` \
Subnet 1: `10.0.0.0/24`\
Subnet 2: `10.0.1.0/24`\
Subnet 3: `10.0.2.0/24`\
Subnet 4: `10.0.3.0/24` 

You would then navigate to the VPC service and: 

1. Create route table for each of the two subnets chosen to be public facing and route 0.0.0.0/0 to the VPC's internet gateway. 
2. Create NAT gateways for the public facing subnets.
3. Create route tables for the private subnets and add a 0.0.0.0/0 routes to the NAT gateways.

