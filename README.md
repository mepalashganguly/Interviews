## Cloud

<a name="Cloud Migration"></a>

<details>
<summary>1.1 - what is Azure SQL Managed Instance?</summary><br><b>

Azure SQL Managed Instance
Designed for: Easy migration of on-premises SQL Server workloads to Azure with minimal changes—ideal for organizations wanting high compatibility with full SQL Server features.

Compatibility: Nearly 100% compatible with on-prem SQL Server, supporting cross-database queries, SQL Agent jobs, CLR integration, and more advanced capabilities not available in Azure SQL Database.

Control: More control over instance-level settings, network isolation (native VNet integration), and advanced security options—similar experience to managing on-prem SQL but without OS access.

Best for: Lift-and-shift migrations, applications that need legacy features, or complex SQL workloads needing broad SQL Server support.

Cost: Higher than Azure SQL Database, but often more cost-effective than running a full VM for complex/multiple databases.

Networking: Access via private virtual network only.

Deployment: Suited for customers with substantial SQL workloads requiring instance-scoped features and broader SQL Server compatibility.

</b></details>


<details>
<summary>1.2 Azure SQL Database? Cost Factors?</summary><br><b>


Azure SQL Database
Designed for: Modern, cloud-native applications that require a fully managed, scalable, and highly available relational database.

Compatibility: Supports most SQL Server features needed for typical applications—but does not support all instance-level or integration features (no cross-database queries, no SQL Agent, for example).

Simplicity & Scalability: Quick to provision; offers options like single databases and elastic pools, easy to scale up/down based on demand.

Best for: New app development, SaaS, web apps, and transactional workloads that don’t need full legacy SQL Server functions.

Cost: Generally less expensive than Managed Instance. Pay for only the resources you use.

Networking: Public and private connection options.

Deployment: Perfect for serverless use cases and companies needing rapid scalability with minimal administrative overhead.

Managed Instance is considerably more expensive for the same compute/storage, but justifies this with advanced compatibility and features for large, complex or legacy workloads.

Azure SQL Database is less costly and more flexible for scaling out hundreds/thousands of databases, especially with elastic pools and serverless compute.

Both offer licensing/commitment discounts and backup/retention as line items; storage costs are similar.

</b></details>

<details>
<summary>1.3 comparison Azure Instance and Azure SQL Database? Cost Factors? </summary><br><b>

Summary Table
Feature	Azure SQL Managed Instance	Azure SQL Database
Compatibility	Near-complete SQL Server	Most SQL features
Instance-level Features	Yes	No
Cross-database Queries	Yes	No
Network Isolation	VNet only	VNet & public options
Best for	Lift-and-shift, complex/legacy	New, cloud-native
Scalability	High (instance-level)	High (db-level)
Cost	Higher	Lower
Bottom line:

Choose Managed Instance for full SQL Server compatibility or migration with complex needs.

Choose Azure SQL Database for new cloud-first apps, microservices, or simple/medium workloads where cost, simplicity, and fast scaling matter most.

Hybrid and migration scenarios often start with Managed Instance for compatibility and then refactor toward Azure SQL Database for cost and modern agility.

</b></details>

<details>
<summary>1.3 How SSL Works? </summary><br><b>
  
When a client initiates a connection, it requests a secure (SSL/TLS) session.

The server presents its SSL certificate, issued by a trusted Certificate Authority (CA).

The client validates the server's certificate to establish authenticity and trust.

Both client and server negotiate encryption algorithms and session keys.

Data sent between client and server is encrypted using these keys, preventing eavesdropping or tampering.

Summary of SSL Steps in a Database Environment:

Client connects; requests SSL/TLS.

Server presents certificate; client validates it.

Both negotiate encryption method and key.

All communication in the session is encrypted.

</b></details>

<details>
<summary>1.4 Azure Traffic Manager? </summary><br><b>

Azure Traffic Manager is a DNS-based global traffic load balancer that enables you to distribute incoming traffic across multiple geographically dispersed endpoints, such as Azure regions, on-premises sites, or other cloud services. It directs client requests to the best available endpoint based on configurable traffic-routing methods, health monitoring, and failover policies.

Key Features of Azure Traffic Manager:
Global DNS-based traffic routing: Client DNS queries are resolved to the most appropriate service endpoint.

Multiple routing methods: Priority, weighted, performance (lowest latency), geographic, multi-value, and subnet-based routing to tailor traffic flow.

