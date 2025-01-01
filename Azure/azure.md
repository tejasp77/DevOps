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
**Advisor** helps you optimize and reduce your overall Azure spend by identifying idle and underutilized resources. You can get cost recommendations from the Cost tab on the Advisor dashboard.

**Azure Monitor** is primarily a monitoring tool that woks on metrics and diagnostics logs. Azure Monitor is a solution for collecting, analyzing and acting on telemetry data from resources.

**Metrics** provide usage statistics like CPU, memory usage.

**Customer insights**  This connects to various sources and provides all customer information at one place.

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

**Azure Traffic manager** is load balancer and used for traffic distribution based on DNS queries.

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

Here’s an important point to remember regarding Azure Policy:

Azure policy assignment scope works in a **top-down manner**. A policy assigned to a higher level scope (like Tenant Root) will **override** policies assigned to lower levels (like specific resource groups).
Therefore, despite the resource group existing, the Azure policy will block the creation of a virtual network within it.

Using Azure Backup option, the virtual machine has to be in the **Stopped** or Deallocated state in order to replace the existing disks on the virtual machine.

Azure policies would only highlight the compliance of existing resource and enforce the policy restrictions on **new resources**.

Since there is only a delete lock on the target resource group, we can still change or **move** the resource to the target resource group.

Both virtual machines are in the same virtual network, so they **can communicate** with each other directly.

Both resource groups are within the same subscription (“skillcertlab-staging”), the Read-Only lock on “skillcertlabs-rg2” **restricts** adding new resources like the web application.

since the lock type is a Delete lock, resources can still be **added** or **updated** in the resource group. Hence the Azure Web app can be moved to this resource group.
Remember – You can move resources across subscriptions. Also remember that the resource group could be located in a different region from the resource itself.

To protect the web servers against SQL injection attacks, one can make use of the **Web Application Firewall** feature.

**Azure AD Join**: When a user joins a device to Azure AD, they are automatically added to the local Administrators group on that device. This gives them the necessary permissions to manage the device.
**Global Administrator**: The Global Administrator role has the highest level of permissions in Azure AD and can manage all aspects of the tenant. This includes the ability to join devices to Azure AD and add users to the local Administrators group.
**Cloud Device Administrator**: The Cloud Device Administrator role has permissions to manage devices in Azure AD, but they cannot directly add users to the local Administrators group on those devices.
**Intune Administrator**: The Intune Administrator role has permissions to manage Intune policies and settings, but they cannot directly add users to the local Administrators group on devices.
Therefore, when skillcertlabusr1 joins a Windows 10 computer to the Azure AD tenant, both skillcertlabusr1 (the user who joined the device) and skillcertlabusr2 (the Global Administrator) will be added to the local Administrators group on the computer.

If you have a duplicate file on the file share and the file server, the file on the file server will have **its name appended with the name of the server**

For administrators, the password reset policy is different wherein **they are not asked for security questions**.

The **Fraud alert** feature lets users report fraudulent attempts to access their resources. When an unknown and suspicious MFA prompt is received, users can report the fraud attempt by using the Microsoft Authenticator app or through their phone.

**Automatically block users who report fraud**. If a user reports fraud, the Microsoft Entra multifactor authentication attempts for the user account are blocked for 90 days or until an administrator unblocks the account. An administrator can review sign-ins by using the sign-in report, and take appropriate action to prevent future fraud. An administrator can then unblock the user's account.

You can actually create alerts **in Azure Monitor based on the events recorded in the Log Analytics workspace**.
You actually have to record the events in a Log Analytics workspace. And then configure alerts in Azure monitor based on the Azure Log Analytics workspace.

skillcertlabapp1 – Be able to see if users are progressing through the entire business process for the application.
In App Insights **Funnels** - Discover how customers use your application.
**Funnels** - Understand how users progress through a series of steps in your application and where they might be dropping off.

skillcertlabapp2 – Here one should be able to analyse the load times and other properties that could influence conversion rates for the application
**Impact Analysis** - Analyze how application performance metrics, like load times, influence user experience and behavior, to help you to prioritize improvements.

skillcertlabapp3 – Here one should be able to analyse how many users return to the application.
The Application Insights **retention** feature provides valuable insights into user engagement by tracking the frequency and patterns of users returning to your app and their interactions with specific features.

skillcertlabapp4 – Here one should be able to see the places where users repeat the same action over and over again.
The **User Flows** tool visualizes how users move between the pages and features of your site. It's great for answering questions like:
- How do users move away from a page on your site?
- What do users select on a page on your site?
- Where are the places that users churn most from your site?
- **Are there places where users repeat the same action over and over?**

