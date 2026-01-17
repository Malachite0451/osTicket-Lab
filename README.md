# osTicket Helpdesk Home Lab

## Overview
This project is a fully functional **osTicket helpdesk deployment** designed to simulate a real-world IT service desk environment. The goal of this lab is to gain hands-on experience with ticket-based support workflows, Linux server administration, web application deployment, and backend service integration commonly used in enterprise IT environments.

The environment consists of a dedicated Debian Linux server hosting osTicket, backed by an Apache web server, PHP application stack, and MariaDB database. The system provides both a user-facing ticket submission portal and an agent/admin interface used to manage, triage, and resolve support requests.

This lab represents **Phase 1** of a multi-phase support infrastructure build. The current deployment operates as a standalone helpdesk system and is designed to be integrated with an existing Active Directory environment in a future phase.

---

## Lab Environment
- **Hypervisor:** Oracle VirtualBox  
- **Operating System:** Debian GNU/Linux 12 (Bookworm)  
- **Web Server:** Apache 2  
- **Database:** MariaDB  
- **Application Stack:** PHP 8.2  
- **Ticketing Platform:** osTicket v1.18.x  

---

## Core Components
- osTicket helpdesk platform
- Apache web server hosting PHP-based application
- MariaDB backend database
- Linux-based server administration
- Web-based user and agent interfaces
- Role-based agent access within osTicket

---

## Architecture & Design

The osTicket deployment follows a traditional single-host application architecture commonly used in small to mid-sized environments:

- One dedicated Linux server
- Apache serving osTicket over HTTP
- PHP handling application logic
- MariaDB storing ticket, user, and configuration data
- Separation between user portal and agent/admin interface

The environment was intentionally kept simple in Phase 1 to ensure stability, clarity, and ease of troubleshooting before introducing external integrations.

---

## Security & Access Model

Access within the osTicket environment is designed to reflect real-world service desk operations while maintaining appropriate separation of responsibilities.

### User Access
- End users access the helpdesk via the web-based ticket submission portal
- Users can create, view, and respond to their own tickets
- No server or administrative access is granted to users

### Agent and Admin Access
- Support agents authenticate through the osTicket agent control panel
- Administrative access is restricted to designated admin accounts
- Configuration changes are limited to the admin interface
- Backend system access (Linux, database) is restricted to server administrators only

### Server Security
- Database access is limited to a dedicated application user
- Database credentials are not shared with system users
- Configuration files are locked down post-installation
- Unused installation components are removed after setup

This layered access model ensures clear separation between users, support staff, and system administrators.

---

## Support Workflow

The lab implements a structured helpdesk workflow designed to mirror real-world IT support operations.

### Ticket Lifecycle
- Users submit tickets through the web portal
- Tickets are categorized using help topics and departments
- Agents review, respond to, and resolve tickets
- Tickets are closed once issues are resolved

### Agent Capabilities
- View and manage assigned tickets
- Communicate with users through ticket threads
- Update ticket status and resolution notes
- Escalate or reassign tickets as needed

### Operational Design
- Centralized ticket queue for support visibility
- Clear separation between user-facing and agent-facing interfaces
- Consistent workflow regardless of ticket type

This workflow demonstrates core service desk operations commonly used in desktop support and NOC environments.

---

## Installation & Configuration Summary

High-level deployment steps included:
1. Installing Debian 12 with a minimal configuration
2. Installing and configuring Apache, PHP, and MariaDB
3. Securing the database using vendor-recommended hardening tools
4. Creating a dedicated database and user for osTicket
5. Deploying osTicket into the Apache web root
6. Completing the web-based installer
7. Performing post-install cleanup and permission hardening
8. Validating application functionality through test tickets

Detailed step-by-step procedures and configuration notes are documented in the `/docs` directory.

---

## Troubleshooting & Lessons Learned

During deployment, several real-world issues were encountered and resolved, including:
- PHP version and extension compatibility issues
- Missing IMAP dependency causing installer failures
- HTTP 500 Internal Server Errors traced via Apache logs
- Database authentication errors due to credential mismatches
- File ownership and permission problems affecting configuration files

These issues were resolved through log analysis, dependency validation, and controlled configuration changes rather than reinstallation, reflecting real-world troubleshooting practices.

---

## Validation
The deployment was validated by:
- Successful access to the user ticket submission portal
- Successful access to the agent and admin control panel
- Creation and resolution of test tickets
- Verification of system stability after service restarts

---

## Future Enhancements (Phase 2)
Planned improvements include:
- Active Directory / LDAP authentication integration
- Centralized user authentication for ticket submission
- Email (SMTP) integration for ticket notifications
- HTTPS configuration using TLS certificates
- Backup and recovery planning
- Integration with existing Active Directory home lab

---

## Documentation
Supporting documentation, configuration notes, and screenshots are available in the `/docs` and `/screenshots` directories.

---

## Skills Demonstrated
- Linux server administration (Debian)
- Apache web server configuration
- PHP application deployment and troubleshooting
- MariaDB database administration
- Log analysis and error diagnosis
- Web application security hardening
- Ticket-based support workflows
- Service desk operations and documentation
- Troubleshooting under real-world constraints
- Technical documentation and system design communication