Health monitoring: Continuously checks the health of each endpoint and automatically removes unhealthy endpoints from rotation.

High availability and failover: In case of endpoint or even entire region failures, traffic is rerouted automatically to healthy endpoints to ensure service continuity.

Works with Azure and external/non-Azure endpoints: Can route traffic across cloud regions or on-premises infrastructure.

Improves performance: By directing users to the closest or best-performing endpoint globally, it reduces latency and enhances user experience.

Azure Traffic Manager is a global DNS-based traffic load balancer that controls how user traffic is distributed across multiple application endpoints (which can be in Azure, other clouds, or on-premises). It works by intercepting DNS queries for your application’s domain and responding with the IP address of the best endpoint based on configured traffic-routing rules and endpoint health.

Here’s how Azure Traffic Manager works in detail:

DNS-Level Operation:
Traffic Manager functions at the DNS layer (Application Layer/Layer 7). When a user tries to access your service, their device asks its DNS resolver to translate your domain name into an IP address.

DNS Query Resolution Process:

The client’s DNS resolver recursively queries authoritative DNS servers.

When the request reaches Azure Traffic Manager's DNS servers, Traffic Manager decides which endpoint to respond with based on:

Endpoint health (unhealthy endpoints are excluded).

The traffic-routing method you configured (e.g., priority, weighted, performance, geographic).

</b></details>

<details>
<summary>1.5 Monolithic Vs Microservices? </summary><br><b>
Monolithic Architecture
A single, unified application where all components (UI, business logic, data access) are tightly integrated and run as one unit.

Typically has a single codebase and a centralized database.

Easier to develop initially and simpler to deploy as just one package.

Components communicate internally through shared memory, resulting in faster communication.

Updating one part often requires redeploying the entire application.

Scaling is done by replicating the whole application, which can be inefficient.

Risk of a single point of failure affecting the entire system.

Best suited for simple, smaller applications or where rapid initial development is prioritized.

Microservices Architecture
The application is broken into small, independent, loosely coupled services, each handling a specific business function.

Each microservice has its own codebase, deployment, and often its own database.

Services communicate over networks, usually via APIs, which adds some latency.

Offers independent deployment and scaling of services, enabling efficient resource use.

Easier to update and maintain individual components without affecting the entire system.

Supports technological diversity, letting teams choose different languages or frameworks per service.

More complex to design, develop, debug, and manage due to distributed nature.

Better fault isolation—failure in one service usually does not bring down the whole application.

Ideal for large, complex, scalable applications needing flexibility and continuous delivery.

Summary Table
Aspect	Monolithic Architecture	Microservices Architecture
Structure	Single unified codebase & deployment	Multiple independent, loosely coupled services
Development	Initially simpler; later more complex to maintain	Complex initially; easier to maintain over time
Deployment	Single deployment unit	Independent deployment per service
Scalability	Scale entire application	Scale services independently
Technology Flexibility	Limited—one tech stack for entire app	High—choose best tech per service
Fault Tolerance	Single point of failure potential	Failure isolated to individual service
Communication	Internal, faster (shared memory)	Network calls, may introduce latency
Maintenance	Difficult as app grows	Easier with modularity and autonomy
Best For	Small to medium apps with less complexity	Large, complex, evolving applications
Choosing between the two depends on the application's size, complexity, scalability needs, team expertise, and business goals. Monolithic suits simpler, smaller apps or when rapid development is essential. Microservices excel at supporting large-scale, complex systems requiring flexibility, resilience, and frequent updates.

This distinction helps in designing modern, scalable, and maintainable software based on specific organizational contexts and future growth plans.
</b></details>

<details>
<summary>1.6 Decission to take wheter to go to Cloud? </summary><br><b>

Deciding between a traditional data center and cloud infrastructure depends on multiple critical factors:

1. Cost Structure
Data Center: High upfront capital for hardware, facilities, and staff, plus ongoing maintenance and energy costs. Economies of scale are only achieved at high, consistent utilization rates.

Cloud: No upfront hardware investment; pay-as-you-go for only what you use. Operational expenses can scale with business needs, but costs may become unpredictable with spikes in usage.

2. Scalability and Flexibility
Data Center: Scaling requires physical expansion, planning, hardware procurement, and time (often months). Capacity is fixed once provisioned, risking both over- and under-utilization.

Cloud: Resources can scale up or down instantly and in small increments, fitting variable or unpredictable workloads and enabling rapid experimentation or global reach.