Here you have to ensure that the **client certificate is installed on every client computer** that needs to establish a Point-to-Site VPN connection to the Azure virtual network.

The backup and restore option is available with the **Standard App Service Plan**.

You can assign Azure Policy to a **management group**, **subscription** or **resource group**.

self-service password reset (SSPR)
Email addresses – only used for SSPR
Security questions – only used for SSPR
App passwords – Can be used as primary authentication method for legacy apps, but cannot be used for both MFA & SSPR

**SMS-based** and **The Authenticator app** - MFA and SSPR

AzCopy is a command-line utility that you can use to copy **blobs** or **files** to or from a storage account.

**Azure file shares** can be used as **persistent volumes** for stateful containers.
**Azure Blob storage** –  Blob storage is optimized for storing massive amounts of unstructured data.
**Azure Queue storage** – Queue storage is for storing messages in distributed applications.
**Azure Table storage** – Table storage is for storing semi-structured data.

Availabilty Set
An update domain is a **group of VMs** and underlying physical hardware that can be rebooted at the same time.
VMs in the same fault domain share common storage as well as a common power source and network switch.
Microsoft updates, which Microsoft refers to as planned maintenance events, sometimes require that VMs be rebooted to complete the update. To reduce the impact on VMs, the **Azure fabric** is divided into update domains to ensure that not all VMs are rebooted at the same time.

To create a vault to protect any data source, the vault must be in the **same region** as the data source. Storage account must be in the **same region** as your Recovery Service Vault.

The location and subscription where this Log Analytics workspace can be created is **independent** of the location and subscription where your vaults exist.

The azcopy copy command copies a directory (and all of the files in that directory) to a blob container. The result is a directory in the container by the same name.
Syntax is : **azcopy copy ” ‘https://..core.windows.net/’ –recursive**
Append the –recursive flag to upload files in all subdirectories.
AzCopy **does not support** copying data to Table & Queue.

When you create a virtual machine (VM). You need to provide the VM administrator username and password. Instead of providing the password, you can pre-store the password in an **Azure key vault** and then customize the template to retrieve the password from the **key vault** during the deployment.

**Azure AD Identity protection** is to detect and investigate identity based risks.

**Automation account** is to automate azure management tasks.

When you define a virtual machine scale set with an Azure template, the Microsoft.Compute/virtualMachineScaleSets resource provider can include a section on **extensions**. The **extensionsProfile** details what is applied to the VM instances in a scale set. To use the Custom Script Extension, you specify a publisher of Microsoft.Azure.**Extensions** and a type of **CustomScript**.
The Custom Script Extension downloads and executes scripts on Azure VMs.

To add custom domain name to webapp
First purchase a domain name, and make sure you have access to the DNS registry for your domain provider. Then you can map the custom domain to your Azure web app. To add a custom domain to your app, you need to verify your ownership of the domain by adding a verification ID as a TXT record with your domain provider.

You must create an **app service plan** before deploying web apps. **One app service plan** can have multiple web apps. To reduce the costs, create **one app service** and use it for 10 web apps.

After you create a virtual machine (VM), you can scale the VM up or down by changing the VM size. In some cases, you must deallocate the VM first. This can happen if the new size is not available on the hardware cluster that is currently hosting the VM. If the virtual machine is currently running, changing its size will cause it to be **restarted**.

Resource lock is used to **avoid accidental deletion of Azure resources**.

You can create a **custom azure policy** to block port 8080. Azure policy enables you to establish conventions for resources in your subscription by describing when the policy is enforced and what effect to take.

You need to view the average round-trip time (RTT) of the packets from VM1 to VM2.
Azure Network Watcher feature - **Connection Monitor** provides you RTT values on a per-minute granularity. The connection monitor capability monitors communication at a regular interval and informs you of reachability, latency, and network topology changes between the VM and the endpoint.

**IP flow verify** — IP flow verify checks if a packet is allowed or denied to or from a virtual machine.
Connection troubleshoot — Enable you to troubleshoot network performance and connectivity issues in Azure
**NSG flow logs** — allows you to log information about IP traffic flowing through an NSG.

A Site-to-Site **VPN gateway** connection can be used to connect your on-premises network to an Azure virtual network over an IPsec/IKE (IKEv1 or IKEv2) VPN tunnel.
This type of connection requires a VPN device, a **VPN gateway**, located on-premises that has an externally facing public IP address assigned to it.

