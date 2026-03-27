# Day 52 – Kubernetes Namespaces and Deployments

## Task 1: Explore Default Namespaces
    
    1.	kubectl get namespaces
    
  <img width="1090" height="261" alt="image" src="https://github.com/user-attachments/assets/ac105ad8-1ec7-4bc3-befc-5cfa6823b859" />

  •	default: This is the general-purpose namespace for objects that do not specify a namespace. For production clusters, it is generally recommended to avoid using the default namespace for your own workloads. where your resources go if you do not specify a namespace
  
  •	kube-system: This namespace is reserved for objects created by the Kubernetes system itself, such as the API server, scheduler, and controller manager. User resources should not be added here.
  
  •	kube-public: This namespace is readable by all clients, including unauthenticated ones. It is typically used for cluster-wide, publicly visible resources.
  
  •	kube-node-lease: This namespace holds Lease objects associated with each node, allowing the control plane to detect node failures quickly via heartbeats. 

  2. Check what is running inside kube-system:  kubectl get pods -n kube-system

     <img width="1090" height="350" alt="image" src="https://github.com/user-attachments/assets/2dbaa445-42b2-46f8-8eda-7aa2b04c8cd0" />

## Task 2: Create and Use Custom Namespaces

   1. Create two namespaces — one for a development environment and one for staging:

      kubectl create namespace dev

      <img width="921" height="103" alt="image" src="https://github.com/user-attachments/assets/f0c55e1e-acb1-468a-8950-18ebbd49d928" />

   2. kubectl create namespace staging

      <img width="1028" height="121" alt="image" src="https://github.com/user-attachments/assets/5cc84490-9a75-411f-a503-73da01842fbf" />

   3. Verify they exist: kubectl get namespaces

      <img width="809" height="325" alt="image" src="https://github.com/user-attachments/assets/e5cdc780-f293-45b1-bd9a-88bafdc35aed" />

   4. create a namespace from a manifest: namespace.yaml
      ```
      kind: Namespace
      apiVersion: v1
      metadata:
        name: production
      ```
   5. create namespace : kubectl apply -f namespace.yaml
      
  <img width="909" height="110" alt="image" src="https://github.com/user-attachments/assets/df8a10d9-4ce7-4c19-b38d-f940ad1cb6e8" />

   6. Verify: kubectl get namespace

      <img width="796" height="315" alt="image" src="https://github.com/user-attachments/assets/477e4486-c2d3-47f6-8e22-68da2a9c2bf1" />

   7. run a pod in a specific namespace:
      
      a. kubectl run nginx-dev --image=nginx:lattest -n dev

      <img width="1090" height="87" alt="image" src="https://github.com/user-attachments/assets/485d1662-e037-4bf0-a626-3a5a2ce793f7" />

      b. kubectl run nginx-staging --image=nginx:latest -n staging

      <img width="1090" height="88" alt="image" src="https://github.com/user-attachments/assets/832ac3d2-7653-4459-8c63-0f56e88a7301" />

    8. List pods across all namespaces: kubectl get pods -A
     
  <img width="1090" height="356" alt="image" src="https://github.com/user-attachments/assets/76f60d40-2007-4319-b3ec-fa18d08d4724" />

    9. Does kubectl get pods show these pods? What about kubectl get pods -A?
  Ans: kubectl get pods shows pods in default namespace. kubectl get pods -A show pods in all namespaces 

## Task 3: Create Your First Deployment

A Deployment tells Kubernetes: "I want X replicas of this Pod running at all times." If a Pod crashes, the Deployment controller recreates it automatically.
```
nginx-deployment.yaml
kind: Deployment
apiVersion: apps/v1
metadata: 
      name: nginx-deployment
      namespace: dev
      labels:
        app: nginx
spec:
    replicas: 3
    selector:
       matchLabels:
          app: nginx
    template:
       metadata: 
          labels:
              app: nginx
       spec:
           containers:
           - name: nginx
             image: nginx:1.24
             ports: 
             - containerPort: 80
```

Apply it: kubectl apply -f nginx-deployment.yaml

<img width="1090" height="114" alt="image" src="https://github.com/user-attachments/assets/b55818c2-f3fd-4302-af80-77942cd1018d" />

Check the result:
kubectl get deployments -n dev  

<img width="988" height="139" alt="image" src="https://github.com/user-attachments/assets/e5e38757-60b1-4f9d-8bfb-2230895cb694" />

kubectl get pods -n dev  

<img width="1090" height="219" alt="image" src="https://github.com/user-attachments/assets/384888d9-12e8-4cbd-923c-5050f717797a" />

## Task 4: Self-Healing — Delete a Pod and Watch It Come Back

