# ☁️ Task 6: Host and Deploy a Web Application on the Cloud

## 🎯 Objective
To deploy a static web application that allows users to download the **FlowTune JavaFX App** using the **AWS Cloud (S3 Static Website Hosting)**.  
This task demonstrates real-world cloud deployment, public access setup, and website hosting.

---

## 💡 Project Overview
**FlowTune** is a simple **JavaFX desktop application** packaged as a `.jar` file.  
The cloud deployment includes:
- A **pastel-dark themed HTML landing page**
- A **download link** for the `FlowTune-1.0.0.jar`
- Public hosting on **AWS S3 Free Tier**

Website URL:  
👉 [http://flowtune-hansika.s3-website-us-east-1.amazonaws.com](http://flowtune-hansika.s3-website-us-east-1.amazonaws.com)

---

## 🛠️ Tools & Technologies
- **Amazon Web Services (AWS S3)** – Static website hosting  
- **HTML, CSS** – Frontend  
- **JavaFX** – App UI  
- **Maven** – Build and package `.jar`  
- **VS Code / IntelliJ IDEA** – Development environment  

---

## 🚀 Deployment Steps (AWS S3)
1. **Build the JavaFX App**
   ```bash
   mvn clean package
   
2.The compiled .jar file will appear in the target/ folder as:`FlowTune-1.0.0.jar`

## Step 3 — Create an S3 Bucket

Open AWS Management Console → S3

Click Create bucket

Enter a name (e.g., flowtune-hansika)

Uncheck “Block all public access”

Click Create bucket
## Step 4 — Upload Your Files

Open your new bucket → Objects tab

Upload:
index.html
FlowTune-1.0.0.jar
After upload, select each file → Actions → Make public using ACL


## Step 5 — Enable Static Website Hosting

Go to Properties → Static website hosting

Click Edit → Enable

Choose:

Hosting type: Host a static website
Index document: index.html


Save changes.


## Step 6 — Set Public Access Policy

Go to Permissions → Bucket Policy and paste the following JSON:

`{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::flowtune-hansika/*"
    }
  ]
}`


Then click Save.

Copy your Website endpoint URL — this is your public site link.


## Step 7 — Verify Your Website

Open your Website Endpoint in a browser:

`http://flowtune-hansika.s3-website-us-east-1.amazonaws.com`


You should see the FlowTune JavaFX App landing page (dark-pastel themed).

Clicking the “Download FlowTune” button should start downloading:

`FlowTune-1.0.0.jar`

## Learning Outcome

By completing this task, I learned how to:

Configure AWS S3 for static web hosting

Manage public access and bucket policies

Deploy a JavaFX app download page to the cloud

Understand endpoint-based website access

Host applications efficiently using AWS Free Tier

