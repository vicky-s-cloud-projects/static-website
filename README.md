# A Simple Floppy Bird Static Website Hosted on AWS (IAM + S3 + CloudFront + Route 53 + ACM + WAF)

This repository contains the source code for a fully production-ready static website deployed on Amazon Web Services. The architecture follows modern cloud engineering best practices including private S3 hosting, CloudFront CDN distribution with HTTPS, domain routing via Route 53, and security enforcement via AWS WAF.

---

## 🚀 Project Overview

This project demonstrates how to deploy a highly available, secure, and globally distributed Floppy Bird static website using AWS services. The goal is to showcase cloud engineering skills and build a portfolio-ready cloud-native solution.

---

## 🏗️ Architecture: 

## Architecture Diagram: 

<img width="890" height="626" alt="image" src="https://github.com/user-attachments/assets/723ead11-bac2-474b-a599-cc320b6fce5c" />


### **Services Used**

* **Amazon S3 (private)** — stores static website files
* **CloudFront (OAC-enabled)** — global CDN with HTTPS
* **Origin Access Control (OAC)** — ensures only CloudFront can access S3
* **Amazon Route 53** — custom domain DNS routing
* **AWS Certificate Manager (ACM)** — SSL/TLS certificate for HTTPS
* **AWS WAF** — Web Application Firewall to protect CloudFront

### **High-Level Flow**

1. User requests `https://vivekchalla.online`
2. DNS (Route 53) routes the user to CloudFront
3. CloudFront serves cached content or fetches from S3 via OAC
4. S3 remains private—only CloudFront can access it
5. WAF filters malicious traffic before CloudFront



## 🧊 Deployment Summary

Below is a simplified summary of how the website was deployed:

### **1. Create S3 Bucket (Private)**

* Block Public Access enabled
* Static website hosting disabled
* Uploaded files from local Ubuntu linux Command line interface to AWS s3 bucket

* <img width="1920" height="1035" alt="Screenshot (4)" src="https://github.com/user-attachments/assets/bb39d296-ca8f-45e3-9ae8-0636770378cc" />
 

### **2. Create CloudFront Distribution**

* S3 bucket as origin (REST endpoint)
* Origin Access Control (OAC) enabled
* Default root object: `index.html`
* HTTPS enforced (redirect HTTP → HTTPS)

* <img width="1913" height="1037" alt="Screenshot (5)" src="https://github.com/user-attachments/assets/6472da89-329c-4637-a80d-6932f0435573" />

* <img width="1920" height="1038" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/312552ed-506f-447f-a3c1-7e800f65ef44" />


### **3. Request ACM Certificate** (in **us-east-1**)

* DNS validation

* <img width="1913" height="1038" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/d5b063c5-0b2b-4127-8cb3-908a9f7f41d6" />


### **4. Configure Route 53**

* A records (Alias) → CloudFront distribution

### **5. Apply AWS WAF Web ACL**

* Added AWS Managed rules
* Associated with CloudFront

* <img width="1920" height="1038" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/826c735e-2af8-4a6b-bf43-cb775cf83bfe" />


---

## 📦 Future Enhancements

Here are ideas to extend this project:

* Add CI/CD via GitHub Actions for automatic deployment to S3
* Add logging & metrics using CloudWatch
* Use Terraform/CloudFormation for full IaC automation
* Add versioning and lifecycle policies to S3

---

## 💡 How to Deploy New Website Updates

After updating your files locally:

1. Upload updated files to S3 via the AWS Console
2. (Optional) Create a CloudFront cache invalidation for instant refresh

---


## 🙋 Author

Designed & deployed as part of cloud engineering learning and portfolio building.

---

If you find this useful, feel free to ⭐ the repository!
