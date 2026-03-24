# Day 50 – Kubernetes Architecture and Cluster Setup

## Task 1: Recall the Kubernetes Story

1.	Why was Kubernetes created? What problem does it solve that Docker alone cannot?
Answer :
   Kubernetes was created by Google to manage containerized applications at massive scale, building on their internal system called Borg.
   Docker is a platform for building and running individual containers, Kubernetes solves the problem of orchestrating and managing a fleet of containers across a cluster of machines in a production environment.

2.	Who created Kubernetes and what was it inspired by?
Ans: 
  Kubernetes was created by Google in 2014.It was inspired by Google’s internal system called Borg.

3.	What does the name "Kubernetes" mean?
Ans: 
"Kubernetes" comes from Greek. It means: “Helmsman” or “Ship Pilot”

## Task 2: Draw the Kubernetes Architecture
### Kubernetes Architecture : 
   <img width="1090" height="568" alt="image" src="https://github.com/user-attachments/assets/fc464829-2334-487a-9af9-17a102340cbc" />

#### Kubernetes Architecture: 
follows a client-server model consisting of a Control Plane (master nodes) that manages and orchestrates the system, and Worker Nodes (data plane) where the actual containerized applications run.

#### Control Plane (Master Node):  
The control plane is the "brain" of the Kubernetes cluster. makes global decisions about the cluster, such as scheduling and managing the desired state.

a.	API Server (kube-apiserver): The front-end of the control plane that exposes the Kubernetes API. All internal and external communication goes through it, and it validates requests and updates the cluster state in etcd.

b.	etcd: A consistent and highly-available key-value store that acts as the single source of truth for all cluster data, state, and configuration.

c.	Scheduler (kube-scheduler): Watches for new pods and assigns them to an appropriate healthy worker node based on resource requirements, constraints, and available capacity.

d.	Controller Manager (kube-controller-manager): A daemon that runs core control loops to continuously compare the cluster's current state with its desired state. It includes several controllers, such as the Node Controller (monitors node health) and Replication Controller (ensures the correct number of pods are running).

#### Worker Nodes:  
Worker nodes are the machines (virtual or physical) that run the containerized applications.

a.	Kubelet: An agent that runs on each node and ensures that the containers within a pod are running and healthy as specified by the control plane.

b.	Kube-proxy: A network proxy that runs on each node, maintaining network rules and facilitating communication between pods and services both inside and outside the cluster.

c.	Container Runtime: The underlying software responsible for running the containers, such as containerd or CRI-O (Docker was a common legacy runtime).


## Task 3: Install kubectl
Install Kubectl in windows: 

1.	curl.exe -LO https://dl.k8s.io/release/v1.35.0/bin/windows/amd64/kubectl.exe
   <img width="990" height="115" alt="image" src="https://github.com/user-attachments/assets/2a6f4a05-3906-46d3-9a4f-463a00eefafd" />

2.	Validate the binary (optional)
   Download the kubectl checksum file:  
   curl.exe -LO https://dl.k8s.io/v1.35.0/bin/windows/amd64/kubectl.exe.sha256
  <img width="1090" height="116" alt="image" src="https://github.com/user-attachments/assets/bb2b91ce-cb57-41d4-a81b-0e54cc99df3d" />

3.	Validate the kubectl binary against the checksum file:
    Using Command Prompt to manually compare CertUtil's output to the checksum file downloaded:  
    CertUtil -hashfile kubectl.exe SHA256
    type kubectl.exe.sha256
  	<img width="1029" height="234" alt="image" src="https://github.com/user-attachments/assets/b939b856-a9bd-4c49-8e62-cf9581c197bd" />

4.	Using PowerShell to automate the verification using the -eq operator to get a True or False result:   
    $(Get-FileHash -Algorithm SHA256 .\kubectl.exe).Hash -eq $(Get-Content .\kubectl.exe.sha256)
  	<img width="1090" height="64" alt="image" src="https://github.com/user-attachments/assets/191ed0d2-c654-450b-8159-9598b7c2a203" />

5.	Test to ensure the version of kubectl is the same as downloaded:  kubectl version --client
    <img width="723" height="129" alt="image" src="https://github.com/user-attachments/assets/7ebb684f-6ad3-402e-9f0b-a8da88421bf7" />

## Task 4: Set Up Your Local Cluster
Install kind in Windows (Kubernetes in Docker)
1. curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.31.0/kind-windows-amd64
   <img width="1056" height="111" alt="image" src="https://github.com/user-attachments/assets/9a9fd12a-3d9d-4371-9694-80acbdb558b1" />

2.	Create folder in C: name kind for move kind.exe file on this folder.
   <img width="1051" height="601" alt="image" src="https://github.com/user-attachments/assets/476e1ff6-fb7d-4eed-a29f-bcdcead135e8" />

