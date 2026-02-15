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

I ran 
