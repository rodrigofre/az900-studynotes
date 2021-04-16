# az900-studynotes

## What is cloud computing?
 - Resources consuming on demand as utility e.g. VMs, storage
 - No need to maintain own infrastructure
## Advantages
- Rapid elasticity
- Pay-as-you-need
- Reliability
- Economies of scale

## Types of cloud computing services: how much you manage vs how much cloud vendor manages
 - Infrastructure as a service
 - Platform as a service
 - Software as a service

![image](https://user-images.githubusercontent.com/78084580/115070612-8ca36400-9ecb-11eb-918d-11b4352c665a.png)
![image](https://user-images.githubusercontent.com/78084580/115070713-af357d00-9ecb-11eb-9a6e-928b95311a5f.png)

## CC Services Scenarios
- IaaS: test and development, storage and backups, high performance computing, big data analysis
- PaaS: analytics, business intelligence, development framework
- SaaS: access to sophisticated applications

## CC Deployment Models
- Public Cloud: hardware shared between clients, Azure, Office 365
- Private Cloud: Azure Stack, looks like data center model, hardware used by a single company
- Hybrid Cloud (public + private w/ orchestration): Azure Stack
- Community Cloud: governments, Azure Government, Germany, China

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
	- Availability Zones: unique physical locations within a single region
		- One or more data centers equipped with independent power, cooling and networking
		- Not available in every region: some regions may contain one data center only. When availability zones are available, there's a minimum of three separate zones
		- Some services may replicate data between availability zones automatically
	- Region Pairs: data centers located 300+ miles, main goal to reduce impact on availability
		- Configuration of automatic replication and failover for some services
		- High availability: service updates for one region at one time
		- Outage recover prioritization: at least one region in each pair will be prioritized for disaster recovery
### Azure Resource Groups: logical containers
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
	- Azure Resource Manager
		- Accessed by many tools such as Azure Portal, Azure PowerShell, Azure CLI, REST interfaces

	![image](https://user-images.githubusercontent.com/78084580/115070799-caa08800-9ecb-11eb-96c1-20ede4182b77.png)

- Tools for managing resources
	- Azure CLI Interface
	- Resource Manager Templates
		- Infrastructure as code: script out repeatable deployments of servers and application infrastructure
		- CI/CD pipelines (Azure Pipelines, GitHub, PowerShell, Azure CLI, Azure Portal)
		- .json files that defines infrastructure and configuration for Azure resources
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
	- Azure Mobile App
		- Useful for health and status monitoring for Azure resources
		- Diagnose and fix issues
		- Run commands via Cloud Shell
		- Possible to watch resources
	- Azure Advisor: how to optimize Azure for security best practices, cost savings, reliability, operational excellence and performance
		- Recommendations
		- Possible to create alerts depending on category and impact
## Azure Core products
### Azure Compute: on-demand computing power
- Easy to provision new resources
- Pay as you use
- No need to manage infrastructure with PaaS options
- Scale depending on workloads
- Not only cost savings compared to on-prem, but in terms of ease of development, deployment and hosting
- Azure Virtual Machines: IaaS
	- Full control over OS
	- Maintain and patch VM image
	- When creating a VM: type of image, size of VM (RAM, processors), availability options
	- Lots of preconfigured images and purpose 
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
		- Azure Containers
		- Azure App Service: PaaS, no need to manage infrastructure
		- Azure Serverless Computing: build applications without managing any underlying infrastructure
			- Azure Functions: run small blocks of code
			- Azure Logic Apps: configure workflows in the cloud
			- Azure Event Grid: build applications that respond to events
	- Networking
		- Virtual network gateways
		- Load balancers
		- Azure CDN
	- Storage
		- Azure storage accounts
- Platform solutions
	- Internet of Things
	- Big Data Analytics
  - Artificial Intelligence
