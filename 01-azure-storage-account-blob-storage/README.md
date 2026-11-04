# Lab 01 — Azure Storage Account and Blob Storage

## 1. Business Problem

Organizations need a reliable and scalable way to store and retrieve files without maintaining physical storage infrastructure.

In this lab, I explored how Microsoft Azure Blob Storage can provide cloud-based file storage while considering security, reliability, and cost.

## 2. Project Objective

My objective was to create an Azure Storage Account with a private Blob container, upload a text file, retrieve it, and verify that the downloaded contents matched the original.

## 3. Azure Resources and Configuration

| Setting | Configuration |
|---|---|
| Resource Group | rg-portfolio-dev |
| Storage Account | stportfolioaz90001 |
| Region | Sweden Central |
| Account Type | StorageV2 |
| Performance | Standard |
| Redundancy | Locally Redundant Storage (LRS) |
| Access Tier | Hot |
| Blob Container | portfolio-files |
| Container Access | Private |
| Test File | hello-azure.txt |

## 4. Implementation

1. I created a resource group to organize my Azure resources.
2. I deployed a Storage Account in Sweden Central.
3. I selected Standard performance, LRS redundancy, and the Hot access tier.
4. I created a private Blob container named portfolio-files.
5. I created a plain-text file named hello-azure.txt.
6. I uploaded the file to Azure Blob Storage using the Azure Portal.
7. I downloaded the file and compared it with the original.

## 5. Testing and Validation

I successfully uploaded and retrieved the file.

After downloading it, I opened the file locally and verified that its contents matched the original.

**Result:** The manual file upload and retrieval workflow worked successfully.

## 6. Security Considerations

- I configured a private container to prevent anonymous public access.
- Azure Storage provided encryption at rest using Microsoft-managed keys.
- Secure transfer was enabled to require HTTPS for supported REST operations.
- Blob and container soft delete were enabled with seven-day retention.
- Public network access was enabled from all networks. I recognize that additional network restrictions would be important to evaluate for sensitive production workloads.

## 7. Troubleshooting

Initially, I attempted to access the Blob container using my Microsoft Entra ID account but encountered an authorization limitation.

I switched to storage account access-key authentication and successfully completed the lab.

This helped me understand the difference between Azure resource management permissions and Blob data access permissions.

For a production-oriented improvement, I would use Microsoft Entra ID with an appropriate Azure RBAC data-plane role, such as Storage Blob Data Contributor.

## 8. Cost and Design Decisions

- **Standard performance:** Appropriate for a small learning workload.
- **LRS:** Provides local redundancy without the additional geographic protection and potential costs of higher redundancy options.
- **Hot access tier:** Suitable for files accessed frequently during testing.
- **Microsoft-managed keys:** Provide encryption at rest without requiring me to manage encryption keys.
- **Cost Management:** I explored Azure Cost Management to understand how cloud spending can be monitored.

## 9. Future Improvements

- Configure Microsoft Entra ID authentication with least-privilege RBAC.
- Evaluate firewall rules and private endpoints.
- Explore Blob versioning and additional recovery options.
- Configure budgets and cost alerts.
- Automate deployment using Azure CLI, Bicep, or Terraform.
- Review resource cleanup to avoid unnecessary ongoing charges.

## 10. Key Takeaways

This lab helped me understand how Azure Resource Groups, Storage Accounts, Blob containers, and individual blobs relate to one another.

I also gained practical experience with file upload and retrieval, access permissions, encryption, redundancy, and cost considerations.

My main takeaway is that Cloud Engineering involves more than deploying resources. It also requires understanding why configurations are chosen, validating that solutions work, and identifying improvements.

## 11. Evidence


### Azure Storage Account Overview
![Azure Storage Account Overview](screenshots/01.Storage-Accnt-Overview.png)

### Private Blob Container
![Private Blob Container](screenshots/02.Private-Container.png)

### Uploaded Blob File
![Uploaded Blob File](screenshots/03-blob-uploaded.png)

### Blob Retrieval and Validation
![Blob Retrieval and Validation](screenshots/04-blob-retrieval-validation.png)

### Microsoft Entra ID Authorization Troubleshooting
![Entra ID Blob Access Denied](screenshots/05-entra-id-blob-access-denied.png)


**Lab Status:** Completed — manual file upload and retrieval verified.
