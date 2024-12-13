# Altcloud-Project

# Web Server Setup and Deployment  

This project demonstrates the process of provisioning a Linux server, setting up a web server, deploying a simple HTML landing page, and enabling HTTPS. It is designed to showcase basic cloud and web development skills.  

## Public IP Address  
Access the deployed web page at:  
**[https://13.41.189.61](https://13.41.189.61)**  

## Project Description  
This project involves 4 steps:  
1. Provisioning an EC2 instance on AWS with Ubuntu Linux.  
2. Installing and configuring the Nginx web server to serve an HTML page.  
3. Deploying an HTML landing page with a personal bio and project description.  
4. Configuring HTTPS using a free SSL certificate (Let’s Encrypt).  

## Steps to Reproduce  

### 1. Provision the Server  
1. Launch an EC2 instance on AWS using Ubuntu 20.04 LTS.  
2. Configure a Security Group to allow traffic on ports 22 (SSH) and 80 (HTTP).  
3. Connect to the instance via SSH using the provided public IP address.  

### 2. Install and Configure Nginx  
1. Update the package list:  
   ```bash
   sudo apt update
   ```  
2. Install Nginx:  
   ```bash
   sudo apt install nginx -y
   ```  
3. Start and enable the Nginx service:  
   ```bash
   sudo systemctl start nginx  
   sudo systemctl enable nginx  
   ```  

### 3. Deploy the HTML Page  
1. Navigate to the Nginx web root directory:  
   ```bash
   cd /var/www/html  
   ```  
2. Delete the default Nginx page:  
   ```bash
   sudo rm index.nginx-debian.html  
   ```  
3. Create a new `index.html` file with the following content:  
   ```html
       <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Victor C. Menyuah's Landing Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

</head>
<body>
    <main>
        <!-- Header Section -->
        <header>
            <h1>I'm Victor C. Menyuah</h1>
            <h2>Project Title: "Welcome to Victor C. Menyuah Landing Page"</h2>
        </header>

        <!-- Project Description Section -->
        <section>
            <h2>Project Description</h2>
            <p>
                This project involves setting up a Linux-based server on AWS to host a web application. We provisioned an EC2 instance, installed Nginx as the web server, and configured networking to allow HTTP traffic. A custom HTML landing page was created and deployed to demonstrate the team's capabilities. The setup also includes troubleshooting connectivity issues to ensure the page is accessible publicly.
            </p>
        </section>

        <!-- Biography Section -->
        <section id="biography">
            <h2>Biography</h2>
            <p>
                I am a dedicated and enthusiastic tech professional currently enrolled in a one-year cloud engineering program and pursuing a CCNA certification to deepen my understanding of networking. With a strong interest in web development, I design clean and responsive websites using HTML, CSS, and JavaScript.
            </p>
            <p>
                I am passionate about combining creativity and technology to solve problems. I hold a degree in Chemical Engineering, but my career pivot to technology has been fueled by my drive to make impactful contributions in the tech industry.
            </p>
            <p>
                In addition to my technical skills, I have experience creating dynamic websites and graphic designs, focusing on user-friendly interfaces. I am currently building projects like dynamic landing pages and charity foundation sites, which reflect my ability to learn quickly and adapt to various challenges.
            </p>
            <p>
                Beyond work, I enjoy contributing to community-building efforts, such as creating a WhatsApp community for teens interested in getting into tech related jobs. As a Nigerian, I draw inspiration from my diverse cultural background to bring unique perspectives to my projects.
            </p>
            <p>
                Fun Fact: I thrive on continuous learning and enjoy experimenting with daring and imaginative design ideas. My ultimate goal is to use technology to empower others and create meaningful solution
            </p>
        </section>
    </main>

    <!-- Footer Section -->
    <footer>
        <p>&copy; 2024 Victor C. Menyuah. All Rights Reserved.</p>
    </footer>
</body>
</html>
   </body>
   </html>
   ```  
4. Restart Nginx:  
   ```bash
   sudo systemctl restart nginx  
   ```  

### 4. Configure HTTPS (Optional Bonus)  
1. Install OpenSSL: Use a self-signed SSL certificate (not trusted by browsers but works for testing  
   ```bash
   sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt  
   ```  
2. Configure Nginx to use the certificate::  
   ```bash
   sudo nano /etc/nginx/sites-available/default 
   ```  
3. Add the following under server { :
   ```bash
   listen 443 ssl;
   ssl_certificate /etc/ssl/certs/nginx-selfsigned.crt;
   ssl_certificate_key /etc/ssl/private/nginx-selfsigned.key;

4. Ensure port 443 is open in your AWS security group.

5. Restart Nginx server:
   ```bash
   sudo systemctl restart nginx

6. Access your site via https://13.41.189.61 (you’ll see a browser warning because it’s self-signed).


## Screenshot  
Include a screenshot of the landing page displayed in a browser.  

## Files Included  
- `index.html` – The HTML file deployed on the server.  
- Screenshot of the deployed web page.   
