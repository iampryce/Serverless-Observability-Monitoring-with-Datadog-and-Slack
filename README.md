<p align="center"> 

  <img width="175" height="183" alt="image" src="https://github.com/user-attachments/assets/d1c44199-c6a9-458f-81a5-8c7a9cbc201d" />

<p/>


<h1 align="center">
Serverless Observability with Datadog and Slack
  
  <h1/>

  <p align="center">


## 📌Project Overview


This monitoring and Alerting stack was implemented on top of the serverless web architecture project:  https://github.com/iampryce/Production-Grade-Serverless-Web-Architecture-with-CI-CD-Integration

This observability layer provides real-time monitoring, alerting, and operational visibility. 


## 🔋 Services Used

![Datadog](https://img.shields.io/badge/Datadog-632CA6?style=for-the-badge&logo=datadog&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)
![Monitoring](https://img.shields.io/badge/Monitoring-Production%20Ready-success?style=for-the-badge)
![Observability](https://img.shields.io/badge/Observability-Enabled-orange?style=for-the-badge)


## Steps

## 1.  Connected AWS to Datadog Using Cloudformation

- _I installed AWS integration in datadog, this set up uses cloudformation stack to set up an iamrole for datadog usage_
- _The iamroles give datadog the permision to access cloudwatch metrics_


<img width="534" height="267" alt="datadog cloud formation stack" src="https://github.com/user-attachments/assets/53dd1e69-2766-4568-9b05-376a6af25385" />

https://github.com/user-attachments/assets/9b660423-aac3-4aac-afac-69ab56cc2582


Stack created ✔

<img width="600" height="300" alt="stack created" src="https://github.com/user-attachments/assets/a02aae01-e360-4ae5-8707-c8ee39429c41" />

AWS account added to Datadog ✔

<img width="602" height="300" alt="AWS account added to datadog" src="https://github.com/user-attachments/assets/3dfaba91-dded-4dee-a1d1-f5c612f65477" />

## 2. Selected the services for metrics ingestion in datadog

_I selected the services i wish to collect metrics from.  Lambda, API Gateway, CloudFront, SES_

Note: Datadog now has access to collect metrics but we need to specify which services metrics we want.


<img width="600" height="300" alt="services metrics selected" src="https://github.com/user-attachments/assets/6d510fcd-f6b4-4dbe-927d-76f0fe93146a" />


## 3. Connected Slack to Datadog

_i installed slack integration in datadog and connected my workspace and channel_

<img width=600" height="300" alt="slack connected" src="https://github.com/user-attachments/assets/e3e55267-ccaf-4b15-bef5-40dd4f0851a3" />




