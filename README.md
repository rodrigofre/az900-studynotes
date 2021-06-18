# az900-studynotes

My notes for preparing to AZ-900 exam. I passed! :)

![image](https://user-images.githubusercontent.com/78084580/122605286-9c673200-d04d-11eb-9b17-52edb098b41d.png)

## What is cloud computing?
 - Resources consuming on demand as utility e.g. VMs, storage
 - Delivery of computing services over the Internet
 - No need to maintain own infrastructure
## Advantages
- Faster innovation
- Rapid elasticity (flexible resources)
- Pay-as-you-need
- Reliability
- Economies of scale

## Cloud benefits
![image](https://user-images.githubusercontent.com/78084580/121568955-a60deb80-c9f6-11eb-8bb8-80b80f25861a.png)

## Types of cloud computing services: how much you manage vs how much cloud vendor manages
 - Infrastructure as a service: pay-as-you-go, infrastructure building (renting servers, VMs, storage, networks)
 - Platform as a service: environment for building, testing and deploying software applications, without focus on managing underlying infrastructure
 - Software as a service: users connect to and use cloud-based apps over the Internet

![image](https://user-images.githubusercontent.com/78084580/115070612-8ca36400-9ecb-11eb-918d-11b4352c665a.png)
![image](https://user-images.githubusercontent.com/78084580/115070713-af357d00-9ecb-11eb-9a6e-928b95311a5f.png)
![image](https://user-images.githubusercontent.com/78084580/121570161-fd608b80-c9f7-11eb-8305-848d09470b2a.png)
![image](https://user-images.githubusercontent.com/78084580/121570324-23862b80-c9f8-11eb-8f6a-3360b4b70b72.png)

## CC Services Scenarios
- IaaS: test and development, storage and backups, high performance computing, big data analysis
- PaaS: analytics, business intelligence, development framework
- SaaS: access to sophisticated applications

## CC Deployment Models
- Public Cloud: hardware shared between clients, Azure, Office 365
- Private Cloud: Azure Stack, looks like **data center model**, hardware used by a single company (company responsible), no access to users outside of the organization
- Hybrid Cloud (public + private w/ orchestration): Azure Stack
- Community Cloud: governments, Azure Government, Germany, China

![image](https://user-images.githubusercontent.com/78084580/121568689-54fdf780-c9f6-11eb-8ea5-10decdeed618.png)

## CapEx vs. OpEx
![image](https://user-images.githubusercontent.com/78084580/121569436-2af90500-c9f7-11eb-9eea-f1c692b14c7b.png)
![image](https://user-images.githubusercontent.com/78084580/121569603-5976e000-c9f7-11eb-91d3-ed65d0d22bf2.png)

## Azure Concepts
### Azure Data Centers
- 160+ Azure data centers around the world
- 150+ edge locations: smaller data centers, caching (Azure CDN)
- Organized into regions: multiple data centers within regions to help with failover (fault tolerance) and high availability
- Economy of scale: no costs related to hardware and infrastructure management
- Datacenter security
	- You don't know the specific locations of each data center
	- Access control: prior approval and justification
	- Physical security, security guards, biometric identification
	- Complies with standards and regulations: ISO 27001, HIPAA, FedRamp, SOC 1&2
	- Region-specific standards: Australia, UK
	- Virtual security: data encryption, separate from data of other customers
	- Redundancy: data stored three times within the data center, possible to expand to other data centers (disaster recovery)
	- Security professionals dedicated to keep customer data and applications safe
- Energy efficiency
	- Data centers are carbon neutral since 2012
	- Renewable energy certificates
	- 100% renewable energy by 2025
	- Solar, wind and hydropower 
	- Research and experimenting
### Azure Regions: physical location of a data center or multiple data centers
![image](https://user-images.githubusercontent.com/78084580/115070752-bc526c00-9ecb-11eb-97d1-f5ff42361c6c.png)
- Choices affect performance and availability of data: high availability and disaster recovery
- Not all services are available in all regions
	- Some services do not require specific region
	- Regions may have regulatory and compliance rules: data residency
	- Azure Geographies: contains one or more regions
		- Used to meet data residency and compliance requirements
		- Single country or set of countries
	- Availability Sets: keep applications online during maintenance or hardware failure
		- ![image](https://user-images.githubusercontent.com/78084580/121571983-12d6b500-c9fa-11eb-890a-0bc0c22fdef1.png)
		- Update domains (UD): scheduled maintenance, performance or security updates are sequenced through update domains
		- Fault domains (FD): physical separation of workloads across different hardware in a datacenter
	- Availability Zones: unique physical locations within a single region
		- ![image](https://user-images.githubusercontent.com/78084580/121572347-74971f00-c9fa-11eb-94e2-6a5d4d6b502c.png)
		- One or more data centers equipped with independent power, cooling and networking
		- Not available in every region: some regions may contain one data center only. When availability zones are available, there's a minimum of three separate zones
		- Some services may replicate data between availability zones automatically
		- Connected through private fiber-optic networks
	- Region Pairs: data centers located 300+ miles, main goal to reduce impact on availability
		- Configuration of automatic replication and failover for some services
		- High availability: service updates for one region at one time
		- Outage recover prioritization: at least one region in each pair will be prioritized for disaster recovery
		- Updates rolled out sequentially to minimize downtime
		- ![image](https://user-images.githubusercontent.com/78084580/121571535-8926e780-c9f9-11eb-8317-6d64a215e1d6.png)
![image](https://user-images.githubusercontent.com/78084580/121571671-b2e00e80-c9f9-11eb-9c20-dc69cfc802a3.png)
### Azure Resource Groups: logical containers to manage and aggregate resources in a single unit
![image](https://user-images.githubusercontent.com/78084580/121572665-ccce2100-c9fa-11eb-9b91-ece3076f6c3e.png)
- Resource: manageable item (VMs, storage, web apps, databases)
- Container that holds related resources: set of resources that share the same lifecycle
- Deploy, update and delete resources together
- It's possible moving individual resources between resource groups
- Resources can be in a single resource group only
- Resources in a resource group can communicate with resources in other resource groups
- Resources can be in different regions
- Resource group can be created in a different region than the resources in the group
- If a resource needs to exist on a different deployment cycle, it should be in another resource group
- Security controls for administrative actions: roles in the team do not have full control to every resource
- Can export infrastructure-as-code using resource manager templates
	- Azure Resource Manager: management layer tha enables creation, update and deletion of resourcesn in a Azure subscription
		- Accessed by many tools such as Azure Portal, Azure PowerShell, Azure CLI, REST interfaces
	![image](https://user-images.githubusercontent.com/78084580/115070799-caa08800-9ecb-11eb-96c1-20ede4182b77.png)
	- Azure Subscription: authenticated and authorized access to Azure accounts
		- Billing boundary: separate billing reports and invoices for each subscription
		- Access control boundary: manage and control access to resources that users can provision with specific subscriptions
		- ![image](https://user-images.githubusercontent.com/78084580/121573083-34846c00-c9fb-11eb-818e-86bf282c4250.png)

# Azure Resources
![image](https://user-images.githubusercontent.com/78084580/121572544-adcf8f00-c9fa-11eb-82cb-1b7fc278a83b.png)

- Tools for managing resources (Azure Management/Monitoring Tools)
	- Azure CLI Interface
	- Resource Manager Templates
		- Infrastructure as code: script out repeatable deployments of servers and application infrastructure
		- CI/CD pipelines (Azure Pipelines, GitHub, PowerShell, Azure CLI, Azure Portal)
		- .json files that defines infrastructure and configuration for Azure resources
		- Create and deploy Azure infrastructure without having to write programming commands
		- ![image](https://user-images.githubusercontent.com/78084580/121587192-e5463780-ca0a-11eb-9181-326d1c8ff669.png)
	- Azure Service Health
		- Global view of health of Azure across regions
		- Azure Status
		- Service issues, planned maintenance
		- Health advisories: features or services getting deprecated
		- Security advisories: notifications or violations that may affect availability of services
		- Resource health: service specific information -> if any issues, information on actions to be taken by Microsoft
		- Health alerts: to be notified when there are any changes to services or status of resources. It’s possible to filter what kinds of alerts to receive, for which event type, services and/or regions. Sent to action groups
		- Action groups: group to include people to be notified on health alerts via email/sms/push/voice
	- Azure Monitor: collecting and analyzing telemetry from Azure services
		- Can monitor on-prem resources
		- Collects metrics from azure resources (single resources only)
		- Different metrics depending on type of resource
		- Maximize availability and performance of applications
		- Application Insights, Log Analytics, Smart Alerts, Automation Alerts, Customized Dashboards
	- Azure Mobile App
		- Useful for health and status monitoring for Azure resources
		- Diagnose and fix issues
		- Run commands via Cloud Shell
		- Possible to watch resources
	- Azure Advisor: how to optimize Azure for security best practices, cost savings, reliability, operational excellence and performance
		- Recommendations
		- Possible to create alerts depending on category and impact
	- Azure PowerShell
	- Azure Cloud Shell
	- Azure REST API 
	- Azure Portal
## Azure Core products
### Azure Compute: on-demand computing power
- Easy to provision new computing resources, like disks, processors, memory, networking and operating systems
- Pay as you use
- No need to manage infrastructure with PaaS options
- Scale depending on workloads
- Not only cost savings compared to on-prem, but in terms of ease of development, deployment and hosting
- Azure Virtual Machines: IaaS
	- Full control over OS
	- Maintain and patch VM image
	- When creating a VM: type of image, size of VM (RAM, processors), availability options
	- Lots of preconfigured images and purpose (Azure Marketplace: applications/services created by Microsoft or technology partners)
	- Shut down to save costs: manually or on a schedule
	- Enables hybrid cloud: extend on-prem
	- Administrative model: role-based, permissions
	- Lift-and-shift migration: on-prem VMs migration to the cloud -> Azure Site Recovery, Azure Migrate (assess the compatibility of on-prem VMs and databases
	- Possibility to change disk size, enable auto-shutdown, configure backup
	- Tools to support troubleshooting VM problems (e.g. boot problems)
	- Connect to the machine remotely via RDP, SSH or Bastion
	- Virtual Machine Scale Set: multiple VMs at once with configured load balancing
		- Number of VMs can be configured to increase or decrease depending on load or schedule
		- Spread VMs across fault domains and update domains
		- No additional charge for scale set: pay for underlying resources (VMs, load balancer, disk storage)
	- Azure Batch: pool of VMs to do large-scale high performance computing jobs in parallel
		- Azure Containers: reduction of costs and improve agility by simplifying processes and reducing friction when releasing/shipping applications
			![image](https://user-images.githubusercontent.com/78084580/115288568-f28c2780-a127-11eb-8a62-8602e6dd1b05.png)
			![image](https://user-images.githubusercontent.com/78084580/115291288-f1a8c500-a12a-11eb-866f-9da4410471bf.png)
			- Azure Container Instances: deploy containers without maintaining or patching environments
				- Smaller applications: simple web apps, smaller devtest scenarios, small-scale batch processing
				- Single container instance per container (low availability, limited scalability)
			- Azure Kubernetes Service: more complex architectures with greater control around deploying and managing health and performance of containers
				- Container management system
				- Scale out container-based applications
				- Monitoring and deploying containers 
				- Possibility to leverage VM Scale Sets
				- Connect with Azure Container Registry: pull container images and build containers from those images
				- Connect with Azure Monitor: monitoring performance and health of the cluster
			- Azure App Service
		- Azure App Service: PaaS, no need to manage infrastructure
			- Similar to traditional web hosting: frameworks already installed on servers
			- Handles management and patching of the web servers
			- Hosts web applications, REST APIs, back-end for mobile applications, containers, WebJobs (continuously/on-schedule) -> executable files, scripts
		- Azure App Service Plans: defines size of the underlying infrastructure (VMs Azure-managed, limited access) like CPU, RAM and storage -> pricing tier
			- Access to different features depending on the pricing tier
		- Azure Serverless Computing: build applications without managing any underlying infrastructure
			- Focus on code and business logic
			- Azure Functions: run small blocks of code
				- Initiated by triggers, timer event
				- Based on events
			- Azure Logic Apps: configure/design workflows in the cloud
				- No need to write code, but it's possible to call Azure Functions if needed
				- Initiated by triggers
				- Large library of connectors (e.g. SharePoint, Azure Storage, Zendesk, SAP, Outlook)
			- Azure Event Grid: build applications that respond to events (event-based architecture e.g publish/subscribe)
				- Connects data sources and event handlers
				- Possibility to create events subscription, automation
		![image](https://user-images.githubusercontent.com/78084580/115916234-e74c3b00-a44a-11eb-8ff7-cdc9e36ea283.png)
	- Networking
		- Virtual network
		![image](https://user-images.githubusercontent.com/78084580/115917864-267b8b80-a44d-11eb-985b-9c2b375dbd61.png)
		- Load balancers
		![image](https://user-images.githubusercontent.com/78084580/115918043-62aeec00-a44d-11eb-9274-be4a940f7c2b.png)
			- Application Gateway
			![image](https://user-images.githubusercontent.com/78084580/115918101-78241600-a44d-11eb-96db-506354449a6c.png)
				- SSL Termination
				- Autoscaling
				- Session Affinity
				- HTTP Header Rewriting
				- Advanced Routing
				- Web Application Firewall
		- Hybrid Cloud
		![image](https://user-images.githubusercontent.com/78084580/115918377-d4873580-a44d-11eb-8c71-4fd1833b4515.png)
		![image](https://user-images.githubusercontent.com/78084580/115918753-495a6f80-a44e-11eb-81ae-e58f1937bd5c.png)
			- ExpressRoute: connect on-prem servers directly to Microsoft data centers
				- Increased speed and encryption options -> increased cost
				- Made for big corporate clients with major security requirements
				- Pricing may be under metered data (per GB) or unlimited data (monthly fee)
				- Bandwidth up to 10Gbps (100Gbps if using ExpressRoute Direct)
				- Also provides redundancy
		- Windows Virtual Desktop
				- Full desktop for users
				- Apps running remotely
				- Similar to Remote Desktop Services (RDS) 
				- Fully managed solution in the cloud
				- Possibility to use a single VM for multiple users: each user's data persisted on a separate disk
				- Possibility to scale in and/or out depending on needs (pay as you go)
				- Possibility of using pre-built images on Azure Marketplace or own prebuilt custom images
				- Authentication: Azure Active Directory, Azure multi-factor authentication
				- Support for most Windows Server versions and 10, 7
		- Azure CDN: distributed network of servers to store cached data, in order to minimize latency to global users and offloading traffic from source web
		![image](https://user-images.githubusercontent.com/78084580/115921328-b6bbcf80-a451-11eb-8e8c-faf5cb062865.png)
		![image](https://user-images.githubusercontent.com/78084580/115921553-069a9680-a452-11eb-880c-ba98d8342e09.png)
		![image](https://user-images.githubusercontent.com/78084580/115921713-41043380-a452-11eb-848b-81295330be6b.png)
		![image](https://user-images.githubusercontent.com/78084580/115921836-71e46880-a452-11eb-9aac-e84e5882b042.png)
			- Mostly static data e.g. images, fonts, videos, HTML pages, client-side scripts, etc.
			- Can connect to multiple Azure services
			- Dynamic Site Acceleration: deliver content faster
			![image](https://user-images.githubusercontent.com/78084580/115922030-ba038b00-a452-11eb-9eb6-ec08845ce622.png)
			![image](https://user-images.githubusercontent.com/78084580/115922100-dacbe080-a452-11eb-8d55-c1606acde522.png)
## Azure Data Storage
- Benefits
	- Automated backup and recovery
	- Replication across the world
	- Encryption options
	- Security and platform integration
	- Development features and support
![image](https://user-images.githubusercontent.com/78084580/115923054-0f8c6780-a454-11eb-9725-3969459b2f83.png)
### Structured data management
- SQL Server on VMs
	- Full control over SQL Server
	- Provision VMs from Azure Marketplace
	- Pay as you go pricing - no licensing fees
	- Automated updates scheduling
	- Managed backup to Microsoft Azure
- Azure SQL Database: fully managed platform-as-a-service
	- Always running the latest version of SQL Server
	- Flexible pricing model: number of virtual cores, DTUs (database transaction units: CPU + memory + data throughput)
	- Flexible deployment options: single database, elastic pool (collection of databases with shared set of resources)
	- Automatic scaling
	- Service tiers for different workloads: common workloads, high transaction rates, very large transactional
	- Some built-in functions are not available, but majority of features is available
- Azure SQL Managed Instance
	- Broadest set of SQL Server capabilities
	- Benefits of managed platform
	- Deploy VM onto VNET
	- Lift-and-shift on-prem databases with minimal changes into an isolated environment
	- Automatic patching and version updates, automated backups, high availability
- Azure Database for MySQL: platform-as-a-service
	- Open-source tools and platform compatibility
	- MySQL Community Edition
	- Pay as you go pricing
	- High availability
	- Dynamic scalability
	- Encryption
	- Automated patching and backup
- Azure Database for PostgreSQL: platform-as-a-service
	- Supports complex data structures
	- Geometric data types
	- Extensions for GIS
	- Managed database features (same as Azure Database for MySQL)
	- Deployment models: single server and Hyperscale Citus (faster response time, good performance for huge datasets 100GB+)
- Other databases can be used under VMs (some images available on Azure Marketplace) 
### Semi-structured data management
- Azure Cosmos DB: globally distributed, multi-modal database
![image](https://user-images.githubusercontent.com/78084580/115926297-0356d900-a459-11eb-97a9-971502ea437b.png)
	- Fast response times
	- Ability to scale up and down rapidly and globally: different regions
	- Backed by SSD storage
	- Consistency options: ensure distributed data is updated
	- Flexible: APIs, not one-size-fits-all
![image](https://user-images.githubusercontent.com/78084580/115926579-71030500-a459-11eb-9dd1-d1c834dae79d.png)
### Data Services
- Azure Storage Accounts
![image](https://user-images.githubusercontent.com/78084580/115927577-03f06f00-a45b-11eb-9450-7a32701c9451.png)
![image](https://user-images.githubusercontent.com/78084580/115927624-14084e80-a45b-11eb-8d57-caffaee62bfe.png)
![image](https://user-images.githubusercontent.com/78084580/115927649-1f5b7a00-a45b-11eb-8074-5255611609c7.png)
![image](https://user-images.githubusercontent.com/78084580/115927679-300bf000-a45b-11eb-9b6a-04a3f9e78542.png)
![image](https://user-images.githubusercontent.com/78084580/115927736-45811a00-a45b-11eb-8694-3707031e03c8.png)
	- Azure Blob Storage: unstructured data e.g. files and documents
	![image](https://user-images.githubusercontent.com/78084580/115929004-6b0f2300-a45d-11eb-8eb3-c23345bb7896.png)
		- Blob snapshots
		- Blob leases: prevent other people to make changes
		- Soft delete: recycle bin
		- Static website hosting
		- CDN integration
		- Azure Search integration
		- Cost factors: storage cost vs transaction cost
		![image](https://user-images.githubusercontent.com/78084580/115929196-bf1a0780-a45d-11eb-8554-1f08b6123777.png)
	- Azure File Storage 
		- SMB protocol (port 445)
		- Can be attached to VMs like a network drive
		- File share with drive letter e.g. H:\
		- Good for migration scenarios
		- Files accessible through REST interface with mechanisms for restricting access
		- Can be mounted concurrently by cloud or on-prem servers
		- Can be cached on Windows servers using Azure File Sync for fast access
			- Possibility to tier files based on how they're used
	- Azure Disk Storage: VMs disks
	- Azure Table Storage: structured date in form of NoSQL non-relational data (similar to CosmosDB)
	- Azure Queue Storage: store and retrieve messages
- Data Access Authorization
	- Role-based access control in Azure Active Directory
	- Storage account keys
	- Shared Access Signatures
		- Security token string 
		- Scope access to particular services, containers or folders
		- Start and end validity period
		- May contain permissions
- Programatic access to storage accounts
	- REST APIs
	- SDKs for many languages
	- PowerShell
	- Azure CLI
	- Azure Storage Explorer
	- AzCopy (CLI tool)
- Transferring data to Azure
	- Azure Database Migration Service
## Azure Platform Solutions
- Internet of Things
	- Azure IoT Central: fully managed global IoT SaaS solution that makes it easy to connect, monitor and manage IoT assets at scale
	- Azure IoT Hub: managed service hosted in the cloud, act as a central message hub for bi-directional communication between IoT applications and devices
	- Azure Sphere: secured, high-level application platform with built-in communication and security features for internet-connected devices
- Big Data & Analytics
	- Azure Synapse Analytics: cloud-based enterprise data warehouse
	- Azure HDInsight: fully managed, open-source analytics service for enterprises
	- Azure Databricks: Apache Spark based analytics service
- Artificial Intelligence & Machine Learning
	- Azure Machine Learning: cloud-based to develop, train and deploy machine learning models
	- Azure Cognitive Services: quickly enable apps to see, hear, speak, understand and interpret user's needs
	- Azure Bot Service: develop intelligent, enterprise-grade bots
## Azure DevOps Solutions
- Azure DevOps: development collaboration tools including pipelines, Kanban boards and automated cloud-based load testing
- GitHub: software development hosting with version control, source code management and bug/task management
- GitHub Actions for Azure: automate software workflow to build, test and deploy from within GitHub
- Azure DevTest Labs: quickly create environments in Azure while minimizing waste and controlling cost

# Azure Security and Network Security
## Security tools and features
- Azure Security Center: monitoring service that provides threat protection across both Azure and on-prem datacenters
	- Security recommendations, detect and block malware, analyze and identify potential attacks
	- Capabilities:
	- ![image](https://user-images.githubusercontent.com/78084580/121724833-cef9b380-cabe-11eb-9892-893702885762.png)
- Azure Sentinel: security information management (SIEM) and security automated response (SOAR) solution that provides security analytics and threat intelligence across an enterprise
	- Integrations with Office 365, Azure Active Directory, Microsoft Cloud App Security, Advanced Threat Protection
- Key Vault: stores application secrets in a centralized cloud location in order to securely control access permissions and access logging
	- Secrets management
	- Key management
	- Certificate management
	- Access policies
- Azure Dedicated Hosts: physical servers that host one or more Azure virtual machines that is dedicated to a single organization's workload
	- Hardware isolation at server level
	- Control over maintenance event timer
	- Aligned with Azure Hybrid Use Benefits

## Secure network connectivity
- Defense in depth
	- Layered approach to securing computer systems
	- Multiple levels of protection
	- Shared concern between cloud providers and customers
	- ![image](https://user-images.githubusercontent.com/78084580/121726200-a1156e80-cac0-11eb-8ffc-8897ea0a747f.png)
	- ![image](https://user-images.githubusercontent.com/78084580/121726296-be4a3d00-cac0-11eb-90a3-2e7999d50d01.png)
	- Combine network security solutions (e.g. NSGs with Azure Firewall, perimeter layer with DDoS protection and Firewall, networking layer with NSG)
- Network Security Groups (NSG)
	- ![image](https://user-images.githubusercontent.com/78084580/121726491-02d5d880-cac1-11eb-89d4-e93cf788fd71.png)
- Azure Firewall
	- ![image](https://user-images.githubusercontent.com/78084580/121726607-2a2ca580-cac1-11eb-84dd-4de09c3ca50a.png)
- Azure DDoS protection
	- ![image](https://user-images.githubusercontent.com/78084580/121726825-6fe96e00-cac1-11eb-8d19-f218b754d136.png)

# Identity, governance, privacy and compliance
## Azure Identity Services
- Authentication and authorization
![image](https://user-images.githubusercontent.com/78084580/121727356-2ea58e00-cac2-11eb-9109-d2bd6a3c1781.png)
- Multi-Factor Authentication: additional security requiring two or more elements for full authentication (something you now, possess and/or are)
- Azure Active Directory
![image](https://user-images.githubusercontent.com/78084580/121727548-70363900-cac2-11eb-9ec5-a614a747ff81.png)
	- Condition access
	- ![image](https://user-images.githubusercontent.com/78084580/121727687-9d82e700-cac2-11eb-9458-dd5ea623b29b.png)
## Azure Governance methodologies
- Role based access control (RBAC)
	- Fine grained access management
	- Segregate duties within the team and grant only amount of access to users that need to perform their jobs
	- Access to Azure portal and access control to resources
- Resource locks
![image](https://user-images.githubusercontent.com/78084580/121728570-d8d1e580-cac3-11eb-9f6f-e239abcd18b4.png)
- Tags
	- Metadata for Azure resources
	- Logically organizes resources into a taxonomy
	- Consists of name-value pair
	- Very useful for rolling up billing information
![image](https://user-images.githubusercontent.com/78084580/121728791-1b93bd80-cac4-11eb-8974-dad054d34403.png)
- Management Groups
![image](https://user-images.githubusercontent.com/78084580/121728879-37975f00-cac4-11eb-9f86-d570fd0f3f00.png)
- Azure Policy
![image](https://user-images.githubusercontent.com/78084580/121729114-79c0a080-cac4-11eb-907b-9a7331291b9e.png)
- Azure Blueprints
- Cloud Adoption Framework for Azure
![image](https://user-images.githubusercontent.com/78084580/121730447-133c8200-cac6-11eb-9be2-f12278e24449.png)

## Privacy, compliance and data protection
- Microsoft core tenants of Security, Privacy and Compliance
![image](https://user-images.githubusercontent.com/78084580/121730639-55fe5a00-cac6-11eb-9dd3-9609aab4c35c.png)
- Compliance Terms and Requirements
![image](https://user-images.githubusercontent.com/78084580/121730835-9231ba80-cac6-11eb-94d4-e258cebdce64.png)
- Microsoft Privacy Statement
![image](https://user-images.githubusercontent.com/78084580/121730940-b097b600-cac6-11eb-864b-c5aef208ba85.png)
- Online Services Terms and Data Protection Addendum
![image](https://user-images.githubusercontent.com/78084580/121730995-c3aa8600-cac6-11eb-8276-6c0ab7418f54.png)
- Trust Center
![image](https://user-images.githubusercontent.com/78084580/121731062-d624bf80-cac6-11eb-8fdb-7ab332e5a9dc.png)
- Azure Compliance Documentation
![image](https://user-images.githubusercontent.com/78084580/121731229-08ceb800-cac7-11eb-9722-2e633baf0c96.png)
- Azure Sovereign Regions
![image](https://user-images.githubusercontent.com/78084580/121731370-37e52980-cac7-11eb-9eda-7c29759c0474.png)
![image](https://user-images.githubusercontent.com/78084580/121731439-52b79e00-cac7-11eb-87da-e2bd3a135629.png)

# Azure Pricing
## Planning and Cost Management
- Factors that affect costs
![image](https://user-images.githubusercontent.com/78084580/121733080-66fc9a80-cac9-11eb-85a3-9fa5be7c5dad.png)
![image](https://user-images.githubusercontent.com/78084580/121733265-a4f9be80-cac9-11eb-90ae-3948629f3a81.png)

- Factors that reduce costs
- Pricing calculator
![image](https://user-images.githubusercontent.com/78084580/121733536-fefa8400-cac9-11eb-88a4-4321ad42d517.png)
- Total Cost of Ownership Calculator
![image](https://user-images.githubusercontent.com/78084580/121733587-0d48a000-caca-11eb-8c4c-8fc2bfd601cb.png)
- Azure Cost Management
![image](https://user-images.githubusercontent.com/78084580/121734571-551bf700-cacb-11eb-8a50-f5144d87a078.png)
- Minimizing costs
![image](https://user-images.githubusercontent.com/78084580/121734671-7a106a00-cacb-11eb-8697-0f6fcc9975fa.png)

## Azure Service Level Agreements (SLA) and Service Lifecycles
![image](https://user-images.githubusercontent.com/78084580/121735125-133f8080-cacc-11eb-859a-03b7e74fd857.png)
![image](https://user-images.githubusercontent.com/78084580/121735212-2fdbb880-cacc-11eb-9913-fc5a4fa780c6.png)
![image](https://user-images.githubusercontent.com/78084580/121735317-5699ef00-cacc-11eb-88ac-292c5f937eeb.png)
![image](https://user-images.githubusercontent.com/78084580/121735513-9d87e480-cacc-11eb-9dd1-1c5e471261c3.png)
![image](https://user-images.githubusercontent.com/78084580/121735651-cad49280-cacc-11eb-9407-523292efa8ad.png)
![image](https://user-images.githubusercontent.com/78084580/121735851-14bd7880-cacd-11eb-8d93-21059fd4b566.png)
