
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
