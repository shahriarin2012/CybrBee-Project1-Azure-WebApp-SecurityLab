# CybrBee-Project1-Azure-WebApp-SecurityLab

This project delivers a hands-on, three-day cybersecurity lab experience, simulating the full lifecycle of deploying and securing a cloud-hosted web application. Designed for practical, enterprise-relevant skill development, the lab incorporates Azure services, SSL/TLS encryption, web application firewall configuration, and cloud security best practices.

Day 1 focuses on foundational deployment. Participants create an Azure Web App, register a low-cost GoDaddy domain, and map it to Azure’s App Service. A Docker-based Cyber Blog Framework is deployed and customized with HTML to create a personalized cybersecurity blog containing original security articles.

Day 2 transitions to encryption and identity trust. Using Azure Key Vault and OpenSSL, a self-signed SSL certificate is generated, converted to PFX format, and bound to the web application. Azure-managed certificates are also deployed for a trusted, browser-recognized configuration. Participants compare the security trade-offs between self-signed and trusted certificates.

Day 3 elevates protection with Azure Web Application Firewall (WAF). Managed rules are analyzed to understand common web vulnerabilities, and a custom geolocation-based access rule is configured to block unwanted traffic. Microsoft Defender for Cloud is used to analyze and remediate security recommendations, ensuring the application meets best practice configurations.

Upon completion, participants will have:

Developed a fully deployed, encrypted, and WAF-protected Azure web application.

Gained practical experience in SSL/TLS management, cloud security configurations, and application hardening.

Built a showcase-ready cybersecurity blog to demonstrate technical skills to employers.

This repository contains documentation, configuration steps, and project deliverables for all three days. It serves as both a reference for future projects and a professional portfolio piece.

# Deepdive into Workflow

![Azure](https://img.shields.io/badge/Cloud-Azure-blue?logo=microsoftazure)
![Docker](https://img.shields.io/badge/Container-Docker-blue?logo=docker)
![Security](https://img.shields.io/badge/Security-SSL%2FTLS-green)
![Firewall](https://img.shields.io/badge/WAF-Enabled-orange)
![HTML](https://img.shields.io/badge/Language-HTML-lightgrey)

## 📌 Overview
**CybrBee Project #1** is a structured, three-day cloud security lab that simulates enterprise-grade web application deployment and protection on Microsoft Azure. You’ll configure a custom domain, deploy a Docker-based site, implement SSL/TLS with both self-signed and managed certificates, and enable WAF protections with Defender for Cloud hardening.

---

## 🚀 Project Timeline

### Day 1 – Build & Deploy
- Create Azure Web App
- Register and map GoDaddy domain
- Deploy Docker-based Cyber Blog Framework
- Customize HTML content

### Day 2 – Secure with SSL/TLS
- Create Azure Key Vault
- Generate self-signed cert with OpenSSL; convert to PFX
- Import & bind cert to App Service
- Add Azure-managed certificate for trusted TLS
- Compare certificate trust models

### Day 3 – Advanced Protection
- Create Azure WAF policy (regional) and analyze managed rules
- Add custom geo-based access rule
- Use Microsoft Defender for Cloud to remediate recommendations

---

## 🛠 Technologies
- **Platform:** Microsoft Azure  
- **Domain Provider:** GoDaddy  
- **Containerization:** Docker  
- **Security:** Azure Key Vault, SSL/TLS, WAF  
- **Analysis:** Microsoft Defender for Cloud  
- **Tools:** OpenSSL, Bash CLI, HTML  

---