1. List pods: kubectl get pods -n dev

   <img width="1090" height="227" alt="image" src="https://github.com/user-attachments/assets/c1fd6d89-9167-46ea-8849-bb07ef03b45a" />

2. Delete one of the deployment's pods (use an actual pod name from your output): kubectl delete pod <pod-name> -n dev
3. Immediately check again: kubectl get pods -n dev

   <img width="1090" height="349" alt="image" src="https://github.com/user-attachments/assets/4b8b1ce0-4b6d-4767-9fb2-49508213debb" />

The Deployment controller detects that only 2 of 3 desired replicas exist and immediately creates a new one. The deleted pod is replaced within seconds.

Verify: Is the replacement pod's name the same as the one you deleted, or different?
Ans: replacement pod name is different from deleted pod.

## Task 5: Scale the Deployment

1. Scale up to 5: kubectl scale deployment nginx-deployment --replicas=5 -n dev
  check: kubectl get pods -n dev
 
 <img width="1090" height="361" alt="image" src="https://github.com/user-attachments/assets/9585b0d4-e59a-41ce-915f-ae004a3aad86" />

2. Scale down to 2: kubectl scale deployment nginx-deployment --replicas=2 -n dev
   check: kubectl get pods -n dev

   <img width="1090" height="359" alt="image" src="https://github.com/user-attachments/assets/05247ded-1722-41fb-8fd0-ad7c7476b0b0" />

3. scale by editing the manifest — change replicas: 4 in your YAML file and run kubectl apply -f nginx-deployment.yaml again

   <img width="1090" height="415" alt="image" src="https://github.com/user-attachments/assets/79ffa28c-cfe1-4675-8cb8-0ec74c5f6b4a" />

Verify: When you scaled down from 5 to 2, what happened to the extra pods?
Ans: extra three pods are deleted automatically.

## Task 6: Rolling Update

1.	Update the Nginx image version to trigger a rolling update:
    kubectl set image deployment/nginx-deployment nginx=nginx:1.25 -n dev

    <img width="1090" height="42" alt="image" src="https://github.com/user-attachments/assets/94354f69-0815-40b8-aa40-d348fa4746cb" />

2. Watch the rollout in real time:  
   kubectl rollout status deployment/nginx-deployment -n dev

   <img width="1016" height="321" alt="image" src="https://github.com/user-attachments/assets/cb0a432a-d5ac-48c2-a3ff-050663449404" />

   Kubernetes replaces pods one by one — old pods are terminated only after new ones are healthy. This means zero downtime.

3.	Check the rollout history: 
    kubectl rollout history deployment/nginx-deployment -n dev

   <img width="1056" height="125" alt="image" src="https://github.com/user-attachments/assets/6e8d0fb1-519e-4227-9e72-ee80ddb40ccc" />

4.	Now roll back to the previous version:
    kubectl rollout undo deployment/nginx-deployment -n dev

    Verify: kubectl rollout status deployment/nginx-deployment -n dev

    <img width="1056" height="137" alt="image" src="https://github.com/user-attachments/assets/ef9afca8-8775-43dd-8049-ddf34ee4fb00" />

5. Verify the image is back to the previous version:
   kubectl describe deployment nginx-deployment -n dev | grep Image (for linux)
   kubectl describe deployment nginx-deployment -n dev | findstr Image (for windows)

   <img width="1002" height="84" alt="image" src="https://github.com/user-attachments/assets/c1706879-1bb1-481b-914b-ee6ef25f2854" />

What image version is running after the rollback?
Ans: nginx:1.24

## Task 7: Clean Up

1. kubectl delete deployment nginx-deployment -n dev

   <img width="1090" height="59" alt="image" src="https://github.com/user-attachments/assets/7d517e66-87af-4e90-b2cd-66e9da9057dc" />

3. kubectl delete pod nginx-dev -n dev
   
   <img width="998" height="64" alt="image" src="https://github.com/user-attachments/assets/628d4053-dfff-4c62-aaf1-551b914aec6e" />

5. kubectl delete pod nginx-staging -n staging

   <img width="1090" height="61" alt="image" src="https://github.com/user-attachments/assets/c8fabdfe-3706-4efa-9f83-3de22856dba6" />

7. kubectl delete namespace dev staging production

   <img width="1090" height="160" alt="image" src="https://github.com/user-attachments/assets/a8869c1d-2f9c-4fa8-a267-6d2c392d09ed" />

9. kubectl get namespaces

    <img width="860" height="209" alt="image" src="https://github.com/user-attachments/assets/9ade94ba-9c9b-46cc-81ae-d5939543ca4d" />

11. kubectl get pods -A

    <img width="1090" height="314" alt="image" src="https://github.com/user-attachments/assets/ebdfa875-3045-4c1e-91ad-9796e6751d40" />
