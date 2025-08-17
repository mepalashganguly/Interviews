
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
  
<summary>Karpentar Vs Cluster Auto Scaller?</summary><br><b>

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

<details>
  
<summary>Flanel Vs Callico Vs Cillium?</summary><br><b>
<img width="1210" height="1124" alt="image" src="https://github.com/user-attachments/assets/c338dd2a-e1bf-4822-9582-a50caabe2310" />

</b></details>

<details>
<summary>K8s Operator?</summary><br><b>

Coming
</b></details>

<details>
<summary>K8s Logs for troubleshhoting?</summary><br><b>  
	
1. All manifest files: /etc/kubernetes/manifests    
2. cd /var/log/containers/ all logs
3. crictl ps -a  
4. crictl logs <container_id>  	

Cluster troubleshoot:
	1. kubectl get cm kubelet-config -n kube-system -o yaml | grep -i cidr  
	2. vi /etc/kubernetes/manifests/kube-controller-manager.yaml get cidr  
    3. kubectl get pods if any error regarding kubeapi server check /etc/kubernetes/manifests/kube-apiserver.yaml Any mismatch change "~/.kube/config" file and check  
	6. Check kubelet service with systemctl status kubelet  
	7. Etcd erro validate etcd manifest under /etc/kubernetes/manifests. Mismatch? Change /etc/kubernetes/manifests/kube-apiserver.yaml  
	8. Get all the listed enable service "systemctl list-unit-files" | grep -i kube  

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




