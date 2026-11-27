
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


## 6. Proposed Architecture and Engineering Decisions

### 6.1 Architecture Overview

The proposed architecture uses Microsoft Entra ID for centralized identity management and Azure Role-Based Access Control (RBAC) for infrastructure authorization.

Employees will be organized into security groups according to their responsibilities. Azure RBAC roles will be assigned to these groups at appropriate scopes.

The architecture separates development, testing and production environments to support security, operational control and future scalability.

### 6.2 RBAC Access Control Matrix

| Security Group | Azure RBAC Role | Assignment Scope |
|---|---|---|
| sg-it-ops | Contributor | DEV, TEST and PROD resource groups individually |
| sg-dev | Contributor | DEV resource group |
| sg-finance | Cost Management Reader | Subscription |
| sg-support | No Azure RBAC role | Not applicable |

### 6.3 Group-Based Access Control

Group-based access control was selected instead of individual role assignments to simplify identity management and reduce administrative overhead.

As the company grows from 50 to potentially 500 employees, managing permissions individually would increase complexity, inconsistent access assignments and the risk of human error.

Assigning permissions through security groups provides a more consistent and scalable approach while establishing a foundation for automated onboarding and offboarding.

### 6.4 IT Operations — Resource Group Scope

IT Operations requires Contributor access across DEV, TEST and PROD to perform infrastructure management responsibilities.

Resource group-level assignments were selected instead of subscription-level Contributor access to limit permissions to approved environments.

This reduces the potential blast radius of compromised accounts and prevents automatic access to newly created resource groups through these assignments.

The trade-off is that multiple role assignments must be maintained.

### 6.5 Developers — Development Environment Isolation

Developers require Contributor access to the DEV environment to perform their assigned responsibilities.

Restricting infrastructure management permissions to DEV follows the principle of least privilege and reduces the risk of accidental or unauthorized changes to production infrastructure.

In a production environment, more granular roles and approved CI/CD deployment identities could further reduce excessive privileges.

### 6.6 Finance — Cost Management Access

The Cost Management Reader role was selected because Finance requires visibility into Azure spending rather than infrastructure management permissions.

Subscription-level scope allows Finance to monitor costs across DEV, TEST and PROD, subject to the applicable billing configuration.

This demonstrates that least privilege requires both an appropriate role and a scope aligned with business requirements.

### 6.7 Customer Service — Application-Level Access

Customer Service does not require Azure RBAC permissions because its responsibilities involve using the company's business application rather than managing cloud infrastructure.

Application-level authorization should be managed separately according to business responsibilities.

This separation reduces unnecessary infrastructure privileges and limits the potential impact of compromised user accounts.

### 6.8 Design Limitations and Trade-offs

- Resource group-level role assignments require more administration than a single subscription-level assignment.
- Security group membership must be regularly reviewed to prevent privilege accumulation.
- Contributor permissions may be broader than necessary for certain responsibilities.
- Resource group separation alone does not provide network isolation.
- Advanced identity security and automation capabilities may require additional Microsoft Entra licensing.

These limitations will be considered during implementation, validation and future architecture improvements.

**Architecture status:** Designed and reviewed. Implementation and security validation are pending.
