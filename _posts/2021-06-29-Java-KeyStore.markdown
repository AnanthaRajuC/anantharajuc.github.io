---
title: "Adding SSL Certificate to Java KeyStore"
author: anantharajuc
categories: [ Java, SSL Certificate ]
layout: post
date: 2021-06-29 18:30
image: /assets/images/java-keystore.png
---

This post briefly documents the process of adding a URLs security certificate to [Java KeyStore](https://en.wikipedia.org/wiki/Java_KeyStore) to mitigate the error of **“PKIX path building failed”** and **“unable to find valid certification path to requested target”** errors.

[Example](https://stackoverflow.com/questions/21076179/pkix-path-building-failed-and-unable-to-find-valid-certification-path-to-requ) issue filed on StackOverflow.

---

#### Minimum Software Requirements

- Java
- Web Browser (Chrome, Firefox, etc.,)

#### Sample Scenario

We will be using https://stackoverflow.com/ as the resource from which we will be exporting the security certificate and adding to the Java KeyStore on our local machine from which we would like to access the URL/API programmatically.

Replace https://stackoverflow.com/ URL with any other URL with which you're facing the certification error.

#### Process to export the security certificate

01. Click on the green lock icon in the URL bar of the web browser and click on **`Certificate`** option in the drop-down list.

![Green Lock Icon]({{ site.baseurl }}/assets/images/java-keystore/1-green-lock-icon.png)  

02. Click on  **`Details`** tab.

![Details Tab]({{ site.baseurl }}/assets/images/java-keystore/2-details-tab.PNG)  

03. Click on **`Copy to file`** button. 

![Copy to file]({{ site.baseurl }}/assets/images/java-keystore/3-copy-to-file.PNG)  

04. Click on **`Next`** button.

![Next]({{ site.baseurl }}/assets/images/java-keystore/4-next.PNG)  

05. Select the **`Base-64 encoded X.509 (.CER)`** format radio button option and click on **`Next`** button.

![Base-64 encoded X.509 CER)]({{ site.baseurl }}/assets/images/java-keystore/5-base-64.PNG)  

06. Click on the browse option and navigate to the location (folder) where you'd like the file to be saved, enter a desired file name and Click on **`Next`** button.

![Save]({{ site.baseurl }}/assets/images/java-keystore/6-save.PNG)  

![Save]({{ site.baseurl }}/assets/images/java-keystore/7-save.PNG)  

07. Settings of the certificate being exported is presented to you for review.

![Review]({{ site.baseurl }}/assets/images/java-keystore/swagger-ui.PNG)  

08. Finally, click on the **`Finish`** button to complete the certificate export process.

![Finish]({{ site.baseurl }}/assets/images/java-keystore/8-finish.PNG)  

![Ok]({{ site.baseurl }}/assets/images/java-keystore/9-ok.PNG)  

Finally, the certificate will be saved in the selected location.

![Certificate]({{ site.baseurl }}/assets/images/java-keystore/10-certificate.PNG)  

#### Process to add the exported security certificate to Java KeyStore

Open command prompt as Administrator and navigate to the location were the certificate was exported to.

Issue the following command, 

**`keytool -import -alias stackoverflow -keystore  "C:\Program Files\Java\jre1.8.0_25\lib\security\cacerts" -file stackoverflow.cer`**

Enter the keystore password as **`changeit`**

![Command]({{ site.baseurl }}/assets/images/java-keystore/11-issue-command.PNG)  

When Prompted with the question **Trust this certificate? [no]:**, type **yes** 

![Prompt]({{ site.baseurl }}/assets/images/java-keystore/12-trust-certificate-prompt.PNG)  

#### Links

[KeyStore Explorer](https://keystore-explorer.org/index.html)

---