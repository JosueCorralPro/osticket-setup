# osTicket Implementation Project

## Project Summary

### Description
This project is a **full implementation of osTicket**, an open-source ticketing system for IT support and customer service. The project provides a step-by-step guide on installing, configuring, and customizing osTicket in a **Windows Server** environment.

### Technologies & Environments Used
- **Languages:** PHP, MySQL
- **Environments:** Windows Server 2022, Ubuntu (for MySQL), Windows 10 (client-side)
- **Applications & Services:**
  - osTicket
  - XAMPP (for Apache & MySQL)
  - Active Directory (for user authentication)
  - Azure (optional VM deployment)

## Installation & Configuration

### 1. Setting Up Windows Server & Ubuntu
- Install Windows Server 2022
- Set up an Ubuntu machine for database hosting (MySQL)
- Configure network settings for communication between machines

### 2. Installing Required Software
- Install XAMPP (Apache, MySQL, PHP) on Windows Server
- Set up osTicket in XAMPP’s **htdocs** folder
- Configure **PHP.ini** settings (e.g., enabling extensions)

### 3. Database Setup
- Create a **MySQL database** for osTicket
- Assign a user with appropriate permissions
- Modify osTicket configuration to connect to the database

### 4. osTicket Configuration
- Install osTicket through the web setup
- Configure ticket categories, SLA, and user roles
- Enable email piping for automated ticket creation

### 5. Active Directory Integration
- Connect osTicket to **Active Directory (AD)** for user authentication
- Configure LDAP settings and test authentication

### 6. Customization & Automation
- Modify UI theme for branding
- Set up **automated ticket assignments**
- Implement custom email notifications

## Demonstration

### Screenshots & Video Walkthrough
- Installation process with screenshots
- Demonstration of ticket creation & assignment
- AD user login demonstration

## Conclusion
This project showcases a **fully functional osTicket help desk** that integrates with Active Directory and MySQL for a robust IT support system. It provides a **scalable** and **efficient** ticketing solution for enterprises.
