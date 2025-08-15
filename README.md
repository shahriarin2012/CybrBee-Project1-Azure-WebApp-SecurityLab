# CybrBee-Project1-Azure-WebApp-SecurityLab

 ## Executive Summary ##
 This project delivers a hands-on, three-day cybersecurity lab experience, simulating the full lifecycle of deploying and securing a cloud-hosted web application. Designed for practical, enterprise-relevant skill development, the lab incorporates Azure services, SSL/TLS encryption, web application firewall configuration, and cloud security best practices.

Day 1 focuses on foundational deployment. Participants create an Azure Web App, register a low-cost GoDaddy domain, and map it to Azure’s App Service. A Docker-based Cyber Blog Framework is deployed and customized with HTML to create a personalized cybersecurity blog containing original security articles.

Day 2 transitions to encryption and identity trust. Using Azure Key Vault and OpenSSL, a self-signed SSL certificate is generated, converted to PFX format, and bound to the web application. Azure-managed certificates are also deployed for a trusted, browser-recognized configuration. Participants compare the security trade-offs between self-signed and trusted certificates.

Day 3 elevates protection with Azure Web Application Firewall (WAF). Managed rules are analyzed to understand common web vulnerabilities, and a custom geolocation-based access rule is configured to block unwanted traffic. Microsoft Defender for Cloud is used to analyze and remediate security recommendations, ensuring the application meets best practice configurations.

Upon completion, participants will have:

Developed a fully deployed, encrypted, and WAF-protected Azure web application.

Gained practical experience in SSL/TLS management, cloud security configurations, and application hardening.

Built a showcase-ready cybersecurity blog to demonstrate technical skills to employers.

This repository contains documentation, configuration steps, and project deliverables for all three days. It serves as both a reference for future projects and a professional portfolio piece.

# Implementation Workflow #

# CybrBee Project #1 – Azure Web Application Security Lab

