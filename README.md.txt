# Static Website Hosting on AWS

This project hosts a static HTML page using AWS S3, CloudFront, and Route53.

## Services Used
- Amazon S3
- CloudFront (CDN)
- Route53 (DNS)

## Architecture
S3 → CloudFront → Route53 (Custom Domain)


static-website-s3/
├── index.html
├── error.html
├── README.md


🛠️ Step-by-Step Setup:

-Create S3 Bucket

Name: babujalpan.com (or any)

Region: ap-south-1 (Mumbai)

Disable “Block All Public Access”

Upload your files: index.html and error.html

Enable Static Website Hosting

Go to bucket → Properties → Static Website Hosting → Enable

Index: index.html, Error: error.html

Add Bucket Policy (to allow public access):

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::babujalpan.com/*"
    }
  ]
}


Use CloudFront:

-Create a distribution with origin as your S3 static URL

-Enable HTTPS, caching, etc

Domain Mapping with Route53:

-Create hosted zone

-Add A record pointing to CloudFront URL