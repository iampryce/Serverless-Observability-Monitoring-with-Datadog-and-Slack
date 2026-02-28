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

![Main-Architecture](https://github.com/user-attachments/assets/6aeb6d1a-da9c-4952-8a13-97e89c4fc2be)




## 🔋 Services Used

![Datadog](https://img.shields.io/badge/Datadog-632CA6?style=for-the-badge&logo=datadog&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)
![Monitoring](https://img.shields.io/badge/Monitoring-Production%20Ready-success?style=for-the-badge)
![Observability](https://img.shields.io/badge/Observability-Enabled-orange?style=for-the-badge)


## Steps

## 1.  Connected AWS to Datadog Using Cloudformation

- _I installed AWS integration in datadog, this set up uses cloudformation stack to set up an iamrole for datadog usage_
- _The iamroles give datadog the permision to access cloudwatch metrics_


<img width="834" height="467" alt="datadog cloud formation stack" src="https://github.com/user-attachments/assets/53dd1e69-2766-4568-9b05-376a6af25385" />

https://github.com/user-attachments/assets/9b660423-aac3-4aac-afac-69ab56cc2582


Stack created ✔

<img width="800" height="400" alt="stack created" src="https://github.com/user-attachments/assets/a02aae01-e360-4ae5-8707-c8ee39429c41" />

AWS account added to Datadog ✔

<img width="802" height="400" alt="AWS account added to datadog" src="https://github.com/user-attachments/assets/3dfaba91-dded-4dee-a1d1-f5c612f65477" />

## 2. Selected the services for metrics ingestion in datadog

_I selected the services i wish to collect metrics from.  Lambda, API Gateway, CloudFront, SES_

Note: Datadog now has access to collect metrics but we need to specify which services metrics we want.


<img width="800" height="400" alt="services metrics selected" src="https://github.com/user-attachments/assets/6d510fcd-f6b4-4dbe-927d-76f0fe93146a" />

<img width="800" height="400" alt="metrics  flow validation" src="https://github.com/user-attachments/assets/0a53b929-c152-4fcc-b3df-266f2895fa6d" />


## 3. Connected Slack to Datadog

_i installed slack integration in datadog and connected my workspace and channel_



<img width="800" height="400" alt="slack connected" src="https://github.com/user-attachments/assets/ac35417f-a7d6-46b8-98b3-c82d142c61ac" />

## 4. Creating Monitor and Alerts in Datadog

### Alert 1 : API Gateway 5XX Errors Monitor (You can use template and adjust to your taste in datadog)

User Impact:

_If something breaks in the backend, the contact form will fail for the visitor. When this happens, a 5XX error is returned and an alert is generated automatically._


Note:
_To test this, I modified the Lambda function to cause an error and submitted the form. This triggered a 5XX response and Datadog sent an alert to Slack._

<img width="800" height="400" alt="Api gateway 5XX error 1" src="https://github.com/user-attachments/assets/cb6616b4-390d-4acb-8fb5-09e6e62f61c0" />


https://github.com/user-attachments/assets/8e9ff184-c20b-41a0-857c-8f9c17fe352e


Slack API gateway notification Verified ✔

<img width="800" height="400" alt="Api gateway Alert Verified 2" src="https://github.com/user-attachments/assets/60d1c722-747d-47a2-85b0-6007442d13ec" />


### Alert 2 : Lambda Function Errors Monitor

User Impact:

_If the Lambda function crashes or throws an error, the contact form cannot complete successfully and the request fails._

Note:
_To test this monitor, I introduced a temporary error in the Lambda code and submitted the form. This increased the Lambda error metric and triggered an alert in Slack._

https://github.com/user-attachments/assets/de8bbce7-7d83-4eec-9486-971956008f42

Slack Lambda notification Verified ✔

<img width="1340" height="607" alt="Lambda alerts verified" src="https://github.com/user-attachments/assets/6a88b59a-727c-4c9a-9c4c-0ae2c785d486" />

### 3 : Lambda Duration Delay Monitor

User Impact:
_If the Lambda function starts taking longer than expected to process requests, users may experience slow responses or potential timeouts when submitting the contact form._

Note:
_To test this monitor, I temporarily added a delay inside the Lambda function and submitted the form multiple times. This increased the execution duration metric and triggered an alert in Slack._

<img width="800" height="403" alt="delay code for lambda duration" src="https://github.com/user-attachments/assets/ca42e166-7308-487f-afac-e7862ba33015" />


https://github.com/user-attachments/assets/05aa28a9-66ae-4f8c-9bae-ab42dcd3762f

Slack Lambda duration monitor notification Verified ✔

Note: _After testing i set the alert threshold back to 8000 and removed the delay code to avoid Unnecessary alerts_

<img width="800" height="400" alt="Lambda duration delay alert" src="https://github.com/user-attachments/assets/58682218-6a89-41fe-b1ed-9329708a7b38" />


### 4 : CloudFront Error Rate Monitor

User Impact:
_If the origin becomes unavailable or misconfigured, users may not be able to load the website, resulting in 403 or 404 errors._

Note:
_To validate this monitor, I temporarily renamed the index.html file in the S3 bucket and created a CloudFront invalidation to clear the cached content. After refreshing the website multiple times, CloudFront returned error responses, which increased the error rate metric and triggered an alert in Slack._


<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/69697ccd-99bb-4949-85a0-768a6181c8f1" />




https://github.com/user-attachments/assets/a68e89ec-fea6-4251-9588-3c4a353cc80c



<img width="800" height="400" alt="cloudfront error 403" src="https://github.com/user-attachments/assets/75ae1695-98ce-4631-9ee6-9dd0e6eeffe5" />

Slack Cloudfront error rate monitor notification Verified ✔

<img width="1284" height="652" alt="cloudfront slack notification verified" src="https://github.com/user-attachments/assets/f747031e-d42e-49a2-ad03-cdc683e41de6" />



## ✅ Project Conclusion

This project demonstrates the design and implementation of a production-grade serverless architecture built on AWS with full automation and monitoring.

What started as a simple static website evolved into a complete cloud-native system featuring:

Global content delivery via CloudFront

Serverless backend powered by API Gateway and AWS Lambda

Automated CI/CD deployments using GitHub Actions

Infrastructure management with CloudFormation

Real-time monitoring and alerting using Datadog and Slack

Beyond just building the system, controlled failure simulations were performed to validate monitoring pipelines and alert reliability. This ensures the architecture is not only automated, but also observable and production-aware.
