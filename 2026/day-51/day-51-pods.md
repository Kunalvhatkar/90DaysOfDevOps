# Day 51 – Kubernetes Manifests and Your First Pods

## Task 1: Create Your First Pod (Nginx)
Create a file called nginx-pod.yaml:
```
kind: Pod
apiVersion: v1

metadata:
    name: nginx-pod

spec:
    containers:
    - name: nginx
      image: nginx:latest
      ports:
      - containerPort: 80
```

Apply it: 

kubectl apply -f nginx-pod.yaml

<img width="1003" height="104" alt="image" src="https://github.com/user-attachments/assets/029dea92-ac7e-4d91-86c5-5f644014ca16" />

Verify:

kubectl get pods  

<img width="809" height="134" alt="image" src="https://github.com/user-attachments/assets/31a0acef-e4eb-4ede-9fbc-c588498e5c15" />

kubectl get pods -o wide  

<img width="1090" height="84" alt="image" src="https://github.com/user-attachments/assets/4aab0459-c599-468e-9ac7-5748febd611e" />

Detailed info about the pod
kubectl describe pod nginx-pod  

<img width="1090" height="504" alt="image" src="https://github.com/user-attachments/assets/49857eeb-f08c-42fc-b6af-8470f6a09c6a" />

<img width="1090" height="459" alt="image" src="https://github.com/user-attachments/assets/ae88878b-3845-42e7-9f8d-afc490c1dc11" />

Read the logs

kubectl logs nginx-pod  

<img width="1090" height="651" alt="image" src="https://github.com/user-attachments/assets/1483677f-6bad-44c9-93ca-ec49d122d339" />

Get a shell inside the container

kubectl exec -it nginx-pod -- /bin/bash

<img width="1090" height="121" alt="image" src="https://github.com/user-attachments/assets/ac800d8a-2727-4ce0-9c97-4574a2646d2f" />

Inside the container

run:  curl localhost:80 

<img width="1090" height="578" alt="image" src="https://github.com/user-attachments/assets/b308f183-85ec-4ecb-ba19-b1e9a6398bcb" />

exit  

<img width="725" height="140" alt="image" src="https://github.com/user-attachments/assets/515778e9-8a39-4ba3-a6bf-1b2bc24cf802" />

Port forward localhost port 8081 and pod port 80 and verify it on web browser localhost:8081

<img width="1090" height="111" alt="image" src="https://github.com/user-attachments/assets/9a0701e9-f76d-472b-ba95-df58d7743e81" />

Access localhost:8081 

<img width="1090" height="308" alt="image" src="https://github.com/user-attachments/assets/72d56d31-cfa1-4dec-8c97-13cf56fe6358" />

## Task 2: Create a Custom Pod (BusyBox)

Write a new manifest busybox-pod.yaml from scratch
```
kind: Pod
apiVersion: v1

metadata:
    name: busybox-pod
    labels:
       app: busybox
       environment: dev

spec:
    containers:
    - name: busybox
      image: busybox:latest
      command: ["sh", "-c", "echo Hello from Busybox && sleep 3600"]
```

Apply and verify:

kubectl apply -f busybox-pod.yaml

<img width="1090" height="184" alt="image" src="https://github.com/user-attachments/assets/ab9eee81-7e40-41f0-9497-3858844c934e" />

kubectl get pods

<img width="919" height="196" alt="image" src="https://github.com/user-attachments/assets/2efdf0be-0a47-4f4e-9379-3ff18c1d2f57" />

kubectl logs busybox-pod

<img width="1028" height="114" alt="image" src="https://github.com/user-attachments/assets/ffc290b8-96fd-47a4-97e0-caad29138979" />

## Task 3: Imperative vs Declarative

You have been using the declarative approach (writing YAML, then kubectl apply). Kubernetes also supports imperative commands:

Create a pod without a YAML file

kubectl run redis-pod --image=redis:latest  

<img width="1090" height="112" alt="image" src="https://github.com/user-attachments/assets/5e3693a5-2c64-416d-a4ac-97b90e212845" />

