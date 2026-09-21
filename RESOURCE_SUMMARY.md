# AWS Terraform Network — Resource Summary

## Purpose

This project demonstrates a small, reusable AWS network built with Terraform. It creates the networking foundation needed for a simple public workload without provisioning an application server.

## Resources created

| Resource | Purpose |
|---|---|
| VPC | Provides an isolated AWS network using `10.0.0.0/16`. |
| Public subnet | Provides a subnet using `10.0.1.0/24` for resources that need internet connectivity. |
| Internet Gateway | Connects the VPC to the internet. |
| Public route table | Adds a default route (`0.0.0.0/0`) through the Internet Gateway and is associated with the public subnet. |
| Security group | Allows inbound SSH on TCP/22 and HTTP on TCP/80, plus unrestricted outbound traffic. |

## Design notes

- Terraform variables keep the region, CIDRs, project name, SSH source ranges, and tags configurable.
- Outputs expose the IDs of the major resources for reuse by future Terraform modules or workloads.
- No EC2 instance is included because it is outside the requested scope.
- SSH should be restricted to a trusted IP range for any non-lab environment.