3. Control, Customization, and Security
Data Center: Full control and visibility over hardware, software, network, and security. Suits organizations with strict compliance/regulatory, latency, or data residency needs.

Cloud: Security and configuration are shared with the provider. Modern cloud platforms offer robust security, but some organizations require direct oversight only possible on-premises. Custom hardware or deep system tuning is easier with traditional data centers.

4. Compliance and Regulatory Requirements
Data Center: Easier to physically secure data and demonstrate compliance in highly regulated sectors (finance, healthcare, government).

Cloud: Major providers possess numerous certifications, but highly specific or national standards may still require physical control only achievable on-premises.

5. Performance, Latency, and Availability
Data Center: Dedicated resources and network may yield lower and more predictable latency. Better for applications needing close-to-the-metal performance.

Cloud: Performance is usually high but can fluctuate due to shared infrastructure. High availability, redundancy, and disaster recovery come built-in, but at premium pricing.

6. Staffing and Operational Burden
Data Center: Needs specialized in-house staff for monitoring, upgrades, support, and security.

Cloud: Reduces staff needs since the provider manages physical hardware, much of the routine maintenance, and basic security.

7. Deployment and Resource Provisioning Speed
Data Center: New environments take time—install hardware, configure networks, etc.

Cloud: Provision new resources and services in minutes, accelerating project delivery and recovery from failures.

In summary:

Prefer cloud for agility, scalability, lower upfront costs, and rapidly changing or unpredictable workloads.

Choose data center if your organization must have close control, strict compliance, extreme customization, or already owns substantial infrastructure.

Hybrid approaches are increasingly popular, blending the predictability and control of data centers with the flexibility and global scalability of cloud platforms.

</b></details>

<details>
<summary>1.7 How to make Cloud Strategy for my Project? </summary><br><b>

