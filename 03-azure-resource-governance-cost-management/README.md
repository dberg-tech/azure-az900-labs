
# Lab 03 — Azure Resource Governance and Cost Management

## 1. Business Problem

A growing e-commerce company has deployed its initial Azure storage and networking infrastructure.

As the environment expands, the company needs to organize its resources, reduce the risk of accidental deletion, and monitor cloud spending.

This lab explores Azure governance and cost management using the existing development resource group.

## 2. Project Objective

Apply Azure resource tags, configure a resource-group delete lock, and review accumulated costs using Azure Cost Management.

This lab builds on the storage and networking foundations established in Labs 01 and 02.


## 3. Azure Resources and Configuration

| Setting | Configuration |
|---|---|
| Resource Group | `rg-portfolio-dev` |
| Region | Sweden Central |
| Environment | Development |
| Project | CloudPortfolio |
| Workload | Ecommerce |
| ManagedBy | CloudEngineering |
| Resource Lock | `lock-portfolio-prevent-delete` |
| Lock Type | CanNotDelete (Delete) |
| Cost Management Scope | Resource Group |
| Cost Analysis Period | November 2026 |
| Budget | Existing subscription-level budget (Lab 01) |

### Resource Tags

I verified four tags on the existing Azure Resource Group:

- `Environment: Development`
- `ManagedBy: CloudEngineering`
- `Project: CloudPortfolio`
- `Workload: Ecommerce`

These tags help organize Azure resources and support governance, reporting, and cost allocation.

### Resource Protection

I configured a CanNotDelete lock at the Resource Group scope to reduce the risk of accidental deletion.

The lock prevents deletion of protected resources but does not prevent all modifications.

### Cost Monitoring

I reviewed accumulated Azure costs for November 2026 using Azure Cost Management.

The displayed actual cost was less than SEK 0.01 at the time of review, with Storage accounting for the reported usage.

A subscription-level budget was previously configured in Lab 01. No additional budget was created in Lab 03.


## 4. Implementation

### Step 1 — Configure Resource Tags

Opened the existing resource group `rg-portfolio-dev` in the Azure Portal and reviewed its tags.

Verified the following tags:

- Environment: Development
- ManagedBy: CloudEngineering
- Project: CloudPortfolio
- Workload: Ecommerce

These tags provide consistent resource classification and support governance and cost reporting.

### Step 2 — Configure a Resource Lock

Navigated to Resource Group > Settings > Locks.

Configured a resource-group-level lock:

- Lock name: `lock-portfolio-prevent-delete`
- Lock type: CanNotDelete (Delete)
- Scope: `rg-portfolio-dev`

Verified that the lock appeared in the Azure Portal.

### Step 3 — Review Azure Cost Analysis

Navigated to Resource Group > Cost Management > Cost analysis.

Reviewed accumulated costs for November 2026.

The Azure Portal displayed an actual cost below SEK 0.01, primarily associated with Azure Storage.

The existing subscription-level budget was configured in Lab 01, so no additional budget was created.


## 5. Governance and Security Decisions

### Why use resource tags?

Tags help identify and organize Azure resources by environment, project, workload, and management responsibility.

They support resource tracking, cost analysis, and operational governance.

### Why configure a CanNotDelete lock?

A CanNotDelete lock reduces the risk of accidentally deleting important Azure resources.

Because the lock is applied at the Resource Group level, it also protects resources within that group from deletion.

However, this lock does not prevent all configuration changes and is not a replacement for Azure RBAC.

### Why review costs at the Resource Group level?

Resource Group cost analysis helps identify spending associated with a particular environment or project.

In this lab, the accumulated cost was below SEK 0.01 at the time of review.

The existing subscription-level budget from Lab 01 provides a separate cost-monitoring control.

### Operational Considerations

- Resource tags do not automatically enforce security policies.
- Resource locks do not control who can access resource data.
- Azure RBAC is used to manage permissions.
- A CanNotDelete lock must be removed by an authorized user before deleting protected resources.
- Azure costs should be reviewed regularly because consumption and pricing can change.


