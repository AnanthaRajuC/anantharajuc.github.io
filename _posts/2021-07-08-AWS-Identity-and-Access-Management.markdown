---
title: "AWS Identity and Access Management (IAM) : User groups, Policies and Users"
author: anantharajuc
categories: [ Cloud, AWS ]
layout: post
date: 2021-07-08 09:50
image: /assets/images/aws-iam.jpg
---

This post briefly documents the process of creating AWS IAM **User groups**, and attaching **permissions policies** to it and then creating the **Users** and adding them to the created User groups via the **Identity and Access Management (IAM)** service.

---

#### Minimum Requirements

- Access to [AWS Management Console](https://aws.amazon.com/console/)

#### User Groups

By default only the **`Root`** user account has the access to **`Billing Information`**. Access to the same can be provided to other user accounts by activating the **`IAM`** access to the Billing Information.

- Naviagte to **`My Account`** page by clicking on the link available on the top-right corner. Scroll down to **`IAM User and Role Access to Billing Information`** section and click on **Edit**

- select the **`Activate IAM Access`** checkbox and click on the **`Update`** Button.

![Enabling Non-Root user accounts to access Billing Information]({{ site.baseurl }}/assets/images/aws-billing-alert/1.PNG)  

---

#### Billing Preferences

At the top of the screen, on the left side navigation bar. Click on the **`Billing Preferences`** option. Select the following checkboxes:

- **Receive PDF invoice by Email**  
- **Receive Free Tier Usage Alert** (*This is different from Billing Alarm*)   
- **Receive Billing Alerts** (*Mandatory for setting up Billing Alarm in CloudWatch service*)  

Click on the **`Save Preferences`** button.

![Billing Preferences]({{ site.baseurl }}/assets/images/aws-billing-alert/2.PNG)  

---

#### Setting-up CloudWatch to create a Billing Alarm

CloudWatch is a monitoring service, it can be used for performance monitoring. Metrics associated with billing can also be monitored.

Change the region to **`US East (N. Virginia) us-east-1`**. All billing information is located within this region.

Navigate to **`CloudWatch`** service under the **`Management & Governance`** section.

- Click on **`Billing`** menu on the left side navigation bar. 
- Click on **`Create Alarm`** button.

![Billing alarms]({{ site.baseurl }}/assets/images/aws-billing-alert/3.PNG)  

- Click on **`Select Metric`** button.

![Metric]({{ site.baseurl }}/assets/images/aws-billing-alert/4.PNG)  

- Click on the **`Billing`** Metrics option.

![Billing metric]({{ site.baseurl }}/assets/images/aws-billing-alert/5.PNG)  

- Click on the **`Total Estimated Charge`** Metrics option.

![Total Estimated Charge]({{ site.baseurl }}/assets/images/aws-billing-alert/6.PNG)  

- Select the **`USD`** Currency option.
- Click on **`Select metric`** button on the bottom right.

![Metrics USD]({{ site.baseurl }}/assets/images/aws-billing-alert/7.PNG)  

Under the **`Conditions`** section, select the *Threshold type* as **`Static`**. Define the alarm condition *Whenever Estimation charges is* as **`Greater`** and define the *threshold value* as some **`USD`** value which is acceptable to you, say for example **`10`**.

When there is a forecast from AWS that you will exceed the 10 USD spend, you will receive a Billing Alarm.

![Conditions]({{ site.baseurl }}/assets/images/aws-billing-alert/8.PNG)  

- Click on **Next** button in the same page. There we will configure notifications.

Set **`Alarm State trigger`** to **`In alarm`** mode.

Select **`Create new topic`** option to create a new *SNS Topic*.

Configure a new topic name and the email endpoint that must receive the notifications and click on **`Create topic`** button.

At the bottom of the page, click on the **Next** button.

![Notification]({{ site.baseurl }}/assets/images/aws-billing-alert/9.PNG)  

- Add **`Name`** and **`Description`** to the alarm. and click on the **Next** button.

![Name and Description]({{ site.baseurl }}/assets/images/aws-billing-alert/10.PNG)  

- On the next page, review the details and at the bottom of the page click on the **`Create Alarm`** button.

![Billing Alarms Success]({{ site.baseurl }}/assets/images/aws-billing-alert/11.PNG)  

**Note** : *You will receive an email with a link to confirm the subscription to that topic*.

---

#### Overview

**SNS Topics Details**.

![SNS Topic Details]({{ site.baseurl }}/assets/images/aws-billing-alert/12.PNG)  

**CloudWatch overview**.

![CloudWatch overview]({{ site.baseurl }}/assets/images/aws-billing-alert/13.PNG)  

**CloudWatch overview of Billing Service**.

![CloudWatch overview of Billing Service]({{ site.baseurl }}/assets/images/aws-billing-alert/14.PNG)  

---