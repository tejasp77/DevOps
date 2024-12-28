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

To backup any resource in Azure, the first thing you need to do is to create a **Recovery Services vault**

**Azure Active Directory (Azure AD) Pass-through Authentication** allows your users to sign in to both on-premises and cloud-based applications by using the same passwords. Pass-through Authentication signs users in by validating their passwords directly against on-premises Active Directory.


If you Redeploy the VM, it will be allocated to a **different hardware cluster**. This will ensure that VM1 is not affected by the maintenance.
If you go to the Redeploy blade of your Virtual Machine, you can see the ability to relocate the VM on a **different host.**


The Capture option is used to **create an image out of the VM**. You need to deploy the VM again or shutdown and start the VM again.

One of the key requirements of peering is that the Virtual Networks **should not have overlapping IP address ranges**.

Service endpoint is used to connect Virtual networks to **other Azure services**.

Gateway subnet used for **virtual gateway connections**.

In order to back up a VM, you have to first create a **recovery services vault**. **Backup policy** used to configure the backup rule.

For the On-premise Active Directory, the user needs to have **Enterprise Admin privileges**. 

Perform Interactive queries using **Azure Log Analytics Workspace**.

**Azure Event Grid** is used for Event Hub.

To collect data about IP addresses connecting to the Load Balancer, you need to enable diagnostics on the **Load Balancer** itself. This will capture network flow logs, which contain information about incoming and outgoing traffic. 
By enabling diagnostics on the Load Balancer, you can analyze the network flow logs to identify the IP addresses that are connecting to it. You can then export these logs to a storage account and use Azure Data Explorer or other analytics tools to run interactive queries on the data.

**Logic App Contributer** role has the permissions for managing Logic App resources. For eg. to create Logic app.

**Logic App Operator** role only has permissions to read, enable and disable Logic Apps , but not create any Logic Apps.

**DevTest Labs User** role only has permissions to work with DevTest labs, lets you to connect, start, restart, shutdown your VMs in DevTests Labs and not Logic Apps.

**NSG Flow Logs** is used to check the flow logs for the allow and deny traffic.

**Connection Troubleshoot** is used to test a connection at a point in time, rather than monitor the connection over time.

**IP Flow Verify** is used to verify the flow of traffic.

**Connection monitor** also provides the minimum, average, and maximum latency observed over time. After learning the latency for a connection, you may find that you’re able to decrease the latency by moving your Azure resources to different Azure regions. 