3.	Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe
   <img width="1029" height="61" alt="image" src="https://github.com/user-attachments/assets/9e923d87-197d-490b-988e-d5225c0b0535" />

4.	Set Path Environment in windows: 

Step1:   
<img width="641" height="378" alt="image" src="https://github.com/user-attachments/assets/ddbf63a3-3841-42a8-b2ba-a242b9e75450" />

Step2:  set environment Path  
<img width="703" height="563" alt="image" src="https://github.com/user-attachments/assets/2b116398-d88d-4272-b55e-e997c10a3429" />

Step3:  
<img width="890" height="620" alt="image" src="https://github.com/user-attachments/assets/235d69fc-24f3-4609-bfa9-ad71e06ee9e5" />

Step4: Copy kind.exe file path in path variable
<img width="750" height="666" alt="image" src="https://github.com/user-attachments/assets/31922ff0-449e-450b-bd1c-53a51e2d565c" />

Step5: Verify kind:  
<img width="484" height="76" alt="image" src="https://github.com/user-attachments/assets/9f811f35-b160-4e5a-9e05-2ab8f438fb64" />

## First Local Cluster: Cluster-config.yml 
 ```
1.	kind: Cluster
2.	
3.	apiVersion: kind.x-k8s.io/v1alpha4
4.	
5.	name: kindcluster
6.	
7.	nodes: 
8.	# three node (two workers) cluster config
9.	- role: control-plane
10.	  image: kindest/node:v1.35.0
11.	
12.	- role: worker
13.	  image: kindest/node:v1.35.0
14.	
15.	- role: worker
16.	  image: kindest/node:v1.35.0
 ```
## create cluster: kind create cluster –config <yml file name> 
<img width="1090" height="443" alt="image" src="https://github.com/user-attachments/assets/2f407e5b-4ead-4b0f-9c0e-bdc0acb698a0" />

## Task 5: Explore Your Cluster
1.	kubectl cluster-info
   <img width="1090" height="163" alt="image" src="https://github.com/user-attachments/assets/b51797ed-09ab-44cc-af97-ec85d6a639f2" />

2. kubectl get nodes
  <img width="1090" height="182" alt="image" src="https://github.com/user-attachments/assets/1c3c886c-4ef4-4718-8c2f-6f87b0a2d534" />

3.	kubectl describe node <node-name>
<img width="1090" height="539" alt="image" src="https://github.com/user-attachments/assets/f2a016c3-9525-4c9b-a857-8d794baca367" />
<img width="1090" height="541" alt="image" src="https://github.com/user-attachments/assets/0a7e4572-983d-4667-9c84-1c02b30593c6" />

4.	kubectl get namespaces
   <img width="794" height="253" alt="image" src="https://github.com/user-attachments/assets/f5d85c4b-f385-4014-8d42-80f0fde1930e" />

5.	kubectl get pods -A
   <img width="1090" height="313" alt="image" src="https://github.com/user-attachments/assets/10eba9be-d36a-459e-a478-89cf0783037d" />

6.	kubectl cluster-info --context kind-kindcluster
   <img width="1090" height="127" alt="image" src="https://github.com/user-attachments/assets/5f9eaf6a-7b3d-4a22-9328-22aa91467295" />

## Task 6: Practice Cluster Lifecycle

1. Delete cluster
kind delete cluster --name devops-cluster
<img width="1090" height="102" alt="image" src="https://github.com/user-attachments/assets/9c7a720e-b0ef-48a4-92a0-0fe5e260c17c" />

2. Recreate Cluster:
   kind create cluster --name <cluster-name>
   <img width="1090" height="356" alt="image" src="https://github.com/user-attachments/assets/b2449102-f1fd-42b0-8203-9fc5ed87766c" />

3. Verify Cluster
   kubectl get nodes   
   <img width="921" height="141" alt="image" src="https://github.com/user-attachments/assets/7674518e-3d5b-4e41-959f-b62d7ffd974e" />

4. Check which cluster kubectl is connected to
   kubectl config current-context
   <img width="784" height="96" alt="image" src="https://github.com/user-attachments/assets/10843c31-f4f3-4cef-9b0e-838f3f843a7a" />

5. List all available contexts (clusters)
   kubectl config get-contexts
   <img width="1028" height="116" alt="image" src="https://github.com/user-attachments/assets/4a4193a7-2a98-4ae3-8f0a-771f4a37b143" />

6. See the full kubeconfig
   kubectl config view
   <img width="709" height="526" alt="image" src="https://github.com/user-attachments/assets/5d87527a-7568-4408-954f-1120336148c7" />

## What is a kubeconfig? 
A kubeconfig file is a YAML-formatted configuration file that stores authentication, cluster, and user information required by kubectl to connect to one or more Kubernetes clusters.
