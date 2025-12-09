---
title: "Week 3 Worklog"
date: 2025-08-25
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Goals:

* Set up VPC Peering
* Learn about AWS Transit Gateway
* Deploy Wordpress on AWS Cloud

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                   | Start Date   | Completion Date | Reference Material                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------- |
| 2   | - Set up VPC Peering <br>&emsp; + Initialize CloudFormation Template <br>&emsp; + Create Security Group <br>&emsp; + Create EC2 instance <br>&emsp; + Update Network ACL               | 25/08/2025   | 25/08/2025      | <https://000019.awsstudygroup.com/vi/1-introduce/> |
| 3   | - Set up VPC Peering <br>&emsp; + Create Peering Connection <br>&emsp; + Enable Cross-Peer DNS <br>&emsp; + Clean up resources                                                        | 26/08/2025   | 26/08/2025      | <https://000019.awsstudygroup.com/vi/6-crosspeerdns/> |
| 4   | - Learn about AWS Transit Gateway <br>&emsp;- **Practice:** <br>&emsp; + Create Key Pair <br>&emsp; + Initialize CloudFormation Template <br>&emsp; + Create Transit Gateway           | 27/08/2025   | 27/08/2025      | <https://000020.awsstudygroup.com/vi/> |
| 5   | - Learn about AWS Transit Gateway <br>&emsp;**Practice:** <br>&emsp; + Create Transit Gateway Attachments <br>&emsp; + Create Transit Gateway Route Tables <br>&emsp; + Add Transit Gateway Routes to VPC Route Tables <br>&emsp; + Clean up resources | 28/08/2025   | 28/08/2025      | <https://000020.awsstudygroup.com/vi/> |
| 6   | - Deploy Wordpress on AWS Cloud <br>&emsp;**Practice:** <br>&emsp; + Prepare VPC and Subnet <br>&emsp; + Create Security Group for EC2 <br>&emsp; + Create Security Group for Database Instance <br>&emsp; + Initialize EC2 Instance <br>&emsp; + Initialize Database Instance | 29/08/2025   | 29/08/2025      | <https://000021.awsstudygroup.com/> |

### Week 3 Achievements:

* Learned Networking – VPC Peering
  * Initialized CloudFormation Template for testing environment
  * Created Security Group for EC2 instance
  * Created EC2 instance for Peering connection
  * Updated Network ACL to ensure connectivity between subnets
  * Created VPC Peering connection between two VPCs
  * Enabled Cross-Peer DNS Resolution for domain name resolution via Peering
  * Cleaned up resources after successful testing

* Learned Networking – AWS Transit Gateway
  * Understood the role of Transit Gateway in connecting multiple VPCs and on-premise networks
  * Created, attached, and managed Transit Gateway Attachments and Route Tables for centralized traffic routing
  * Ensured stable and scalable routing compared to VPC Peering

* Practiced initial deployment of Wordpress on AWS Cloud:
  * Successfully deployed Wordpress environment with EC2 Instance (application) and Database Instance (MySQL/RDS)
  * Set up networking (VPC, Subnet) and security permissions using Security Groups to ensure application safety
  * Connected Wordpress application to the database and successfully tested the deployment