**Azure Application Gateway** is a web traffic load balancer. It does not provide connectivity to on-premise resources.

**Azure Active Directory’s Application Proxy** provides secure remote access to on-premises web applications. It does not provide connectivity to on-premise file shares.

There are five VMs. So, **five** NICs
The rules are same for all VMs, so **one** NSG.

Clients using Windows can access directly peered VNets, but the **VPN client must be downloaded** again if any changes are made to VNet peering or the network topology. Non-Windows clients can access directly peered VNets.

**Gateway Transit** is a VNet Peering property that enables one virtual network to use the VPN gateway in the peered virtual network for cross-premises connectivity.

**BGP** is for dynamic routing.

You can’t add address ranges to, or delete address ranges from a virtual network’s address space once a virtual network is peered with another virtual network.
To add or remove address ranges, **delete the peering, add or remove the address ranges, then re-create the peering**.

Port forwarding lets you connect to virtual machines (VMs) in an Azure virtual network by using an Azure Load Balancer public IP address and port number. To set up port forwarding on an Azure Load Balancer, you must create **inbound NAT port-forwarding rules**.

**Frontend IP configuration** allows you to configure a public IP address for the load balancer.

**A load balancer rule** is used to define how incoming traffic is distributed to the all the instances within the backend pool.

You have an on-premises network that you plan to connect to Azure by using a site-so-site VPN.
In Azure, you have an Azure virtual network named VNet1 that uses an address space of 10.0.0.0/16 VNet1 contains a subnet named Subnet1 that uses an address space of 10.0.0.0/24.
You need to create a site-to-site VPN to Azure.
Which four actions should you perform in sequence?
**Create a gateway subnet Create a VPN gateway Create a local gateway Create a VPN Connection**
Virtual network already exists. So, we need to continue the steps from creating a gateway subnet.

In Web app, **Web server logging** – Raw **HTTP request** data in the W3C extended log file format. Each log message includes data such as the HTTP method, resource URI, client IP, client port, user agent, response code, and so on.
**Application logging** is for Logs messages generated by your application code.

In Azure Monitor
**Workbooks** are for creating visual reports.
Workbooks provide a flexible canvas for data analysis and the creation of rich **visual reports** within the Azure portal. They allow you to tap into multiple data sources from across Azure, and combine them into unified interactive experiences.
Workbooks are currently compatible with the following data sources:
- Logs
- Metrics
- **Azure Resource Graph**
- Alerts (Preview)
- Workload Health
- Azure Resource Health
- Azure Data Explorer

In Azure Monitor **Service health alerts** are to get up to date information and alerts on Azure issues like service outages and planned maintenances.

**A Recovery Services vault** is a storage entity in Azure that houses data. The data is typically copies of data, or configuration information for virtual machines (VMs), workloads, servers, or workstations. You can use Recovery Services vaults to hold backup data for various Azure services such as IaaS VMs (Linux or Windows) and Azure SQL databases.
When you create an Azure Backup for virtual machines, you need to either create a **Recovery services vault** or select an existing Recovery services vault.

**Azure Storage Explorer** is a free tool from Microsoft that allows you to work with Azure Storage data on Windows, macOS, and Linux. You can use it to upload and download data from Azure blob storage.

**SMB (Server Messgae Block)** is a network file sharing protocol that allows applications to read and write files, and request services from server programs. It can be used on top of other network protocols, such as TCP/IP.

Run **Set-AzMarketplaceTerms** to accept the legal terms. Accept or reject terms for a given publisher id(Publisher), offer id(Product) and plan id(Name).
Please use **Get-AzMarketplaceTerms** to get the agreement terms.

From Azure PowerShell, run the **Set-AzApiManagementSubscription** cmdlet  This command sets the existing subscription details.

From the Azure portal, register the Microsoft.Marketplace resource provider  This **registers Microsoft.Marketplace resource provider in the subscription**.

To assign a role to a user –
1. Sign in to the Azure portal with an account that’s a global admin or privileged role admin for the directory.
2. Select Azure Active Directory, select Users, and then select a specific user from the list.
3. For the selected user, select **Directory role,** select **Add role**, and then pick the appropriate admin roles from the Directory roles list, such as Conditional access administrator.
4. Press Select to save.

From the Licenses blade, assign a new license  This steps **adds a license to the user**, not a role

From the Groups blade, invite the user account to a new group  This step **add users to a group**, not a role.

