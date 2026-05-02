# Project 1: Static Website Hosting with AWS S3 + CloudFront

> Day 1 of 30 Day DevOps HandsOn Challenge  
> *Live URL:* https://d3grv3lzzu4qgs.cloudfront.net

## 📋 Overview
This project deploys a static website using AWS S3 for storage and CloudFront as a global CDN. The setup follows AWS security best practices: the S3 bucket remains private and is only accessible through CloudFront using Origin Access Control (OAC).

## 🛠️ Tech Stack
- *AWS S3* - Object storage for static files
- *AWS CloudFront* - Global CDN with free HTTPS
- *Origin Access Control (OAC)* - Secure S3 access without public bucket policy
- *Git + GitHub* - Version control and documentation

## 🏗️ Architecture
User → CloudFront (HTTPS) → S3 Bucket (Private via OAC)
*Key Security Features:*
1. S3 bucket has all public access blocked
2. CloudFront uses OAC to read from S3 privately  
3. Free TLS certificate via `*.cloudfront.net`
4. `Default root object: index.html` configured

## 🚀 Deployment Steps

### 1. Create Project & Initialize Git
Created `index.html` and initialized local repository.

![Git Init](1.png)

### 2. Push Initial Code
git remote add origin https://github.com/amtulsaboor/Project-1-static-website-s3-cloudfront.git
git branch -M main
git push -u origin main
![Git Push](2.png)

### 3. Create S3 Bucket
- *Bucket name:* `project-1-static-website-s3-cloudfront-amtulsaboor`
- *Region:* `us-east-1`
- *Public access:* All blocked
- *Uploaded:* `index.html`

*Verification:* Direct S3 URL access denied. Confirms bucket is private.

![S3 Access Denied](3.png)

### 4. Create CloudFront Distribution
- *Origin:* S3 bucket with OAC enabled
- *Default root object:* `index.html`
- *HTTPS:* Enabled by default

### 5. Test Live Site
After CloudFront status = `Enabled`, the site is accessible globally.

![Live Site](4.png)

## ✅ Result
*Live URL:* https://d3grv3lzzu4qgs.cloudfront.net

## 💡 What I Learned
| **Concept** | **Takeaway** |
| **S3 Static Hosting** | Keep buckets private. Never use public ACL for production |
| **CloudFront + OAC** | OAC replaced OAI. Secure way to connect CloudFront to private S3 |
| **Default Root Object** | CloudFront won't serve `/` without `index.html` set |
| **AWS Console Bugs** | Wizard loops on `Edit`. Solution: create first, patch settings after deploy |
## 🐛 Troubleshooting Notes
1. *`Access Denied` XML from S3 URL:* Expected. Proves bucket is private.
2. *`403 Forbidden` from CloudFront:* Fixed by setting `Default root object = index.html`
3. *GitHub UI upload fails:* Use `git push` from terminal instead

## 🔗 Links
- *Live Site:* https://d3grv3lzzu4qgs.cloudfront.net
- *GitHub Repo:* https://github.com/amtulsaboor/Project-1-static-website-s3-cloudfront

---
*Deployed by:* Amtal Saboor  
*Date:* May 2, 2026  
*Challenge:* 30 Day DevOps HandsOn ‎<This message was edited>
