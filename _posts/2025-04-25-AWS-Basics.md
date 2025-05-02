---
title: "AWS Basics"
date: 2025-04-25 15:20:00
categories: [ Miscellaneous ]
tags: [ Miscellaneous ]
---



{% include toc title="Index" %}

### What is cloud?
Cloud is the combination of multiple servers.
There are different types of Cloud services like on-premises,Iaas,Caas,Paas,Faas,Saas. <br>
Most of the companies use Caas,Paas

### AWS Modules
IAM (Identity Access Management): which contains users,roles,user groups etc..<br>
EC2 ---> Virtual Servers of cloud(It will give virtual servers).<br>
Elastic BeanStalk --> Place where we run and manage web apps.supports 5000 port<br>
ECS --> This is where you run containers<br>
ECR --> This is where you store containers<br>
EKS(Elastic Kubernetes Service)<br>
AWS S3 --> Storage place,where you can upload your file and get the url.<br>
AWS RDS --> where we create database.<br>
Multiple combine servers combine them called clusters.<br>
A policy is an object in AWS that defines permissions.

### IAM User

### Elastic BeanStalk(Creating Environment for Java application)
--> First created a jar file from java application which has spring web.<br>
--> Deploy that jar file in Elastic Beanstalk by creating a Environment where we also need to add a role that we created <br>
--> I got a domain link after creating environment, from that we can access application <br>


### Aurora & RDS
Here i created DB-identifier(sa-db) by choosing postgresql database and giving inputs like port,username,password after creating we will get Endpoint.<br>
I have used that end point to connect RDS through local postgres using all the credentials that i have given there.<br>
To connect to AWS RDS from local postgres you need to Server->Registers->server(there we need to give Name,need to give Endpoint in connection with username and password)<br>
--> After Connection we change localhost to aws domain name(Endpoint) and username,password details in application properties of java application.
<br>
**After that create a jar file and deploy that file in Elastic Beanstalk by creating Environment by this we achieved keeping application and database in AWS.
