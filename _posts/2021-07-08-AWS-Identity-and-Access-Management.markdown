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

- From the services drop down from the Navigation bar, select the **`Identity and Access Management (IAM)`** service. 

- From the left side navigation pane under **`Access Management`**, select the **`User groups`** option and click on the **`Create group`** button.

![User groups]({{ site.baseurl }}/assets/images/aws-iam/23.PNG)  

- In the following page, Name the group.

![Name the group]({{ site.baseurl }}/assets/images/aws-iam/24.PNG)  

- Under the **`Attach permissions policies`** section, attach all the needed policies as per the requirement.

![Attach permissions policies]({{ site.baseurl }}/assets/images/aws-iam/25.PNG)  

---

#### Users 

- From the left side navigation pane under **`Access Management`**, select the **`Users`** option and click on the **`Add user`** button.

![Users]({{ site.baseurl }}/assets/images/aws-iam/26.PNG)  

- In the following page, set the **`User name`**.

- under the **`Select AWS access type`**, configure how the user will access AWS with the Access type option. Programmatic access, AWS Management Console access. Set the console password or autogenerate it.

- click on **`Next: Permissions`** button

![Add user]({{ site.baseurl }}/assets/images/aws-iam/27.PNG)  

##### Permissions

- Add the user to the previously created **`User group`**.

- click on **`Next: Tags`** button.

![Permissions]({{ site.baseurl }}/assets/images/aws-iam/28.PNG)  

---

##### Tags

- Add tags as a **Key : Value** pair as per the need.

- click on **`Next: Review`** button.

![Tags]({{ site.baseurl }}/assets/images/aws-iam/29.PNG)  

---

##### Review

- All the selected options from the previous steps are presented for your review. Should you find any discrepencies, go back to the previous steps and fix them accordingly. Once everything is as per your need, click on the **`Create user`** button.

- click on **`Next: Review`** button. On the next page you will see a **`Success`** message upon the creation of the new user. click on the **`Close`** button.

![Review]({{ site.baseurl }}/assets/images/aws-iam/30.PNG)  

![Success]({{ site.baseurl }}/assets/images/aws-iam/31.PNG) 

---

##### User

- In the Users section, you will see the newly created user. Click on the user.

![User]({{ site.baseurl }}/assets/images/aws-iam/32.PNG)  

- Click on the **`Security credentials`** tab, click on **`Create access key`** if you'd like to create **`Access key`** for this user.

![Security credentials]({{ site.baseurl }}/assets/images/aws-iam/33.PNG)  

![Access Key]({{ site.baseurl }}/assets/images/aws-iam/34.PNG)  

---

#### Overview

**Sign in**

![Sign in]({{ site.baseurl }}/assets/images/aws-iam/36.PNG)  

**Sign in as IAM User**

![Sign in as IAM User]({{ site.baseurl }}/assets/images/aws-iam/37.PNG)  

**Logged-in user**

![Logged-in user]({{ site.baseurl }}/assets/images/aws-billing-alert/38.PNG)  

---