In the Azure portal, you can manage the device administrator role on the Devices page. To open the Devices page:
1. Sign in to your Azure portal as a global administrator.
2. Search for and select Azure Active Directory.
3. In the Manage section, click Devices.
4. On the Devices page, click **Device settings**.
To modify the device administrator role, configure Additional local administrators on Azure AD joined devices.

You can’t delete a Recovery Services vault with any of the following dependencies:
-  You can’t delete a vault that contains protected data sources (for example, IaaS VMs, **SQL databases**, Azure file shares).
- You can’t delete a vault that contains backup data. Once backup data is deleted, it will go into the soft deleted state.
- You can’t delete a vault that contains backup data in the soft deleted state.
- You can’t delete a vault that has registered storage accounts.

Therefore, resource group deletion will fail. You must **stop the backup** before initiating a delete.

Moving the web app **does not have an impact** on app service plan. The app service plan will **remain** in its source location or resource group. Since web app is moved to a different resource group, the policies in the target resource group will be **applied**.

**Network Performance Monitor** is a cloud-based hybrid network monitoring solution that helps you monitor network performance between various points in your network infrastructure. It also helps you monitor network connectivity to service and application endpoints and monitor the performance of Azure ExpressRoute.
You can monitor network connectivity across **cloud deployments** and **on-premises locations**, multiple data centers, and branch offices and mission-critical multitier applications or microservices. With Performance Monitor, you can detect network issues before users complain.

**Service Map**— Service Map automatically discovers application components on Windows and Linux systems
**Connection troubleshoot** — enable you to troubleshoot network performance and connectivity issues in Azure
**Effective routes** You can use effective routes to determine why you can’t connect to the VM.

From Metrics, create a chart  **Metrics** provide usage metrics like CPU, Memory usage etc..

Each NIC attached to a VM must exist in the **same location** and subscription as the VM. Each NIC must be connected to a VNet that exists in the **same Azure location** and subscription as the NIC.

**IT Service Management Connector (ITSMC)** allows you to connect Azure to a supported IT Service Management (ITSM) product or service.
Azure services like Azure Log Analytics and Azure Monitor provide tools to detect, analyze, and troubleshoot problems with your Azure and non-Azure resources. But the work items related to an issue typically reside in an ITSM product or service. ITSMC provides a bi-directional connection between Azure and ITSM tools to help you resolve issues faster.
ITSMC supports connections with the following ITSM tools:
- ServiceNow
- **System Center Service Manager**
- Provance
- Cherwell

With ITSMC, you can create work items in ITSM tool, based on your Azure alerts (metric alerts, Activity Log alerts and Log Analytics alerts).

Availability zone **does not protect** from region failures.

**External collaboration settings** let you turn guest invitations on or off for different types of users in your organization. You can also delegate invitations to individual users by assigning roles that allow them to invite guests.

To synchronize the files in the file share named data to an on-premises server named Server1

You can use Azure File Sync to centralize your organization’s file shares in Azure Files, while keeping the flexibility, performance, and compatibility of an on-premises file server. Azure File Sync transforms Windows Server into a quick cache of your Azure file share. You can use any protocol that’s available on Windows Server to access your data locally, including SMB, NFS, and FTPS. You can have as many caches as you need across the world.
The steps are as follows.
- **Install the Azure File Sync agent**
- **Register Windows Server with Storage Sync Service**
- **Create a sync group and a cloud endpoint**.

If any errors occur in the target slot (for example, the production slot) after a slot swap, restore the slots to their pre-swap states by **swapping the same two slots** immediately.

An app service plan can have multiple web apps. However, the app service plan should be either windows or linux based. The windows app service plan supports .NET, .NET Core and PHP whereas Linux app service plan is needed for Ruby. So, you need **two app service plans**.

When the budget thresholds you’ve created are exceeded, **only notifications are triggered**. None of your resources are affected and your consumption isn’t stopped. You can use budgets to compare and track spending as you analyze costs.



Scenario: PreparationLabs must meet technical requirements including:
Ensure that VM3 can establish outbound connections over TCP port 8080 to the applications servers in the Montreal office.

**IP flow verify **checks if a packet is allowed or denied to or from a virtual machine. The information consists of direction, protocol, local IP, remote IP, local port, and remote port. If the packet is denied by a security group, the name of the rule that denied the packet is returned. While any source or destination IP can be chosen, IP flow verify helps administrators quickly diagnose connectivity issues from or to the internet and from or to the on-premises environment.

Scenario: Create a custom Azure role named Role1 that is based on the Reader role.

**Get-AzRoleDefinition Name Reader | ConvertTo-Json**

