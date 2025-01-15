# Peering-Connection



VPC Peering Connection demonstrates how to establish and manage a peering connection between two Virtual Private Clouds (VPCs) to enable secure communication. This project is ideal for connecting workloads across VPCs in the same or different AWS regions.

## Features

Private Communication: Securely connect two VPCs for internal traffic.

Cross-Region Connectivity: Establish peering connections across AWS regions.

Resource Sharing: Enable access to shared resources like databases and applications.

Custom Route Tables: Control traffic routing between VPCs.

Enhanced Security: Use security groups and network ACLs to enforce access control.

## Prerequisites

Before starting, ensure you have:

Two AWS VPCs (in the same or different regions) with non-overlapping CIDR blocks.

AWS CLI installed and configured.

Permissions to create and manage VPCs and route tables.


## Setup and Installation

Step 1: Create a Peering Connection

Open the AWS Management Console and navigate to VPC > Peering Connections.

Click Create Peering Connection and provide the following details:

Requester VPC ID

Accepter VPC ID

(Optional) Accepter Account ID if the VPC is in a different AWS account.

Confirm and create the peering connection.

If the accepter VPC is in a different account, the owner must accept the request.

Step 2: Update Route Tables

Navigate to VPC > Route Tables.

Select the route table associated with the requester VPC.

Add a route for the accepter VPC's CIDR block, pointing to the peering connection.

Repeat the process for the accepter VPC's route table.

Step 3: Configure Security Groups

Update security group rules to allow traffic between the VPCs.

Example rule for inbound traffic:

Protocol: TCP

Port Range: 80 (or your application port)

Source: CIDR block of the peer VPC.

Step 4: Test Connectivity

Launch instances in each VPC.

Test communication using ping, curl, or application-level connectivity.


## Example Configuration

Example Route Table Entry:

Destination: 10.1.0.0/16 (Peer VPC CIDR block)

Target: pcx-0abcd1234efgh5678 (Peering connection ID)

Security Group Rule:

Type: Custom TCP Rule

Protocol: TCP

Port Range: 80

Source: 10.1.0.0/16

## Monitoring and Troubleshooting

CloudWatch Logs: Enable VPC Flow Logs to monitor traffic between VPCs.

Peering Connection Status: Check the status in the AWS Console to ensure the connection is active.

Route Table Validation: Verify that routes are properly configured.

Security Group Rules: Ensure rules allow traffic from the peer VPC.



## Outcome

By completing this project, you will:

Gain practical experience in setting up VPC peering connections.

Understand routing and security configurations for private VPC communication.

Enable seamless data sharing between VPCs.
