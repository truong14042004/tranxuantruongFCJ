---
title: "Week 4 Worklog"
date: 2025-09-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Goals:

* Continue deploying Wordpress on AWS Cloud
* Get familiar with Amazon Relational Database Service (Amazon RDS)

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                   | Start Date   | Completion Date | Reference Material                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------- |
| 2   | - Deploy Wordpress on AWS Cloud <br>&emsp; + Install httpd service <br>&emsp; + Install php-mysql <br>&emsp; + Install php7.3 <br>&emsp; + Move the directory to where Wordpress will be executed to proceed with downloading and installing Wordpress <br>&emsp; + Open a web browser and access the EC2 webserver's public IPv4 DNS address <br>&emsp; + Set up basic parameters for Wordpress to log in to the Wordpress admin interface | 01/09/2025   | 01/09/2025      | <https://000021.awsstudygroup.com/> |
| 3   | - Deploy Wordpress on AWS Cloud <br>&emsp; + Create Autoscaling for Wordpress Instance: <br>&emsp; + Create AMI from Webserver Instance DNS <br>&emsp; + Create Launch Template <br>&emsp; + Create Target Group <br>&emsp; + Create Load Balancer <br>&emsp; + Create Auto Scaling Group | 02/09/2025   | 02/09/2025      | <https://000021.awsstudygroup.com/> |
| 4   | - Deploy Wordpress on AWS Cloud <br>&emsp; + Backup and restore database <br>&emsp; + Create CloudFront for Web Server <br>&emsp; + Clean up resources | 03/09/2025   | 03/09/2025      | <https://000021.awsstudygroup.com/> |
| 5   | - Get familiar with Amazon Relational Database Service (Amazon RDS) <br>&emsp;**Practice:** <br>&emsp; + Create VPC <br>&emsp; + Create EC2 Security Group <br>&emsp; + Create RDS Security Group <br>&emsp; + Create DB Subnet Group | 04/09/2025   | 04/09/2025      | <https://000005.awsstudygroup.com/vi/4-create-rds/> |
| 6   | - Get familiar with Amazon Relational Database Service (Amazon RDS) <br>&emsp;**Practice:** <br>&emsp; + Create EC2 instance <br>&emsp; + Create RDS database instance <br>&emsp; + Deploy application <br>&emsp; + Backup and restore <br>&emsp; + Clean up resources | 05/09/2025   | 05/09/2025      | <https://000005.awsstudygroup.com/vi/4-create-rds/> |

### Week 4 Achievements:

* Deployed Wordpress on AWS Cloud
  * Successfully installed Wordpress on EC2 Webserver, accessible via IPv4 Public DNS.
  * Set up basic parameters and logged in successfully.
  * Built Autoscaling mechanism for Wordpress Instance using AMI, Launch Template, Load Balancer, Target Group, and Auto Scaling Group, enabling flexible system scalability.
  * Performed backup and restore of the Wordpress database to ensure data availability.
  * Integrated CloudFront to distribute static content, increase access speed, and improve user experience.

* Got familiar with Amazon Relational Database Service (Amazon RDS)
  * Learned how to operate RDS and related components: VPC, Security Group, DB Subnet Group.
  * Successfully created RDS Database Instance and connected it to EC2 for application deployment.
  * Practiced management operations: backup, restore, and resource cleanup.



