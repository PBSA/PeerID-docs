# Creating the Service

Once we have created a Cluster, we can create a service inside it.

## Configure Service

1. Choose a Launch Type. \(In this case we will be using FARGATE\).
2. Select a Task Definition and revision.
3. Select the platform version.
4. Select a cluster.
5. Create a name for the service.
6. Select the service type \(in this case we will be using REPLICA\).
7. Enter the number of tasks that the service should try to keep running.
8. Enter the desired value for the minimum and maximum healthy percent.

### Deployments

Select either the Rolling update or Blue/green deployment.

### Task Placement

Select a placement strategy from the placement templates.

## Configure network

### VPC and security groups

1. Select your Cluster VPC.
2. Select your desired subnets.
3. Attach security groups. 
4. Attach a Load Balancer

## Set Auto Scaling \(optional\)

Select Service Auto Scaling to set cardinality of tasks and automatic task scaling policies.