1. How much I have time
2. Whether my App is stratigic? ( life time of an App, if it's not stratigic App then rehost )
3. Total Cost of Ownership by time and ROI
4. My Project Budget
5. Company Strategy ( IAAS/PAAS/SAAS )
6. Effort ( Low/Midium/high )
7. Discover -  
   7.1 What App? --- ( Understand the type of App )  
   7.2 Performance? --- ( Right Sizing )  
   7.3 Dependencies? --- ( Grouping all the related service including monitoring )  
   7.4 App Value? --- ( Target Service )  
8. Asses:  
   8.1 Understand the type of App  
   8.2 Right Sizing  
   8.3 Grouping  
   8.4 Target Service  
9. Migrate  
   9.1 Plan ( Test Migration / Fail Back / Online/OffLine / Downtime / Notification / Intimation / Collaboration / Chnage Plan / CR's )  
   9.2 Migrate  
10. Optimize   

</b></details>


<details>
<summary> 1.8 What are 5R's Migration strategy? </summary><br><b>


5R's
1. Rehost - No Code Change ( life time of an App, if it's not stratigic App then rehost )
2. Refactor ( PAAS ) - No Code Changing
3. Re-archietect - ( Changing DB, Code change, changing my application, shift to vm based app to container / Servreless etc )
4. Rebuild - ( To many changes then - Build from Scratch )
5. Replace
5R's Based on Effor level ( Low/Midium/high )
   
</b></details>

<details>
<summary>1.6 DataCenter Migration Diagram to Azure? </summary><br><b>
Summary
RTO tells you how long you can afford for your system to be down.
RPO tells you how much data loss is tolerable if a failure happens.

<img width="1500" height="1000" alt="image" src="https://github.com/user-attachments/assets/c711af62-f5da-413e-bf07-edaa2760fc26" />
<img width="740" height="338" alt="Screenshot 2025-08-13 at 1 14 02 AM" src="https://github.com/user-attachments/assets/8cbd6e18-e646-4aed-9f47-640b400d6e7f" />

Windows Virtual Desktop
Azure VMWare Service
Azure Kubernetes Service

</b></details>


<details>
<summary>1.6 Windows Virtual Desktop? </summary><br><b>

  
Windows Virtual Desktop, now known as Azure Virtual Desktop (AVD), is a comprehensive cloud-based desktop and application virtualization service provided by Microsoft on the Azure platform. It lets organizations securely deliver virtualized Windows desktops and remote applications to users anywhere, leveraging the scalability and reliability of Azure cloud infrastructure.

Key Features
Multi-Session & Single-Session: Run multiple user sessions on a single Windows 11 or Windows 10 Enterprise VM (exclusive in Azure), optimizing costs and resource usage. Alternatively, you can provide single-user desktops for a personal experience.

Full Desktop or Apps: Publish entire desktops or individual apps (RemoteApps) to users, depending on organizational needs.

Broad Device Support: Access virtual desktops from almost any device via Remote Desktop clients or web browsers, including Windows, Mac, iOS, Android, and even thin clients.

Simplified Management: Centralized, unified management for deploying desktops, apps, and updates; scalable configuration without running on-premises gateways or brokers.

Optimized for Microsoft 365: Enhanced experience and performance for Microsoft 365 Apps for enterprise in multi-user scenarios.

Hybrid & On-Prem Integration: Supports hybrid environments to connect on-premises infrastructure with Azure-based virtual desktops.

Security: Secure connections (TLS), integration with Azure Active Directory, multi-factor authentication, and management of user roles and access.

Cost Management: Pay-as-you-go pricing for consumed Azure VM and storage resources; autoscale features to match user demand and control costs.

How Windows/Azure Virtual Desktop Works
Deployment: Set up host pools (collections of Azure VMs) that serve as session hosts for virtual desktops and apps.

User Authentication: Uses Azure Active Directory (AAD) for authentication and authorization.

Connection: Users log in from any supported device and connect via secure Remote Desktop Protocol (RDP) sessions to their virtual desktops or apps.

Session Management: Supports both persistent (personal) and non-persistent (pooled) desktop experiences to suit different user profiles and business needs.

Monitoring and Scaling: Integrated tools for monitoring usage, health, and performance, plus built-in auto-scaling for maximum efficiency.

Common Use Cases
Remote workforce enablement

BYOD (Bring Your Own Device) scenarios

Secure access for contractors/third parties

Disaster recovery and business continuity

Legacy application hosting and modernization

Advantages
Rapid deployment and scaling of desktop environments

Reduce hardware overhead and administrative burden

Native support for Windows 11/10 multi-session and legacy Windows Server applications

Easy integration with existing Microsoft licensing

In summary:
Azure (Windows) Virtual Desktop empowers organizations to deliver secure, scalable, and flexible Windows desktop experiences from the Azure cloud, supporting modern remote work, application compatibility, and efficient IT operations.

Related
How does Azure Virtual Desktop enhance remote desktop security and scalability
What are the cost benefits of using multi-session Windows 11 in Azure Virtual Desktop
How do Persistent and Non-Persistent WVD modes impact user experience and management
What are the main differences between Azure Virtual Desktop and Windows 365
How can I migrate existing RDS deployments to Azure Virtual Desktop efficiently

</b></details>

<details>
<summary>1.7 RTO Vs RPO? </summary><br><b>
  
<img width="1001" height="471" alt="image" src="https://github.com/user-attachments/assets/7f651290-1908-4b8d-804e-b12b855ec80a" />

</b></details>

## Kubernetes

<a name="Kubernetes Interview"></a>

<details>
<summary>1.1 - what is Kubernetes Operator and how does it works?</summary><br><b>

A Kubernetes Operator is a powerful mechanism to automate application-specific operations in clusters, making it easier to deploy, manage, and scale stateful or complex software on Kubernetes with the reliability and repeatability expected of cloud-native infrastructure.

Why Use Operators?
Declarative management: Interact with apps through familiar kubectl commands, just like built-in resources.

Consistency: Repeatable, automated operational workflows reduce human error.

Advanced automation: Handles both Day 1 (install/configure) and Day 2 (update/backup/restore) operations.

Key Concepts
Custom Resources (CRs) and CRDs: Operators introduce Custom Resource Definitions (CRDs), allowing you to define and manage custom application objects in your cluster, using standard Kubernetes APIs and tools.

Controller Logic: The operator runs a control loop, constantly monitoring the actual state of an application and its components in the cluster, and acting to reconcile it with the desired state specified in the custom resource.

Automation: Operators can automate complex tasks such as installation, configuration, upgrades, scaling, backups, restoration, failure recovery, and even custom workflows for stateful applications.

Extensibility: They allow you to extend Kubernetes beyond built-in resources, packaging domain-specific knowledge for managing sophisticated software systems (e.g., databases, queues, monitoring systems) as if each were a first-class Kubernetes object.

Example Use Cases
Auto-deploying and scaling databases like PostgreSQL or MongoDB.

Orchestrating periodic backups and handling disaster recovery.

Rolling out software upgrades and schema migrations safely.
</b></details>

<details>
<summary>1.1 - Kubernetes Services, Explain each?</summary><br><b>
In Kubernetes, a Service is a fundamental concept that defines a logical set of Pods and a policy for accessing them. Pods are ephemeral, meaning they can be created, destroyed, and replaced at any time, leading to a constant change in their IP addresses. A Service provides a stable, persistent network endpoint (a stable IP address and DNS name) that other applications can use to communicate with the Pods, regardless of their individual IP addresses.

Here are the main types of Kubernetes Services:

1. ClusterIP (Default)
Definition: This is the default and most common Service type. It exposes the Service on a cluster-internal IP address.

Access: The Service is only reachable from within the Kubernetes cluster. It is not accessible from the outside.

Use Case: Ideal for internal communication between different components of your application, such as a frontend talking to a backend service.

2. NodePort
Definition: This type of Service exposes the application on a static port on each Node's IP address.

Access: The Service is accessible from outside the cluster by connecting to any of the cluster Nodes on the specified NodePort (e.g., NodeIP:NodePort).

Use Case: Useful for simple external access to your application, especially in development or testing environments, or when you want to use your own load balancer.

3. LoadBalancer
Definition: This Service type is an extension of NodePort. It provisions an external load balancer from a supported cloud provider (like AWS, GCP, or Azure) and assigns a public IP address to the Service.

Access: External clients can access the Service using the public IP address provided by the cloud provider's load balancer. The traffic is then routed to the Pods.

Use Case: The most common way to expose an application to the internet in a production environment, as it provides high availability and traffic distribution.

4. ExternalName
Definition: An ExternalName Service maps a Service to a DNS name. It does not create any proxying, load balancing, or internal IP address.

Access: When a client in the cluster makes a request to the Service's DNS name, the Kubernetes DNS service returns a CNAME record to the external name.

Use Case: Used to provide a simple, internal alias for an external service (e.g., a database running outside the cluster or a service in a different namespace).

5. Headless
Definition: A "headless" Service is a special case of a Service that does not get a stable ClusterIP.

Access: Instead of a single ClusterIP, the Kubernetes DNS service returns the IP addresses of all the Pods that the Service selects. This allows clients to connect directly to the Pods.

Use Case: Useful for stateful applications or when you need direct control over which Pod to connect to, such as for a database cluster where each replica needs to be addressed individually.
</b></details>

<details>
  
<summary>1.1 - Karpentar Vs Cluster Auto Scaller?</summary><br><b>

Cluster autoscaller 
Pods (VPA + HPA declaired full) -> Call API of auto-scaller Pool -> Node Pool -> Instance Service (EC2) --- Conclussion Time Consuming

Karpentar
Pods (VPA + HPA declaired full) -> Call API Instance Service (EC2) --- Conclussion Time saver than Cluster AutoScaller

Cluster Autoscaller always need same configuration EC2 Instance
where as in Karpenter we can call any size of EC2 instatance into Kubernetes Cluster Pool.

Karpentar provides prometheus metrics hence it;s provide certain level of visibility. 

Karpentar deployed several CRDsfrom it's Helm

NodeClass
- EC2NodeClass - AWS - To Map each Node in NodePool available in the each Node Porovide.
- AKSNodeClass - Azure 
- ECSNodeClass - Alibaba
NodePool - is refereing to NodeClass allwing Karpenter to doing task properly
- It has certain level of config for kubelet how should it behave refering maximum number pods or restrict resource size etc.
- But most important it help to create NodePool on which define its type of Nodes we are looking for depending on NodePool Node.
NodeClaim - 
- Karpenter will create or delete the Node depending on the demand by Pod or the Cluster.
- Karpenter Pod (demand) -> NodeClaim -> Karpenter -> EC2 -> Karpenter -> Node (Update) 
Karpenter will disrupt Node depending on "Epmty" / "UnderUtilize" / "Drifted"

Ref: https://www.youtube.com/watch?v=THj__UYiq90

</b></details>

 
## GiHub Action

<a name="GitHub Action"></a>

<details>

<summary>1.1 - The key components of GitHub Actions?</summary><br><b>

Workflow: A workflow is a YAML-defined automated process stored in the .github/workflows/ directory of your repository. It consists of one or more jobs and can be triggered by specific events (like push, pull_request), manually, or on a schedule. Multiple workflows can exist per repository, each handling different automation tasks.

Event (Trigger): An event is any activity that occurs in your repository, such as a code push, pull request, issue creation, or a scheduled timer. Events are what initiate (trigger) the workflows.

Job: A job is a set of steps that run in the same environment (runner), either sequentially or in parallel with other jobs. Jobs can be dependent on each other or run independently, providing workflow flexibility.

Step: Steps are individual tasks or command executions within a job. Each step might run a shell script or invoke an action. Steps within a job share the same runner and environment, allowing them to pass data between each other.

Action: An action is a pre-built, reusable code package that performs a specific task within a workflow—for example, checking out your code, setting up Node.js, or sending notifications. Actions can be used from the GitHub Marketplace or custom-developed for your needs.

Runner: The runner is the machine (virtual or self-hosted) that executes the jobs in your workflows. GitHub provides hosted runners on Linux, Windows, and macOS, or you can configure your own self-hosted runners for custom needs.

Artifacts: Files or directories (such as build results, logs, or reports) created and uploaded at the end of a job/run, allowing you to access and use job outputs later in the pipeline.

Secrets: Encrypted environment variables (like API keys, tokens, passwords) that can be used securely within workflows. These are managed via GitHub’s settings and exposed only at runtime.

Together, these components enable the automation of build, test, deployment, and other software lifecycle tasks directly in your GitHub repository, with powerful flexibility and integration options.

Related
What are the core components that make up a GitHub Action workflow
How do jobs and steps interact within a GitHub Action
Why are reusable actions important for workflow efficiency
How do GitHub-hosted and self-hosted runners differ in executing workflows
What role does event triggering play in initiating a GitHub Action

</b></details>

## SRE's

<a name="SRE's"></a>

<details>

<summary>1.1 - Python OOPS?</summary><br><b>

Object-Oriented Programming (OOP) is a core concept in Python, and interview questions often revolve around its principles and practical application. Here's a breakdown of key topics you should be prepared to discuss:

1. The Four Pillars of OOP

Encapsulation: The concept of bundling data (attributes) and methods that operate on that data into a single unit (a class). It involves controlling access to the internal state of an object to prevent direct modification.

Inheritance: A mechanism for creating a new class (a subclass) from an existing class (a superclass). The subclass inherits the attributes and methods of the superclass, promoting code reuse.

Polymorphism: The ability of an object to take on many forms. In Python, this often refers to method overriding (a subclass providing its own implementation of a method defined in its superclass) or how a single operator (like +) can behave differently with different data types (e.g., adding numbers vs. concatenating strings).

Abstraction: The process of simplifying complex reality by modeling classes based on essential properties and behaviors, while hiding unnecessary details. This is often achieved using abstract classes and methods, which are meant to be subclassed and implemented.

</b></details>

## SRE's

<a name="SRE's"></a>

<details>

<summary>1.1 - SLA Vs SLOs Vs SLI?</summary><br><b>
1. SLA – Service Level Agreement
What it is: A formal, legally binding contract between a service provider and a customer that specifies measurable service commitments (e.g., 99.9% uptime, 1-hour ticket response, etc.) and the consequences if they’re not met (like service credits or penalties).

Audience: Customers, legal/business teams, service provider.

Implication: SLA violations usually result in financial or contractual penalties and affect trust.

2. SLO – Service Level Objective
What it is: A specific, measurable internal goal set by the service provider to help ensure SLA commitments are met. An SLO is generally a target percentage or threshold (e.g., “99.95% of requests in a month must complete under 300ms”).

Audience: Engineering/operations teams.

Implication: SLOs guide operations, reliability engineering, and trigger corrective actions when not met—no direct legal penalty, but often prompt process reviews or feature freezes.

3. SLI – Service Level Indicator
What it is: A quantitative metric or measure of service performance; it’s the actual value recorded (e.g., measured uptime for the past 30 days or average response time).

Audience: Technical/development teams, monitoring, and operations.

Implication: SLIs are the raw data points that show if SLO targets (and thus SLA obligations) are being met. For example, if SLO is 99.9% availability, SLI might record actual availability of 99.87% for last month.

<img width="739" height="347" alt="Screenshot 2025-08-13 at 1 14 15 AM" src="https://github.com/user-attachments/assets/ebecd80f-fc7e-4dc8-a170-8738f412aac7" />


