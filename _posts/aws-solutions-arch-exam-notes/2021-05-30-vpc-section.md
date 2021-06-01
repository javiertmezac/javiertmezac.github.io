---
layout: post
title:  "VPC Section - AWS Solutions Arch exam notes"
date:   2021-05-30 23:00:00 -0800
categories: aws_exam_notes
---

# VPC Section
[An interactive IP address and CIDR range visualizer](https://cidr.xyz/)

## Default VPC configuration
- vpc
- route table
- internet gateway
- network access control list (ACL)
- subnets with internet access
- security group

## Custom VPC Creation
### VPC
- Tenancy: Default means shared resources, Dedicated means is going to cost $$$
- NO CREATED
  - subnets 
  - internet gateway
- CREATED
  - route table
  - Network ACLs
  - security group

### Subnets
 - by default they are not assigned public ipv4 address
 - 5 IPs are reserved by amazon [VPC and Subnet sizing for ipv4](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#VPC_Sizing)

### How to get internet access
1. Create Internet Gateway .. It can be attached to 1 VPC (no more)
2. Route Table.
  - Main RT allows communication between subnets that are using sorrect ip configuration ie. (10.0.0.0/16)
  - by default all subents that are created are associated with MAIN RT.
  - best practice - create a public Route Table and explicitly associate subnets to it (to allow internet access)
    - edit routes on this public route ie. 0.0.0.0/0 -> target internet gateway (ipv6) ::/0 -> internet gateway
    - associate subnet to it. "Remember to choose the one with autho-assigned public ipv4 address"

## Findings while surfing the Console
- depending on the selected Region "default VPC configuration changes"
 - number of subents and range of IP addresses ie ()
  California us-west-1 : 2 subents 172.31.0.0/20 172.31.16.0/20
  Oregon us-west-2: : 4 subnets 172.31.0.0/20 172.31.16.0/20 172.31.32.0/20 172.31.48.0/20


## For later
- IPv6 CIDR block