So, you need to get the reader role definition.

Scenario: Ensure Azure Multi-Factor Authentication (MFA) for the users in the finance department only.
The recommendation is to **use conditional access policies** that can then be targeted to groups of **users**, specific applications, or other conditions.

While the Network Contributor role provides broad network-related permissions, it doesn’t specifically grant the necessary rights to enable Traffic Analytics. To enable Traffic Analytics, you need to assign a role that includes the permission to manage **Azure Monitor resources**.

Here are the correct roles that would allow Admin1 to enable Traffic Analytics:

- **Owner**: This role provides full access to all resources within the subscription, including Azure Monitor resources.
- **Contributor**: This role also grants full access to all resources within the subscription, including Azure Monitor resources.
- Network Contributor: This role provides broad network-related permissions, but it doesn’t include the necessary permissions to manage Azure Monitor resources.
- Reader: This role provides read-only access to resources within the subscription and doesn’t grant any permissions to manage Azure Monitor resources.

Assigning the Network Contributor role to Admin1 **does not meet** the goal of enabling Traffic Analytics. You need to assign a role that includes the permission to manage Azure Monitor resources, such as **Owner** or **Contributor**.

The Reader role at the subscription level **does not grant** the necessary permissions to enable Traffic Analytics for an Azure subscription. To enable Traffic Analytics, you need to assign a role that has **Monitor** permissions at the subscription level.

Here are some roles that have Monitor permissions:

- Owner
- Contributor
- **Monitor**
- Reader (with the “Monitor resources” permission enabled)

Therefore, you need to assign one of these roles to Admin1 at the subscription level to enable Traffic Analytics.


Ensure that App2 can only read from storage1 for the next 30 days.
What should you configure in storage1 for App2? **Shared access signature (SAS)**

**Access Control (IAM)**: IAM is used to manage access to Azure resources.

The correct order to transfer 2 TB of data from Server1 to an Azure storage account using the Azure Import/Export service is:

1. **Attach an external disk to Server1 and then run waimportexport.exe**: This step prepares the data for transfer by copying it to the external disk.
2. **From the Azure portal, create an import job**: This creates a job in the Azure portal to track the import process.
3. **From the Azure portal, update the import job**: This step provides information about the shipment, such as the carrier and tracking number.
4. **Detach the external disks from Server1 and ship the disks to an Azure data center**: This is the final step to initiate the data transfer.

Key points:
- The Azure Import/Export service allows you to transfer large amounts of data to Azure by shipping physical disks to an Azure data center.
- The waimportexport.exe tool is used to prepare the data on the external disks.
- The import job in the Azure portal tracks the progress of the data transfer.

By following these steps in order, you can successfully transfer your data from Server1 to the Azure storage account using the Azure Import/Export service.

The three actions you should perform to connect VNet1 to the on-premises network by using a site-to-site VPN and minimize cost are:

1. **Create a VPN gateway that uses the Basic SKU**: The Basic SKU is the most cost-effective option for a site-to-site VPN connection. It supports up to 100 VPN connections and is suitable for most small to medium-sized networks.
2. **Create a gateway subnet**: You need to create a subnet within VNet1 to host the VPN gateway resources. This subnet should be in a different availability zone than the subnet that hosts your virtual machines to ensure redundancy.
3. **Create a connection**: You need to create a connection between the VPN gateway in Azure and your on-premises VPN device. This connection will define the parameters for the VPN tunnel, such as the IP addresses, shared key, and protocol.

**DevTest Labs User role** only lets you connect, start, restart, and shutdown virtual machines in your Azure DevTest Labs.

**Logic App Operator** – Lets you read, enable, and disable logic apps, but not edit or update them.

You need to provide the Developers group with the ability to create Azure logic apps in the Dev resource group.
Solution: On Dev, you assign the **Contributor** role to the Developers group.

Contributor Grants full access to manage all resources, but does not allow you to assign roles in Azure RBAC, manage assignments in Azure Blueprints, or share image galleries.

You receive a notification that VM1 will be affected by maintenance.
You need to move VM1 to a different host immediately.
Solution: **From the Redeploy blade, you click Redeploy.**

Instead **redeploy the VM**. If you have been facing difficulties troubleshooting Remote Desktop (RDP) connection or application access to Windows-based Azure virtual machine (VM), redeploying the VM may help. **When you redeploy a VM, Azure will shut down the VM, move the VM to a new node within the Azure infrastructure, and then power it back on, retaining all your configuration options and associated resources**.