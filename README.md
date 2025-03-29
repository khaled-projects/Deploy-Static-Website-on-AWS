# Deploy Static Website on AWS

Welcome to the Deploy Static Website on AWS guide! This document provides step-by-step instructions to host a static website using AWS S3 and CloudFront.

CloudFront Endpoint
Your deployed website is accessible at:
https://d2f6xogq7yp8ia.cloudfront.net

## Steps to Deploy a Static Website on AWS

### 1. Create an S3 Bucket

Create an S3 bucket to store your static website files.

```bash
aws s3 mb s3://my-static-website --region us-east-1

```
### 2. Enable Static Website Hosting
Enable static website hosting on your S3 bucket:

```bash
aws s3 website s3://my-static-website --index-document index.html
```
### 3. Set Bucket Permissions
Modify the bucket policy to allow public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-static-website/*"
    }
  ]
}
### 4. Configure CloudFront Distribution
Create a CloudFront distribution for better performance and security.

```bash
aws cloudfront create-distribution --origin-domain-name my-static-website.s3.amazonaws.com

Once the distribution is created, use the CloudFront Endpoint URL to access your website.

### 5. Test Your Website
Open the following URL in your browser:
https://d2f6xogq7yp8ia.cloudfront.net

## Your static website is now live on AWS!
