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
![image](https://github.com/user-attachments/assets/d8356651-60eb-4bdd-8c6b-53a0988e3333)

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

**Support Request Contributor**

Read roles and role assignments -- **Microsoft.Authorization/*/read**

Create and update a support ticket -- **Microsoft.Support/***

Gets or lists resource groups. -- **Microsoft.Resources/subscriptions/resourceGroups/read**

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

**Storage Account Contributer** permits management of Storage accounts.

**Storage Blob Data Owner** provides full access - read, write, and delete permissions to Azure Storage blob containers and data, including assigning POSIX access control. 

**Storage Blob Data Contributor** - Read, write, and delete Azure Storage containers and blobs.

Only the **BLOB storage** service is supported with the Export job feature. 

For import job feature **Azure Blob storage** and **Azure File storage** is supported.

In order to ensure that traffic is routed via the intrusion-based device, you need to setup a **route table** and add the route table to the subnets in the other virtual networks.

**Azure policies** are used from a governance perspective.

Use **resource tags** to organize your Azure resources and also apply billing techniques department wise.

**Azure role-based access control** is used to control access to resources.

Create alerts based on **Activity Logs in Azure Monitor**.

**Azure Advisor** service is used as a recommendations engine.

**Service Health service** is used to inform users on the health of all Azure based services.

**Azure Locks**

Resource Lock Analysis

1. Resource Group “skillcertlabs-rg1”:
   - Contains three resources:
     - skillcertlabstore2090: Has a Delete lock (skillcertlablock2).
     - skillcertlabnetwork: Has a Read-only lock (skillcertlablock3).
     - skillcertlabip: No lock.
2. Resource Group “skillcertlabs-rg2”:
   - Has a Delete lock (skillcertlabock1).

Moving Resources in Azure

In Azure, when moving resources between resource groups, the following rules apply regarding locks:

- If the destination resource group has a Delete lock, it prevents any resources from being deleted from that group. However, it does not prevent moving resources into it.
- If the source resource group has a Read-only lock on any of its resources, that might restrict modifications, including moving resources out of the group.
- The presence of a Read-only lock on “skillcertlabnetwork” means that modifications to this resource are restricted, which could prevent moving it to another resource group.

Given the above analysis, you **cannot** move the resource “skillcertlabnetwork” from “skillcertlabs-rg1” to “skillcertlabs-rg2” because:
- The resource “skillcertlabnetwork” has a Read-only lock applied to it, which restricts modifications to the resource.
- Moving a resource to another resource group is considered a modification operation, and the Read-only lock on “skillcertlabnetwork” prevents this action.

If user has the **Global Administrator** role and has created the new directory, the user would have the required permissions to create new users in the directory.

Solution:

There are two possible solutions:

1. **Skillcertlabusr1 grants access**: Skillcertlabusr1, who created the new tenant, has the necessary permissions. They can grant Global Administrator or User Administrator roles to skillcertlabusr2 **within the new tenant**.
2. **Use Azure AD B2C**: If the company wants external users in the new tenant, consider using Azure AD B2C, which allows self-service signup or social logins.

While skillcertlabusr2 has Global Administrator privileges in the original tenant (skillcertlabs.onmicrosoft.com), those privileges **don’t extend** to the newly created tenant (staging.skillcertlabs.onmicrosoft.com).

If the user is **User Administrator** then he would have permission for current directory (skillcertlabs.onmicrosoft.com) only. In order to add users to the new directory, the main user needs to be given the required Global Admin role in the new directory.

Network interface needs to be created in the **same region** as the virtual network. When you create a virtual network, an important aspect is to ensure you set the virtual network for the network interface.

Backup policy types available in Azure Backup
- Azure VM
- Azure File Share
- SQL Server in Azure VM
- SAP HANA in Azure VM

So, we can have on policy for the **Azure virtual machines** and one for **Azure file shares**. The Azure SQL Databases have a separate backup mechanism via **automated backups**.

Once you add a server as a server endpoint with a particular file path, you **can’t add** the server as another endpoint with another path.

Azure subscription that contains a Log Analytics workspace named stagingworkspace. You have to get the error events from the table named Event.

**search in (Event) “error”**

If the user state is in the **Enforced state**, then the user will **need to use MFA for the login process**.

**Floating IP** is used when you have multiple front-end IP’s.

**Health Probe**  is used to check the health of the back end VM’s.

**TCP Reset** is used for idle timeout.

**Cost Analysis section for the subscription** allows you to see all the costs.

A **data collector set** if used to collect data for Performance counters.

**Network Watcher variable packet capture** allows you to create packet capture sessions to track traffic to and from a virtual machine. Packet capture helps to diagnose network anomalies both reactively and proactivity. Other uses include gathering network statistics, gaining information on network intrusions, to debug client-server communications and much more.

**Azure AD roles** are specifically meant to control access to Azure AD.

Move Azure resources across subscriptions using the **Move-AzResource** powershell command. 

For achieving high availability, you need to use **Availability sets**.
**Availability set** for multiple VMs
- Provide a Service Level Agreement (SLA) of 99.95 percent availability.
- Use managed disks.

**Azure Traffic manager** is used for traffic distribution based on DNS queries.

**Owner** has permission to assign read role to user.
**Network Contributor** does not have access to assign read roles. And if you look at the **Security admin role** , it only has the privilege to work with Security Center.

The local VPN gateway is used when you want to define **site-to-site VPN connections**.

Users can connect to file share from their home computers using **port 445**.

**Role based access policies** can be used to restrict access to resources, but they can put any sort of governance on what type of resources to create.

Want to ensure that only Virtual Machines of a particular SKU size can be launched in their Azure account. This can be done with **Azure policies**.

Which of the following network watcher feature would you use for the following requirement?
“Find out if a network security rule is preventing a network packet from reaching a virtual machine hosted in an Azure virtual network”
This can be done with the **IP Flow Verify feature**. It checks if a packet is allowed or denied to or from VM.

**Next Hop** is used to get the next hop type and IP address of a packet from a specific VM.

**Packet Capture** is used for deep dive network packet capture.

**Traffic Analysis** is a cloud-based solution that provides visibility into user and application activity in cloud networks.

You can achieve 99.99% SLA on the infrastructure level for your virtual machines by **deploying them across availability zones**.

**Availability sets** can only guarantee an SLA of 99.95%

In load balancers, virtual machines need to be part of a **single virtual network**.
![image](https://github.com/user-attachments/assets/bb94a13b-4ef6-4f74-9349-0bc597da0c0b)

When transferring data to an Azure storage account, you can transfer data to **Azure blob storage** or **Azure file storage**.

For administrators, the password reset policy is different wherein **they are not asked for security questions**.

Scale sets are used to **scale the Virtual machines based on load**. But here to achieve the desired level of availability, you also need to use an **Availability set**. You can use availability sets along with scale sets to achieve high availability.





