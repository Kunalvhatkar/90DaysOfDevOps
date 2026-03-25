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
