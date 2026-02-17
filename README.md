# lab-3

<img width="375" height="168" alt="image" src="https://github.com/user-attachments/assets/3231a68b-9089-4c1c-9444-f2a34172e9ff" />

1) auth list output & project config

<img width="951" height="637" alt="image" src="https://github.com/user-attachments/assets/5d6d34f0-6ddd-4b2c-a56d-4e0d73cb292f" />

2) Confirms I am authenticated to Google Cloud and my project is set correctly in the right zone. I also configured the compute zone so resources will be created in the right region.

3) <img width="896" height="328" alt="image" src="https://github.com/user-attachments/assets/d3f08717-39dc-4c59-a621-48d71083130b" />

I cloned the Google microservices repo which has the orders and products services that will be containerized and deployed to Kubernetes.

4)<img width="910" height="284" alt="image" src="https://github.com/user-attachments/assets/294ddfe7-0151-4bd8-a056-ac24296399a4" />

I enabled the Cloud Resource Manager API, Kubernetes Engine API, and Container Registry API. These are necessary for making and controlling the Kubernetes cluster and for building & storing container images. After enabling the Container API, I verified that it worked by listing the enabled services.

5) <img width="776" height="688" alt="image" src="https://github.com/user-attachments/assets/f412b8c7-fd18-41d2-9de2-c7d66298232b" />

The Project ID, email and Role was added/replaced successfully.

6)<img width="908" height="619" alt="image" src="https://github.com/user-attachments/assets/0a74be2d-3969-4d29-ae8b-e027d2e971de" />

I created a Google Kubernetes Engine (GKE) cluster named gke-cluster with three worker nodes. After the cluster was up & running, I configured kubectl access and got the cluster credentials. I made sure there was connectivity to the cluster by running kubectl get nodes, which showed all three nodes in the Ready state.

7) <img width="868" height="741" alt="image" src="https://github.com/user-attachments/assets/78d6139d-5da8-4958-a745-e3ec2d72e75e" />

I ran gcloud artifacts repositories list --location=us-east1 and was confused why it was showing "listed 0 items" and I ran tuo89020@cloudshell:~ (dotted-saga-484500-n2)$ gcloud artifacts repositories list to see where my Artifact Registry (called REPOSITORY: my-repository) was that I created in Lab 1 and was able to locate it in LOCATION: us-east4. After selecting the correct region I was able to proceed with the lab.

8) <img width="806" height="571" alt="image" src="https://github.com/user-attachments/assets/b78b27dd-c8df-49e1-b599-7c8acc5e4bac" />

The name of my repo was listed correctly in the registryUri.

9) <img width="897" height="170" alt="image" src="https://github.com/user-attachments/assets/b9a97e66-8af7-4229-93dc-763ada422d92" />

<img width="1238" height="631" alt="Screenshot 2026-02-15 145649" src="https://github.com/user-attachments/assets/05d3133c-c49f-465e-a3aa-044c76c6c4d4" />


<img width="744" height="206" alt="Screenshot 2026-02-15 145714" src="https://github.com/user-attachments/assets/a98eec77-65b5-460a-b47d-643366a0aa7f" />

From my home directory I was able to persist the registry path as an environment variable with my replaced and corrected region location with the environmental variable ART_REG verified.

10) Now I'm building the orders image:

<img width="806" height="283" alt="Screenshot 2026-02-15 192533" src="https://github.com/user-attachments/assets/922f4876-ce9f-4d88-bb53-a1e67eb98052" />

I used Google Cloud Build to build Docker images for both microservices and pushed them to Artifact Registry so Kubernetes could deploy them later.

11) Task 6 — Deploy products and orders to GKE using YAML manifests.
<img width="570" height="362" alt="image" src="https://github.com/user-attachments/assets/7d069e0d-3a7a-4735-a050-022b9890aa98" />

<img width="637" height="640" alt="image" src="https://github.com/user-attachments/assets/1091f37a-2c00-414a-9d93-b110e821db3e" />

I created a Kubernetes Deployment and Service for the products microservice using YAML files. There were 3 replicas so Kubernetes automatically runs three pods using the container image. The ClusterIP service allows internal communication within the cluster by mapping port 80 to the container port. kubectl apply, the pods initially showed as unavailable while starting, but soon all three were running successfully. I also deleted one pod to demonstrate Kubernetes self-healing, and the system automatically created a replacement pod.

12) Step 6 — Inspect Selectors and Confirm How the Service Binds to Pods
<img width="1835" height="796" alt="image" src="https://github.com/user-attachments/assets/2b58abf0-13b4-43f8-b5bc-c4953b40f8a9" />

The products pods are running and correctly labeled, and that the products-service is using the selector app=products to connect to those pods. Two temporary client pods (dns-client and http-client) were created to test communication inside the cluster. The DNS lookup confirms that the service name resolves to a ClusterIP address, and the curl request successfully retrieves product data from the API through the service. The Kubernetes service discovery and internal networking are working properly so the pods can communicate using the service name instead of individual pod IP addresses.

13) Task 7 — Quick Deployment and Testing of the orders Microservice (Repeat + Validate)
    <img width="889" height="799" alt="image" src="https://github.com/user-attachments/assets/322f18a9-7caf-4a39-b071-789c1ccc88bb" />

<img width="1021" height="788" alt="image" src="https://github.com/user-attachments/assets/8644c9bc-1239-400c-afcd-0b7f79a335bf" />

<img width="1845" height="355" alt="image" src="https://github.com/user-attachments/assets/4246fd22-e55f-426e-8742-26afea6aed85" />

Creation and deployment of the orders microservice in Kubernetes. An orders.yaml file was made containing both a Deployment with three replicas and a ClusterIP Service. After applying the configuration, the deployment successfully started with all pods running and assigned IP addresses. DNS testing from the dns-client pod confirmed that the service name resolves to a ClusterIP, and curl requests from the http-client pod successfully retrieved order data from the API. EndpointSlice correctly maps the service to the IP addresses of the running pods, showing internal networking and service discovery within the cluster.
