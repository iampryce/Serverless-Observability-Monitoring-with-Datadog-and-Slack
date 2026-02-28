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

![Main-Architecture](https://github.com/user-attachments/assets/793213a6-8942-40a5-a562-fc3134efabae)



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

<img width="600" height="300" alt="metrics  flow validation" src="https://github.com/user-attachments/assets/0a53b929-c152-4fcc-b3df-266f2895fa6d" />


## 3. Connected Slack to Datadog

_i installed slack integration in datadog and connected my workspace and channel_



<img width="600" height="300" alt="slack connected" src="https://github.com/user-attachments/assets/ac35417f-a7d6-46b8-98b3-c82d142c61ac" />

## 4. Creating Each Monitor and Alerts in Datadog

### Alert 1 : API Gateway 5XX Errors (You can use template and adjust to your taste in datadog)

 User Impact:  Contact form submission fails for the visitor, whenever there is a failure in form submision an alert will be generated

Note: To generate alert, I made some changes in the lambda code and sumbmited a form. This will automatically generate error message.

<img width="700" height="300" alt="Api gateway 5XX error 1" src="https://github.com/user-attachments/assets/cb6616b4-390d-4acb-8fb5-09e6e62f61c0" />



https://github.com/user-attachments/assets/8e9ff184-c20b-41a0-857c-8f9c17fe352e


Slack notification Verified ✔

<img width="700" height="300" alt="Api gateway Alert Verified 2" src="https://github.com/user-attachments/assets/60d1c722-747d-47a2-85b0-6007442d13ec" />


### Alert 2 : Lambda Function Errors