## 6. Validation Evidence

The following screenshots demonstrate the Azure governance configurations and cost analysis completed in this lab.

### 1. Resource Group Tags

Verified four tags applied to `rg-portfolio-dev` for resource organization and governance.

![Azure Resource Group tags](screenshots/01-resource-group-tags.png)

### 2. Resource Group Delete Lock

Verified that the `CanNotDelete` lock was configured at the Resource Group level.

![Azure Resource Group delete lock](screenshots/02-resource-group-delete-lock.png)

### 3. Azure Cost Analysis

Reviewed accumulated costs for November 2026 at the Resource Group scope.

At the time of review, the reported cost was below SEK 0.01, primarily associated with Azure Storage.

![Azure Resource Group cost analysis](screenshots/03-resource-group-cost-analysis.png)


## 7. Key Learnings

Through this lab, I gained practical experience with Azure resource governance and cost management.

- **Resource Organization:** Learned how Azure tags classify resources by environment, project, workload, and management responsibility.
- **Resource Protection:** Configured a CanNotDelete lock to reduce the risk of accidental deletion of resources within a Resource Group.
- **Governance vs. Security:** Understood that tags organize resources and locks protect against deletion, but neither replaces Azure RBAC or security policies.
- **Cost Visibility:** Used Azure Cost Management to review accumulated spending at the Resource Group level and identify which services generated costs.
- **Budget Scope:** Understood the distinction between subscription-level budgets and Resource Group cost analysis. An existing subscription-level budget was configured in Lab 01.
- **Operational Responsibility:** Learned that resource locks must be considered during cleanup and that cloud spending requires ongoing monitoring.

### Cloud Engineering Takeaway

Deploying cloud resources is only part of a Cloud Engineer's responsibility.

A well-managed Azure environment also requires consistent resource organization, protection against accidental changes, cost visibility, and appropriate access controls.

This lab introduced foundational governance practices that can be expanded through Azure Policy, RBAC, Infrastructure as Code, and automated cost monitoring in future projects.


## 8. Connection to Previous Labs and Future Development

This lab is part of a progressive Azure Cloud Engineering portfolio based on a simulated e-commerce environment.

### Lab 01 — Azure Storage Foundation

Deployed an Azure Storage Account and Blob Container to explore cloud storage, data access, and authorization.

Investigated an HTTP 403 authorization error and resolved it by assigning the appropriate Azure RBAC role.

Also explored Azure Cost Management and configured a subscription-level budget.

### Lab 02 — Azure Networking Foundation

Created an Azure Virtual Network with two subnets:

- `snet-app-dev` — for future application workloads.
- `snet-private-endpoints-dev` — for future private connections to Azure services.

Learned how to plan private IPv4 address ranges and distinguish network segmentation from actual traffic isolation.

### Lab 03 — Azure Governance and Cost Management

Extended the existing Azure environment by:

- Applying consistent Resource Group tags.
- Configuring a CanNotDelete resource lock.
- Reviewing accumulated costs at the Resource Group level.
- Understanding the difference between resource organization, protection, and access control.

All three labs use the existing development Resource Group, `rg-portfolio-dev`.

### Future Development

The next stages of this portfolio will explore:

- Network Security Groups and traffic filtering.
- Private connectivity between Azure services.
- Azure identity and access management.
- Infrastructure as Code using Bicep and Terraform.
- Monitoring, alerting, and deployment automation.

The long-term goal is to develop this environment into a more secure, maintainable, and automated Azure infrastructure project.

### Previous Labs

- [Lab 01 — Azure Storage Account and Blob Storage](../01-azure-storage-account-blob-storage/README.md)
- [Lab 02 — Azure Virtual Network and Subnets](../02-azure-virtual-network-subnets/README.md)

---

**Lab Status:** Completed and verified  
**Certification Track:** Microsoft Azure Fundamentals (AZ-900)