Check it

kubectl get pods 

<img width="790" height="225" alt="image" src="https://github.com/user-attachments/assets/1708b0c6-2a78-4966-bbec-46391a190270" />

Now extract the YAML that Kubernetes generated: 

kubectl get pod redis-pod -o yaml  

<img width="790" height="1158" alt="image" src="https://github.com/user-attachments/assets/28132e50-97b0-4d4b-b0e6-31d2dde75807" />

<img width="1090" height="965" alt="image" src="https://github.com/user-attachments/assets/ad212021-16ef-4629-aa95-e39fe9fc439f" />

<img width="765" height="521" alt="image" src="https://github.com/user-attachments/assets/b7ad9776-8a14-45e5-b77d-aa75cb19bda5" />

You can also use dry-run to generate YAML without creating anything:

kubectl run test-pod --image=nginx --dry-run=client -o yaml

<img width="1090" height="395" alt="image" src="https://github.com/user-attachments/assets/176662eb-69e4-4c27-bcd4-b5b9ffa299c6" />

## Task 4: Validate Before Applying

Before applying a manifest, you can validate it:
Check if the YAML is valid without actually creating the resource
kubectl apply -f nginx-pod.yaml --dry-run=client

<img width="1090" height="116" alt="image" src="https://github.com/user-attachments/assets/5074e2c8-c24b-4a41-9a0e-34d5f9132a10" />

Validate against the cluster's API (server-side validation)
kubectl apply -f nginx-pod.yaml --dry-run=server  

<img width="1090" height="93" alt="image" src="https://github.com/user-attachments/assets/c70902b1-8229-4921-88f8-1ae5b206be59" />

## Task 5: Pod Labels and Filtering

Labels are how Kubernetes organizes and selects resources. You added labels in your manifests — now use them:

List all pods with their labels
kubectl get pods --show-labels

<img width="1090" height="215" alt="image" src="https://github.com/user-attachments/assets/c35cb196-5f20-40cd-bf09-53f7cf410d03" />

Filter pods by label
kubectl get pods -l app=nginx  

<img width="1009" height="90" alt="image" src="https://github.com/user-attachments/assets/2244d584-a3af-4449-8757-c8548b4f5b34" />

kubectl get pods -l environment=dev

<img width="1083" height="141" alt="image" src="https://github.com/user-attachments/assets/2075819b-9174-4759-9c31-6d9cc79f0cde" />

Add a label to an existing pod
kubectl label pod nginx-pod environment=production 

<img width="1090" height="90" alt="image" src="https://github.com/user-attachments/assets/76a95bd1-414f-4d0b-a5f2-4cb845137ba8" />

Verify

kubectl get pods --show-labels  

<img width="1090" height="214" alt="image" src="https://github.com/user-attachments/assets/2d01c3aa-2fdd-44f0-adb1-baafe999d5e6" />

Remove a label

kubectl label pod nginx-pod environment- 

<img width="1090" height="253" alt="image" src="https://github.com/user-attachments/assets/ba3258d6-bd04-4e66-b4d8-a0c6a5687729" />


## Task 6: Clean Up

Delete all the pods you created:

Delete by name
kubectl delete pod nginx-pod  

<img width="984" height="96" alt="image" src="https://github.com/user-attachments/assets/64db8042-c3f9-49cb-8ef0-d9f4375a9909" />

kubectl delete pod busybox-pod  

<img width="971" height="96" alt="image" src="https://github.com/user-attachments/assets/171ff9a3-ebb3-43d1-9bf9-a5a47fb352f9" />

kubectl delete pod redis-pod 

<img width="950" height="96" alt="image" src="https://github.com/user-attachments/assets/ae7a844e-3ddb-4d0e-9ae4-3614239bbabe" />

delete using the manifest file

kubectl delete -f nginx-pod.yaml 

<img width="1029" height="109" alt="image" src="https://github.com/user-attachments/assets/3e023772-a80e-4200-8593-0475817d2359" />

