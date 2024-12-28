Azure File Sync
- Use as file distribution service

**Add-AzStorageAccountNetworkRule** is used to add an IP address or an IP address range to have access to the storage account.

Premium SSD has the capability to support an **IOPS up to 20,000**.

If you **enable collection of guest OS diagnostics data**, you will have the ability to collect data on the performance counters on Windows based virtual machines.

The **local VPN gateway** is used when you want to define site-to-site VPN connections.

Use the secrets feature in **Azure Key vault** for storing passwords.

In order to ensure that secrets from Azure Key vault can be accessed you need to ensure you set the **access policies** accordingly.

In order to ensure the client IP is requested by the same back end virtual machine, you need to **enable Session Persistence and set it to Client IP**.

UNC path URL format for Azure file share
![alt text](<Screenshot from 2024-12-28 13-34-00.png>)

**Azure locks** are used to prevent users from accidentally deleting or modifying critical resources.

**Connection Monitor** is designed to actively monitor network connectivity between two endpoints, including Azure virtual machines and external hosts. It can help identify network issues, latency, and packet loss.

By default, the virtual network which is registered as the registration network for a private hosted zone, also automatically becomes a **resolution network** as well. Hence the virtual machines hosted in this network would be able to **resolve the host names**.

Since we need to distribute traffic across the virtual machines, we can use either the **Load Balancer** or **Application Gateway service**.

Use **Azure Advisor** to provide insights into looking at the prospect of reduction of costs.

**Azure Monitor** is primarily a monitoring tool that woks on metrics and diagnostics logs.

The location of the resource would **remain** as it is. It’s only the resource group that changes.

**Managed Identity** is the most secure and recommended approach to grant access to Azure resources without using secrets like access keys or connection strings.

Deploy the virtual machines across **multiple** availability zones.

For an Azure Web App, you need to have an **Azure App Service Plan** in place. To minimize costs, you can have a **single** App Service Plan and link all the Azure Web Apps to that App Service Plan.

Resource group-level policies typically take **precedence** over subscription-level policies when there’s a direct conflict.

**Storage File Data SMB Share Reader** RBAC role allows read access in Azure Storage file shares over SMB.

**Storage File Data SMB Share Contributor** RBAC role allows read, write and delete access in Azure Storage file shares over SMB.

**Storage File Data SMB Share Elevated Contributor** RBAC role allows read, write, delete and modify NTFS permissions in Azure Storage file shares over SMB.

**Cloud-init** is a widely used approach to customize a Linux VM as it boots for the first time. You can use cloud-init to install packages and write files, or to configure users and security. As cloud-init runs during the initial boot process, there are no additional steps or required agents to apply your configuration.

The **cloud tiering feature** is used to ensure volumes have a percentage of free space when you use the Azure File Sync service.

Support Request Contributor
Read roles and role assignments -- Microsoft.Authorization/*/read
Create and update a support ticket -- Microsoft.Support/*
Gets or lists resource groups. -- Microsoft.Resources/subscriptions/resourceGroups/read