# Static-Website-hosting-using-AWS-S3-and-CloudFront

![image](https://github.com/user-attachments/assets/e8a12b39-1487-48eb-b7bd-6cde0f87c851)

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
   ![image](https://github.com/user-attachments/assets/da0beca2-3c59-44ad-853a-bbb1aa5df0b7)

2. **Click Create Bucket**.
   ![image](https://github.com/user-attachments/assets/f6013616-9483-43ab-b165-732f387cd622)

3. Choose a **bucket name** and select the region.
4. Block all **public access** to the bucket for security.
   ![image](https://github.com/user-attachments/assets/19e88396-2af6-4c34-abec-90c686bfc44d)

5. Click on **Create Bucket**.
   ![image](https://github.com/user-attachments/assets/170b8e40-326d-4f06-8a5d-1ed799c15c3e)

6. **Upload website files** (HTML, CSS, JavaScript, etc.) to the bucket by clicking on the bucket and then clicking **Upload**.
![image](https://github.com/user-attachments/assets/f9d722c6-9957-47a1-a330-fb159eaa8bc0)

7. Copy the web files from your local system to the S3 bucket
    ![image](https://github.com/user-attachments/assets/1e70013e-328e-484f-a29c-eb04aee4346d)

8. Click on upload
    ![image](https://github.com/user-attachments/assets/7f60b747-0e58-418b-91cf-a9f18dc0edac)



### Step 2: Request SSL Certificate via AWS Certificate Manager (ACM)
AWS Certificate Manager (ACM) is a service that simplifies the process of provisioning, managing, and deploying SSL/TLS certificates to secure network communications by enabling encryption for data in transit and establishing the identity of websites or applications. ACM helps protect your resources by ensuring encrypted connections, automating certificate renewal, and seamlessly integrating with AWS services like Elastic Load Balancing, CloudFront, and API Gateway, making it easy to enhance the security of your applications and websites.

1. **Search for ACM** and click on **Certificate Manager**.
2. Click on **Request a certificate**.
![image](https://github.com/user-attachments/assets/556fd948-6c31-43ce-b885-68cae48e338d)

3. Choose **Request a public certificate** and click **Next**.
![image](https://github.com/user-attachments/assets/6abe05a6-ebf8-421e-87fe-5e3c7e146bc8)

4. Enter your **domain name** (e.g., example.com).
  ![image](https://github.com/user-attachments/assets/6ccc7ca8-7c94-4e34-8eba-35de26861723)

5. Next, you would need to add another domain name to create a wildcard certificate. 
A wildcard certificate allows you to secure a domain and all its subdomains under a single certificate.
![image](https://github.com/user-attachments/assets/40894a3c-4687-4262-bb2a-e8022062c109)

6. Click **Request**.
    ![image](https://github.com/user-attachments/assets/f7730acb-7ea2-4e92-9bf8-53c3e71e2ced)

7. To validate the certificate, click **Create records in Route 53** and then **Create records** to confirm domain ownership.
![image](https://github.com/user-attachments/assets/5007d27b-b982-4e74-a945-0cd2e99d1565)
![image](https://github.com/user-attachments/assets/27258727-6072-4f95-8717-c3c6e289614b)


### Step 3: CloudFront Setup to Deliver Content
Amazon CloudFront is a content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers worldwide with low latency and high transfer speeds. It is integrated with other AWS services and offers robust security features like DDoS protection, encryption, and access controls.

1. **Search for CloudFront** and click on it.
2. Click **Create CloudFront Distribution**.
   ![image](https://github.com/user-attachments/assets/fbf3335f-afdf-4903-af47-bf3ec1aeae28)

3. In the **Origin Name**, select the S3 bucket you created.
   ![image](https://github.com/user-attachments/assets/2e1216fb-a875-4540-a987-86323cdf7042)

5. Choose **Legacy access identity** for the origin access and create a new **OAI** (Origin Access Identity).
   ![image](https://github.com/user-attachments/assets/9eb64f14-17c1-4b3b-ac1f-cd885c2e31ea)

6. Click Create new OAI, give it a name and then select Yes, update the bucket policy
   ![image](https://github.com/user-attachments/assets/1cdcd02f-ce12-4a06-b50c-ee511a146792)

7. **Enable HTTP to HTTPS redirection**.
    ![image](https://github.com/user-attachments/assets/0f1c94eb-6e37-45e7-8405-b18a272c9610)

8. Set **Alternate Domain Name** and select the **SSL certificate** you created.
    ![image](https://github.com/user-attachments/assets/d5632971-3fe0-46cb-baf0-fabb957bf7da)

9. Under custom SSL Certificate, choose the certificate we just created
    ![image](https://github.com/user-attachments/assets/d3229a89-48b6-4293-a041-8269eeae2448)

10. Set the **Default Root Object** to `index.html`.
    ![image](https://github.com/user-attachments/assets/a2b56677-d4e2-421d-b961-ec7cb60d1bb8)

11. Click **Create Distribution**.
    ![image](https://github.com/user-attachments/assets/05e5e699-3cb2-4988-9391-b8c6cb4eab57)

12. After the distribution is created, copy the **CloudFront domain name** and paste it in your browser to test.
![image](https://github.com/user-attachments/assets/2c1745e2-21e5-4c0e-bfc8-c6024bc1e547)

13. Below the outcome, our static website is running perfectly well
![image](https://github.com/user-attachments/assets/b1763b04-5d72-4e87-bfea-7b1f174bb987)


### Step 4: Connect Domain Name to CloudFront
Connecting a domain name to AWS CloudFront refers to the process of configuring a custom domain (such as www.example.com) to route traffic through Amazon CloudFront, which is a global Content Delivery Network (CDN). CloudFront caches and distributes your content—such as images, videos, web pages, and APIs—across a worldwide network of edge locations, ensuring that users access this content from the nearest geographic server for faster loading times and lower latency.

1. **Search for Route 53** and click on **DNS Management (Hosted Zones)**.
   ![image](https://github.com/user-attachments/assets/a346d0f9-5d1b-43e1-81e3-a7afaf0c3d58)

2. Select your **domain**.
   ![image](https://github.com/user-attachments/assets/baaaa184-3553-485f-9581-e4510d2a1730)

3. Click **Create Record** and turn on **Alias**. Point it to the CloudFront distribution.
   ![image](https://github.com/user-attachments/assets/42c48be6-eb33-40db-bf77-4e421a4dc2b8)
   ![image](https://github.com/user-attachments/assets/1d44edaa-5f1e-4c31-bb6a-b0b1e5ee4a0a)

4. Create another record for **www** as a **CNAME** and point it to the domain name.
   ![image](https://github.com/user-attachments/assets/23936ab6-40f3-4800-9e5a-90cad58df46c)

5. **Test** the Route 53 configuration by copying the domain name and pasting it in the browser.
    ![image](https://github.com/user-attachments/assets/8243ea82-9422-4aa1-8a7c-a28e00dc588b)

6. Browser outcome
![image](https://github.com/user-attachments/assets/2b409b35-2693-42a5-a7e7-e08613099b0f)


## Conclusion
Hosting a static website using AWS S3 and CloudFront provides a robust, scalable, and cost-effective solution for delivering high-performance content to users worldwide. By leveraging Amazon S3 for secure and reliable storage and Amazon CloudFront for global content delivery, the project ensures minimal latency, enhanced security, and seamless scalability to meet varying traffic demands.  
The integration of SSL/TLS encryption, custom domain configurations, and caching optimizations further enhances the website’s security and user experience.  
This project demonstrates how AWS services can be effectively combined to deliver a professional-grade static website hosting solution that is both user-friendly and business-ready.
