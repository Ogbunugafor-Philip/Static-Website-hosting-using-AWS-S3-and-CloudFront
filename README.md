# Static-Website-hosting-using-AWS-S3-and-CloudFront

## Introduction
AWS offers a scalable and cost-effective solution for hosting static websites using Amazon S3 and Amazon CloudFront. S3 provides secure, durable, and highly available storage to host your static content, such as HTML, CSS, and JavaScript files.  
CloudFront, a global Content Delivery Network (CDN), complements S3 by caching your website’s content at edge locations worldwide, ensuring faster delivery and reduced latency for users. It also supports SSL/TLS encryption, custom domains, and caching optimization for enhanced security and performance.  
Together, S3 and CloudFront enable you to host reliable, secure, and high-performance static websites with ease.

## Project Objectives
- Host static website files on Amazon S3 for cost-effective, highly available, and durable storage.
- Deliver content globally with Amazon CloudFront, reducing latency and enhancing user experience.
- Secure the website by enabling SSL/TLS encryption and implementing robust access control measures.

## Project Steps

### Step 1: S3 Bucket Setup for Website Hosting
1. **Search for S3** and click on it.
2. **Click Create Bucket**.
3. Choose a **bucket name** and select the region.
4. Block all **public access** to the bucket for security.
5. Click on **Create Bucket**.
6. **Upload website files** (HTML, CSS, JavaScript, etc.) to the bucket by clicking on the bucket and then clicking **Upload**.

### Step 2: Request SSL Certificate via AWS Certificate Manager (ACM)
1. **Search for ACM** and click on **Certificate Manager**.
2. Click on **Request a certificate**.
3. Choose **Request a public certificate** and click **Next**.
4. Enter your **domain name** (e.g., example.com).
5. Optionally, add another domain name to create a **wildcard certificate**.
6. Click **Request**.
7. To validate the certificate, click **Create records in Route 53** and then **Create records** to confirm domain ownership.

### Step 3: CloudFront Setup to Deliver Content
1. **Search for CloudFront** and click on it.
2. Click **Create CloudFront Distribution**.
3. In the **Origin Name**, select the S3 bucket you created.
4. Choose **Legacy access identity** for the origin access and create a new **OAI** (Origin Access Identity).
5. **Enable HTTP to HTTPS redirection**.
6. Set **Alternate Domain Name** and select the **SSL certificate** you created.
7. Set the **Default Root Object** to `index.html`.
8. Click **Create Distribution**.
9. After the distribution is created, copy the **CloudFront domain name** and paste it in your browser to test.

### Step 4: Connect Domain Name to CloudFront
1. **Search for Route 53** and click on **DNS Management (Hosted Zones)**.
2. Select your **domain**.
3. Click **Create Record** and turn on **Alias**. Point it to the CloudFront distribution.
4. Create another record for **www** as a **CNAME** and point it to the domain name.
5. **Test** the Route 53 configuration by copying the domain name and pasting it in the browser.

## Conclusion
Hosting a static website using AWS S3 and CloudFront provides a robust, scalable, and cost-effective solution for delivering high-performance content to users worldwide. By leveraging Amazon S3 for secure and reliable storage and Amazon CloudFront for global content delivery, the project ensures minimal latency, enhanced security, and seamless scalability to meet varying traffic demands.  
The integration of SSL/TLS encryption, custom domain configurations, and caching optimizations further enhances the website’s security and user experience.  
This project demonstrates how AWS services can be effectively combined to deliver a professional-grade static website hosting solution that is both user-friendly and business-ready.
