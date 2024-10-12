# AWS VPC Peering Planning Document

## Documentation

[Learn more about VPC Peering](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)


## VPC Information

### Me
- VPC CIDR: 
- Account ID: 
- VPC ID: 
- EC2 Private IP: 
- Region: 

### Other Person
- VPC CIDR: 
- Account ID: 
- VPC ID: 
- EC2 Private IP: 
- Region: 

## Steps
1. **Create a custom VPC**: Specify your desired CIDR block.
2. **Create a Security Group (SG)**: Allow ICMP, HTTP, and SSH traffic.
3. **Launch an EC2 instance**: Use the created SG and an appropriate key pair.
4. **Verify SSH access**: Check connectivity by SSHing into the EC2 instance and pinging it.
5. **Create a cross-account peering connection**: Initiate or accept the peering request.
6. **Update the route table**: Add the requester CIDR and the PCX connection.
7. **Verify connectivity**: Use ping or curl (if hosting a web server) to confirm cross-account private access.

## Tear Down
1. Terminate EC2 instances.
2. Delete security groups.
3. Remove routes associated with the peering connection.
4. Delete other resources in the VPC if they exist:
   - If created, delete NAT gateways.
   - Release any elastic IP addresses associated with NAT resources or EC2 instances.
5. Delete the VPC.

### Example Configuration
| Info      | Example Values                        |
|------------------|------------------------------|
| VPC CIDR        | 10.20.0.0/16                |
| Account ID      | 134567244321                 |
| VPC ID          | vpc-086e030f2a4fc5656       |
| EC2 Private IP   | 10.20.1.164                  |
