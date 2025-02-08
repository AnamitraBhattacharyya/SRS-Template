# Software Requirements Specification
## For Citizen HelpDesk Portal

Version 0.1  
Prepared by Anamita Bhattachayya 
Group 24
<date 1.2.25>  

Table of Contents
=================
* [Revision History](#revision-history)
* 1 [Introduction](#1-introduction)
  * 1.1 [Document Purpose](#11-document-purpose)
  * 1.2 [Product Scope](#12-product-scope)
  * 1.3 [Definitions, Acronyms and Abbreviations](#13-definitions-acronyms-and-abbreviations)
  * 1.4 [References](#14-references)
  * 1.5 [Document Overview](#15-document-overview)
* 2 [Product Overview](#2-product-overview)
  * 2.1 [Product Perspective](#21-product-perspective)
  * 2.2 [Product Functions](#22-product-functions)
  * 2.3 [Product Constraints](#23-product-constraints)
  * 2.4 [User Characteristics](#24-user-characteristics)
  * 2.5 [Assumptions and Dependencies](#25-assumptions-and-dependencies)
  * 2.6 [Apportioning of Requirements](#26-apportioning-of-requirements)
* 3 [Requirements](#3-requirements)
  * 3.1 [External Interfaces](#31-external-interfaces)
    * 3.1.1 [User Interfaces](#311-user-interfaces)
    * 3.1.2 [Hardware Interfaces](#312-hardware-interfaces)
    * 3.1.3 [Software Interfaces](#313-software-interfaces)
  * 3.2 [Functional](#32-functional)
  * 3.3 [Quality of Service](#33-quality-of-service)
    * 3.3.1 [Performance](#331-performance)
    * 3.3.2 [Security](#332-security)
    * 3.3.3 [Reliability](#333-reliability)
    * 3.3.4 [Availability](#334-availability)
  * 3.4 [Compliance](#34-compliance)
  * 3.5 [Design and Implementation](#35-design-and-implementation)
    * 3.5.1 [Installation](#351-installation)
    * 3.5.2 [Distribution](#352-distribution)
    * 3.5.3 [Maintainability](#353-maintainability)
    * 3.5.4 [Reusability](#354-reusability)
    * 3.5.5 [Portability](#355-portability)
    * 3.5.6 [Cost](#356-cost)
    * 3.5.7 [Deadline](#357-deadline)
    * 3.5.8 [Proof of Concept](#358-proof-of-concept)
* 4 [Verification](#4-verification)
* 5 [Appendixes](#5-appendixes)
Software Requirements Specification (SRS) for Citizen HelpDesk Portal
Revision History
|           Name         | Date     |                         Reason For Changes                    |   Version   |

| Anamitra Bhattachayya  | 2025-2-1 |                           Initial Draft                       | 1.0         |

|         Ayan Panda     |  2025-2-4 |   	         Refined and Expanded Draft with References        |     1.1      |


Export to Sheets:
1. Introduction

1.1 Document Purpose:
This document defines software requirements for a web-based, citizen helpdesk portal designed for public grievance and complaint management. It's a comprehensive guideline for all involved parties, which include developers, testers, project managers, officials from the governmental side, and citizens, regarding the functionality and performance of this system.

1.2 Product Scope:
The Citizen HelpDesk Portal will enable citizens to easily file complaints about public services, transparenly and automatically track the status of their complaints, and automatically receive updates on the status at regular intervals. Government authorities would have their own admin dashboard to manage and resolve complaints effectively. Scope includes complaint registration, tracking, notifications, admin dashboard, reporting, user management, security features, and accessibility considerations. The integration of existing government legacy systems is excluded from the initial release but will be considered for future phases.


1.3 Definitions, Acronyms and Abbreviations:

SRS: Software Requirements Specification
UI: User Interface
API: Application Programming Interface   
Admin: Administrator
UAT: User Acceptance Testing
CRUD: Create, Read, Update, Delete
OTP: One-Time Password
WCAG: Web Content Accessibility Guidelines
GDPR: General Data Protection Regulation
CCPA: California Consumer Privacy Act
1.4 References

ISO/IEC/IEEE 29148:2018 : Systems and software engineering — Requirements engineering. (This standard provides guidance on writing good software requirements specifications.)
WCAG 2.1: Web Content Accessibility Guidelines. (Essential for ensuring accessibility for users with disabilities.)
OWASP Top 10: Open Web Application Security Project Top 10. (A standard awareness document for web application security.)
1.5 Document Overview

This document is structured into the following sections: Introduction, Product Overview, Requirements, Verification, and Appendixes.  Each section provides progressively more detailed information about the Citizen HelpDesk Portal.

2. Product Overview:

2.1 Product Perspective:
The Citizen HelpDesk Portal will be a standalone web application that can be accessed by regular web browsers (Chrome, Firefox, Safari, Edge) on desktops and mobile phones. It will be built on a modern, scalable architecture, with a robust backend system (PHP Laravel or Python Flask) and relational database (PostgreSQL). The application will be deployed on a cloud hosting server platform (e.g., AWS, Google Cloud, Azure) to offer scalability, reliability, and security. The cloud hosting will also simplify maintenance and updating.
2.2 Product Functions:

Complaint Registration:

Complaints can be submitted by filling in detailed descriptions (free text, character limit), location of the problem (through a map interface with address auto-complete and/or manual address input), type of complaint (e.g., sanitation, infrastructure, utilities, water supply, electricity, etc., with a predefined list controlled by the admin), and uploading attached documents (images, PDFs, with size and type restrictions).

The system will validate all input fields, including required fields, data formats, file sizes, and file types. Clear error messages will be displayed to guide the user.
On successful submission, the system will automatically generate a unique tracking ID for the complaint, which will be displayed to the citizen and sent via email/SMS.

Complaint Tracking:

Complaints can be tracked by citizens in real-time using the unique tracking ID.
The status updates will be clearly shown, with timestamps and descriptions of each step (e.g., Submitted, Acknowledged, Assigned to an Official, In Progress, Resolved, Closed).
Citizens can choose to receive status updates via email, SMS, or both, and can customize their notification preferences.

Automated Alerts:

The system will automatically send email/SMS alerts to citizens at critical status changes, e.g., when the complaint is acknowledged by an official, when it is assigned, when work begins, when it is resolved, and when it is closed.
The content of the notifications will be clear and concise, with the tracking ID and a brief description of the status change.
The system will allow administrators to set the notification templates and the events that trigger notifications.

Admin Dashboard:

Secure login with role-based access control (e.g., admin, supervisor, officer). Two-factor authentication (2FA) using OTP is recommended.
Dashboard summary with key performance indicators (KPIs) such as number of open complaints, complaints by category, average time to close, and officer performance. Visualizations (charts, graphs) will be used to display this effectively.
Complaint Management: Admins can view, filter, sort (date, category, status, etc.), assign complaints to concerned officials, and update complaint status. Bulk operations (assigning multiple complaints) will be facilitated.

User Management: Admins can manage government official user accounts, such as creating new accounts, editing accounts, assigning roles and permissions, and resetting passwords.

Reporting Module: Offer complaint statistics reports (e.g., number of complaints by category, resolution time, officer performance, trends over time). Reports should be exportable to various formats (CSV, PDF, Excel).

User Management (Admin):

Full CRUD operations for government official accounts.
Fine-grained role-based access control, which enables fine-grained control over user permissions.
Password management features such as password reset and strong password policy enforcement.

2.3 Product Constraints:
Technology decisions and infrastructure spend will be impacted by budget restrictions.
The system must be compliant with applicable data privacy laws, for example, GDPR and CCPA, to safeguard citizen data.
Integration with current government legacy systems is not in the first phase scope but is a future enhancement opportunity.

2.4 User Characteristics:

Citizens: Users will be technically knowledgeable to varying degrees and may be multi-lingual. The system will be intuitive, user-friendly, and usable by a variety of users. Multi-lingual capability will be needed.
Government Authorities: Government authorities will be technically proficient to varying degrees. Proper training manuals and user manuals will be provided.

2.5 Assumptions and Dependencies:

It is assumed that there is reliable internet connectivity for government users and citizens.
Government officials will be provided with the required hardware (smartphones and computers) and software (browsers).
There will be a secure and reliable email/SMS gateway service for notifications.

2.6 Apportioning of Requirements

All requirements outlined in this document are considered essential for the initial release of the Citizen HelpDesk Portal unless explicitly stated otherwise.

3. Requirements:
3.1 External Interfaces:

3.1.1 User Interfaces:
Web-based Interface: Accessible through modern web browsers (Chrome, Firefox, Safari, Edge) on desktop and mobile devices.
Responsive Design: The interface must be responsive to different screen sizes and orientations, providing an optimal user experience across devices. A mobile-first approach is recommended.
Multi-language Support: The portal must be multi-language. A language selection option (e.g., dropdown menu) must be present on all pages. The content, such as labels, messages, and help text, must be translated. A translation management option (e.g., a translation management system) must be present for the admin interface.
Accessibility: The portal must adhere to WCAG 2.1 Level AA guidelines to provide accessibility for people with disabilities. This includes features like keyboard navigation, screen reader support, alternative text for images, and sufficient color contrast.
User-Friendly Design: The interface must be easy to use and intuitive, with clear visual cues and consistent layout. A user-centered design process must be followed, with user feedback and usability testing.
Complaint Registration Form: A minimal and concise form with labeled fields for complaint description, location (map integration and address input), category selection (predefined list), and supporting document uploads. Real-time input validation with informative error messages.
Complaint Tracking Interface: A dedicated page where users can enter their tracking ID to view the current status of their complaint. Status updates must be displayed in graphical chronological timeline format.
Admin Dashboard: A secure, password-protected interface with role-based access control. The dashboard must provide an overview of key metrics and links to different management sections.
3.1.2 Hardware Interfaces:
Web Server: An efficient web server (e.g., Apache, Nginx) to handle the expected traffic load.
Database Server: A dedicated database server (PostgreSQL) to hold application data.
Email/SMS Gateway: Integration with a reliable email/SMS gateway service to send alerts.
Cloud Infrastructure: The application will be deployed on a cloud platform (AWS, Google Cloud, Azure) to take advantage of its scalability, reliability, and security capabilities.
3.1.3 Software Interfaces:
Backend Framework: PHP (Laravel) or Python (Flask) will be employed for backend coding.
Database: PostgreSQL will be employed as the relational database.
Frontend Technologies: HTML, CSS, and JavaScript (using a current framework such as React, Vue, or Angular) will be utilized for frontend development.
API: A RESTful API will be employed for the communication between frontend and backend. API documentation will be auto-generated (e.g., with Swagger).
Email/SMS Gateway API: Integration of the selected email/SMS gateway provider's API.
Map API: Integration with a map API (e.g., Google Maps, Leaflet) for geographical input on the complaint registration form.
Authentication and Authorization: Secure authentication and authorization will be used (e.g., OAuth 2.0).
3.2 Functional Requirements:

(Detailed breakdown of each function from Section 2.2)
Complaint Registration:
Capture complaint details (description, location, category, supporting documents).
Validate user input (required fields, data formats, file sizes, file types).
Generate a unique tracking ID.
Send confirmation email/SMS to the user with the tracking ID.
Store the complaint data in the database.
Complaint Tracking:
Retrieve complaint status based on the tracking ID.
Display status updates in a user-friendly format (timeline).
Allow users to configure notification preferences.
Automated Alerts:
Send email/SMS notifications at key status changes.
Allow admins to configure notification templates and triggers.
Admin Dashboard:
Secure login with role-based access control and 2FA.
Display key performance indicators (KPIs) and visualizations.
Manage complaints (view, filter, sort, assign, resolve).
Manage user accounts (CRUD operations, roles, permissions).
Generate reports (complaint statistics, performance reports).
User Management (Admin):
Create, read, update, and delete government official accounts.
Assign roles and permissions to users.
Manage user passwords (reset, password policies).
3.3 Quality of Service Requirements:

3.3.1 Performance:

Page Load Time: Maximum 2 seconds for all pages.
API Response Time: Maximum 1 second for all API requests.
Concurrent Users: The system should handle at least 1000 concurrent users without significant performance degradation.
Scalability: The system should be scalable to accommodate future growth in the number of users and complaints.
3.3.2 Security:

Authentication: Secure user authentication using industry best practices (e.g., password hashing, salting). 2FA using OTP is highly recommended.
Authorization: Role-based access control to restrict access to sensitive functionalities.
Data Encryption: Sensitive data (e.g., user passwords, personal information) should be encrypted at rest and in transit (HTTPS).
Input Validation: Thorough input validation to prevent SQL injection, cross-site scripting (XSS), and other web vulnerabilities.
Penetration Testing: Regular security audits and penetration testing to identify and address potential vulnerabilities.
OWASP Compliance: The portal will be developed in line with OWASP secure coding practices.
3.3.3 Reliability:

Uptime: 99.9% uptime.
Data Backups: Regular automated backups of the database.
Disaster Recovery: A disaster recovery plan should be in place to ensure business continuity in case of system failure.
3.3.4 Availability

The system should be available 24/7, except for scheduled maintenance.
3.4 Compliance Requirements:

Data Privacy: Compliance with GDPR, CCPA, and other relevant data privacy regulations. This includes data anonymization, data retention policies, and user consent management.
Accessibility: Compliance with WCAG 2.1 Level AA accessibility guidelines.
3.5 Design and Implementation Requirements:
(Continuing from the previous response - Section 3: Requirements)

3.5 Design and Implementation Requirements (Continued)

3.5.1 Installation

Automated Installation: The system should be easily installable and deployable, preferably using automated scripts or tools. This should include database setup, configuration, and dependency installation.
Documentation: Clear and comprehensive documentation should be provided for installation and configuration, including system requirements, dependencies, and step-by-step instructions.
3.5.2 Distribution

Cloud Deployment: The application will be deployed on a cloud platform (AWS, Google Cloud, Azure) to leverage its scalability, reliability, and security features. Containerization (e.g., Docker, Kubernetes) is recommended for easier deployment and management.
Version Control: A version control system (e.g., Git) will be used throughout the development process to track changes and facilitate collaboration.
3.5.3 Maintainability:

Code Quality: The code should be well-structured, modular, and easy to understand, following coding best practices and style guides. Code reviews should be conducted regularly.
Documentation: Comprehensive documentation, including API documentation, code comments, and user manuals, should be provided.
Logging and Monitoring: The system should include logging and monitoring capabilities to track system performance, identify errors, and facilitate debugging.
3.5.4 Reusability:

Modular Design: The system should be designed with reusable components and modules to reduce development time and improve maintainability.
API Design: A well-defined and documented API should be provided to allow integration with other systems.
3.5.5 Portability:

Platform Independence: The system should be portable across different server environments (e.g., Linux, Windows) and cloud platforms.
Database Portability: Consider using database abstraction layers to facilitate migration to different database systems if needed in the future.
3.5.6 Cost:

Cost Optimization: The system should be designed and implemented with cost optimization in mind, utilizing open-source technologies and cloud resources efficiently.
Budgeting: A detailed budget should be developed for the project, including development costs, infrastructure costs, maintenance costs, and ongoing support costs.
3.5.7 Deadline

25.8.1 The project should be completed by the specified deadline. A detailed project plan with milestones and timelines should be developed and followed.
3.5.8 Proof of Concept

Core Functionalities: A proof of concept (POC) demonstrating the core functionalities of the system (complaint registration, tracking, admin dashboard) will be developed and tested before full-scale development begins. This POC will serve to validate the technical feasibility of the proposed solution and gather feedback from stakeholders.
4. VerificationUnit Testing: The individual units and modules will be adequately tested to ensure that they are working as expected. Automated unit testing is recommended.

Integration Testing: The interfaces among different modules will be tested to ensure that they integrate properly.

System Testing: The system will be end-to-end tested to ensure that it is meeting all the specifications required.

User Acceptance Testing (UAT): The system will be tested by representative users to ensure that it is meeting their requirements and expectations. UAT has to be performed in a real-world setting.

Performance Testing: The system will be tested under different load conditions to ensure that its performance, scalability, and responsiveness are as expected.

Security Testing: Penetration testing and vulnerability scanning will be performed to identify and fix any security loopholes.

Accessibility Testing: The system will be tested to ensure that it is WCAG 2.1 Level AA accessibility guidelines compliant.
5. Appendixes

Sample Complaint Registration Form: A sample of the complaint registration form, including all fields and validation rules.
Sample Admin Dashboard Screenshots: Screenshots of the admin dashboard, showing key metrics and functionalities.
Database Schema: A diagram or description of the database schema, including tables, columns, and relationships.
API Documentation: Documentation for the RESTful API, including endpoints, request/response formats, and authentication methods. (Swagger or similar tool recommended).
User Manual: A user manual for both citizens and government officials, providing instructions on how to use the system.
Glossary of Terms: A glossary of terms used in the SRS.