![Azure](https://img.shields.io/badge/Cloud-Azure-blue?logo=microsoftazure)
![Docker](https://img.shields.io/badge/Container-Docker-blue?logo=docker)
![Security](https://img.shields.io/badge/Security-SSL%2FTLS-green)
![Firewall](https://img.shields.io/badge/WAF-Enabled-orange)
![HTML](https://img.shields.io/badge/Language-HTML-lightgrey)

## 📌 Short Tagline
Three-day Azure security lab: build, encrypt, and protect a Docker-based web app with custom domain, SSL/TLS, WAF rules, and Defender for Cloud hardening.

---

## 📈 Project Workflow Overview

### **Day 1 – Build, Host, and Customize the Web Application**
**Objective:** Establish the foundational environment for the project by creating and hosting a cloud-based web application, configuring a custom domain, and deploying the application framework.  

**Step-by-Step Procedure:**
1. **Create an Azure Web App**
   - Log in to [Azure Portal](https://portal.azure.com) → **App Services** → **+ Create** → **Web App**.
   - Configure subscription, resource group, unique name, PHP 8.2, Linux OS, and Basic B1 plan.
   - Click **Review + Create** → **Create**.

     <img width="1890" height="781" alt="image" src="https://github.com/user-attachments/assets/d5064f3a-7209-4bb5-a659-de633001e869" />


2. **Register a Custom Domain via GoDaddy**
   - Purchase a `.club` or `.xyz` domain from [GoDaddy](https://www.godaddy.com) (1-year plan for discount).
   - Skip publishing the placeholder page.
   -  <img width="1712" height="340" alt="image" src="https://github.com/user-attachments/assets/ab7b4caf-f55b-4b12-9c6b-9b8e43af70ba" />


3. **Map Domain to Azure App Service**
   - In Azure App Service → **Custom Domains** → **Add Custom Domain**.
   - Get **A record** and **TXT record** from Azure.
   - Add them in GoDaddy DNS (TTL 1 hour) and remove the parked A record.
   - Validate and bind the domain in Azure.

4. **Deploy the Docker-Based Cyber Blog Framework**
   ```bash
   az webapp config container set \
     --name <webapp-name> \
     --resource-group <resource-group> \
     --docker-custom-image-name cyberxsecurity/project1-apachewebserver:4.0 \
     --enable-app-service-storage -t

5. **Customize HTML Content:**

SSH into container: Azure App Service → SSH → Go.

Edit /var/www/html/index.html to update:

Blog title, intro, email, LinkedIn link, profile image, and two blog posts.

Backup after edits:
cp /var/www/html/index.html /home

--------------------------------------------------------------------------------------------------------------------------------------------

### **Day 2 – Secure the Application with SSL/TLS**

**Objective:** Implement encryption for secure communications between clients and the web application.

Step-by-Step Procedure:

1. Create an Azure Key Vault

        - Name: project1-keyvault → same region as Day 1 → Standard tier.
        - Set Vault Access Policy for your account.

2. Generate Self-Signed Certificate with OpenSSL
         openssl req -x509 -sha256 -nodes -days 365 \
        -newkey rsa:2048 \
        -keyout project1_key.key \
        -out project1_cert.crt \
        -addext "extendedKeyUsage=serverAuth"



         - Fill in certificate details.

           - Convert to PFX:
   
           openssl pkcs12 -export \
           -out project1_cert.pfx \
           -inkey project1_key.key \
           -in project1_cert.crt

4. Import and Bind Self-Signed Certificate

       Azure Key Vault → Certificates → Import .pfx.

       App Service → Certificates → Add from Key Vault.

       Bind to domain under TLS/SSL Settings.

5. Deploy Azure-Managed Certificate

       App Service → TLS/SSL Settings → Managed Certificate → Create & bind.

6. Validate

       Check site in browser:

            Self-signed cert → security warning.

            Managed cert → no warning.



---------------------------------------------------------------------------------------------------------------------
### **Day 3 – Implement Advanced Protection **



**Objective:** Apply advanced security controls using Azure Web Application Firewall (WAF) and Microsoft Defender for Cloud.

Step-by-Step Procedure:

1. Create a WAF Policy

      Azure Portal → Web Application Firewall policies (WAF) → + Create.
  
      Select Regional WAF, match region, and associate with App Service or Front Door.

2. Analyze Managed Rules

     Review rules for SQL injection, XSS, etc.

     Enable/disable as needed.

3. Configure Custom Geo-Blocking Rule

   Custom Rules → + Add.
   
   Name: Project1Rule → Priority: 100.
   
   Match: Geo Location → Remote Address → is not → [USA, Canada, Australia].
   
   Action: Deny.

4. Remediate Security Recommendations

   In App Service → Microsoft Defender for Cloud.
   
   Apply fixes for HTTPS enforcement, TLS settings, backups, etc.

5. Final Verification

   Confirm geo-blocking works.
   
   Check Defender for Cloud shows improved security posture.


# ------------------------------------------------------------------------------------------


# Conclusion: 

This project exemplifies the integration of cloud technologies, web application security, and operational best practices in a structured, real-world scenario. By combining Azure’s scalable infrastructure, enterprise-grade encryption, and advanced firewall capabilities, it delivers both a functional solution and a demonstration of industry-aligned cybersecurity skills. The methodologies applied here can be adapted, extended, and scaled to meet diverse organizational security requirements while reinforcing a culture of proactive threat mitigation and operational excellence.

## Next Steps ##

Enhancement: Integrate automated CI/CD pipelines for continuous deployment and security validation.

Monitoring: Implement Azure Monitor and Application Insights for advanced performance tracking and anomaly detection.

Offensive Testing: Extend the lab with Kali Linux and Metasploitable2 to simulate penetration tests and validate defensive measures.

Scalability: Deploy the solution across multiple regions with load balancing for high availability and disaster recovery preparedness.

Compliance Alignment: Map configurations to compliance frameworks such as NIST CSF, ISO 27001, or CIS Benchmarks to demonstrate regulatory readiness.
