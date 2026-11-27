
# Lab 04 — Enterprise Identity, RBAC & Least Privilege

**Status:** In progress  
**Learning path:** AZ-104 — Microsoft Azure Administrator  
**Focus:** Cloud Engineering & Cloud Security

## 1. Business Scenario

A simulated e-commerce company with 50 employees is expanding its cloud infrastructure on Microsoft Azure.

The organization consists of four departments:

| Department | Employees |
|---|---:|
| IT Operations | 5 |
| Development | 15 |
| Finance | 5 |
| Customer Service | 25 |

The company occasionally hires external contractors and plans to operate three environments:

- DEV — Development
- TEST — Testing and validation
- PROD — Production

The organization must prepare its identity and access management architecture to support potential growth from 50 to 500 employees.

## 2. Problem Statement

Management has identified several security and operational challenges:

- Excessive employee permissions.
- Inconsistent individual access assignments.
- Risk of unauthorized production infrastructure changes.
- Risk of former employees retaining access.
- Lack of standardized onboarding and offboarding processes.
- Increasing administrative workload.
- Risk of compromised employee accounts.

The current access management approach is not sufficiently secure or scalable to support future business growth.

## 3. Engineering Assignment

Acting as the Cloud Engineer with security responsibilities in this simulated enterprise, my assignment is to design, implement and validate a centralized identity and access management solution using Microsoft Entra ID and Azure Role-Based Access Control (RBAC).

The solution must balance security, operational efficiency, scalability, administrative complexity and cost.

## 4. Business and Security Requirements

- Implement group-based access control.
- Enforce the principle of least privilege.
- Restrict developers' infrastructure management access to DEV.
- Allow IT Operations to manage approved infrastructure across DEV, TEST and PROD.
- Provide Finance with subscription-wide cost visibility.
- Separate application access from infrastructure management access.
- Support future workforce growth.
- Establish a foundation for automated identity lifecycle management.
- Validate authorized and unauthorized access.

## 5. Expected Outcome

A secure, scalable and manageable identity architecture that reduces excessive privileges, minimizes the potential blast radius of compromised accounts and supports future automation.

---

> This project is a simulated enterprise scenario for hands-on Azure administration, cloud engineering and cloud security practice. Implementation and validation results will be documented as the lab progresses.

