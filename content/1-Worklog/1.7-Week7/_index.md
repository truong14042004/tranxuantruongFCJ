---
title: "Week 7 Worklog"
date: 2025-10-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Goals:

* Manage access to EC2 Resource Tag service with AWS IAM.
* Get started with Grafana on AWS.
* LIMIT USER PERMISSIONS WITH IAM PERMISSION BOUNDARY

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                   | Start Date   | Completion Date | Reference Material                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------- |
| 2   | - Manage access to EC2 Resource Tag service with AWS IAM <br> - Create policies with roles that can be used by certain users <br>&emsp; + Create IAM User <br>&emsp; + Create IAM Policy <br>&emsp;**Practice:**  <br>&emsp; + Create IAM Role    <br>&emsp; + Log in to AWS Management Console and access IAM Management Console. <br>&emsp; + Create role   <br>&emsp; + Create an IAM role for EC2 Administrator user with the policies created above.                                                              | 20/10/2025   | 20/10/2025      |<https://000028.awsstudygroup.com>
| 3   | - Manage access to EC2 Resource Tag service with AWS IAM. <br>- Test policies<br>&emsp; + Switch Role <br>&emsp; + Check IAM Policy<br>&emsp; + Access EC2 console in AWS Region - Tokyo <br>&emsp; + Access EC2 console in AWS Region - North Virginia <br>&emsp; + Create EC2 instance with and without Tags that meet the conditions<br>&emsp; + Edit Resource Tag on EC2 Instance<br>&emsp; + Test policies <br>&emsp; + Clean up resources                                 | 21/10/2025   | 21/10/2025      | <https://000028.awsstudygroup.com> |
| 4   | - Get started with Grafana on AWS <br>- Preparation steps: <br>&emsp;**Practice:** <br>&emsp;  + Create VPC and subnet <br>&emsp; +   Create Security Group  <br>&emsp; + Create EC2 Instance <br>&emsp; + Create IAM User <br>&emsp; + Create IAM Role <br>&emsp; + Assign IAM Role<br>- Install Grafana<br>- Monitor with Grafana  | 22/10/2025   | 22/10/2025      | <https://000029.awsstudygroup.com> |
| 5   | - LIMIT USER PERMISSIONS WITH IAM PERMISSION BOUNDARY  <br>- Prepare AWS account with IAM enabled. <br>&emsp; + Create Policy <br>&emsp; + Copy the JSON from the workshop into the field <br>&emsp; + Skip tagging and select Next: Review<br>&emsp; + Name the policy ec2-admin-restrict-region.       | 23/10/2025   | 23/10/2025       | <https://000030.awsstudygroup.com/vi/3-createpolicy> |
| 6   | - LIMIT USER PERMISSIONS WITH IAM PERMISSION BOUNDARY <br>&emsp;**Practice:** <br>&emsp; + Create an IAM user and apply permission boundary to the user <br>&emsp; + Check Limited IAM User <br>&emsp; + Check if the user assigned AmazonEC2FullAccess is restricted by Permission Boundary <br>&emsp; + Clean up resources                                                                                        | 24/10/2025   | 24/10/2025      | <https://000030.awsstudygroup.com/vi/3-createpolicy>|

### Week 7 Achievements:

* Managed access to EC2 service with AWS IAM (Resource Tag):
  * Understood and applied IAM Policy mechanism to control EC2 access based on Resource Tag.
  * Created and assigned IAM Role/Policy to users, thereby restricting EC2 instance operations according to defined tags.
  * Successfully tested policies by creating/editing EC2 instances in different regions.

* Got started with Grafana on AWS:
  * Installed and deployed Grafana on EC2.
  * Understood IAM Role assignment and data monitoring integration.
  * Built a basic monitoring environment with Grafana, enabling more visual monitoring of AWS systems and applications.

* Limited permissions with IAM Permission Boundary:
  * Learned the concept of Permission Boundary to control the maximum scope of IAM User permissions.
  * Deployed permission boundary policies.
  * Successfully tested: even when the user is granted AmazonEC2FullAccess, actions outside the allowed scope are still restricted.



