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
