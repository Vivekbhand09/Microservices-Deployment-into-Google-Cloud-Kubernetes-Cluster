## ☁️ Deploying EazyBank Microservices on Google Cloud (GKE)

In this section, I deployed my **EazyBank microservices project** to a cloud provider.  
I chose **Google Cloud Platform (GCP)** because it provides a **$300 free tier credit** that can be used within **90 days**, which is sufficient to explore and deploy real-world cloud-native applications.

For container orchestration on the cloud, I used **Google Kubernetes Engine (GKE)**.

---

## 🔹 High-Level Deployment Flow

1. Build Docker images for all microservices.
2. Push all Docker images to **Docker Hub**.
3. Set up a **Google Cloud account** and project.
4. Create a **GKE Kubernetes cluster**.
5. Connect local system to GKE using **Cloud SDK**.
6. Deploy Kubernetes manifests to the cloud cluster.
7. Verify services and test APIs using cloud endpoints.

---

## 🔹 Google Cloud Account & Project Setup

- First, I visited the **Google Cloud website**.
- Navigated to **Google Kubernetes Engine** and opened the **Console**.
- Clicked on **Try for Free**.
- Filled in required account and billing information.
- After successful setup, I was redirected to the **GCP Dashboard**, where the **$300 free credits** were visible.
- I created a **new GCP project**, which acts as a container for all cloud resources like clusters, services, and networking.

---

## 🔹 Installing Google Cloud SDK (CLI Setup)

To communicate with Google Cloud from my local system, I installed the **Google Cloud SDK**.

Steps:
- Went to the **Cloud SDK – Get Started** page.
- Downloaded and installed the SDK on my local system.
- Verified installation using:

```bash
gcloud --version
```

- Initialized the CLI:

```bash
gcloud init
```

- Logged in using my Google account.
- Selected the created GCP project during initialization.

This setup allows my local `kubectl` and `gcloud` commands to interact with GCP resources.

---

## 🔹 Enabling Kubernetes Engine & Creating GKE Cluster

- From the **Google Cloud Dashboard**, I searched for **Kubernetes Engine**.
- Enabled the **Kubernetes Engine API**.
- Clicked **Create Cluster**.
- Switched to **Standard Cluster**.
- Configured basic cluster settings and created the cluster.

Once the cluster was created:
- Clicked on the **three-dot menu** → **Connect**.
- Copied the provided command and pasted it into my local CLI.

This command established a connection between my local system and the GKE cluster.

To validate the connection:

```bash
kubectl get nodes
```

This confirmed that the Kubernetes cluster was reachable and ready.

---

## 🔹 Deploying Microservices to GKE

After connecting to the cluster:
- I updated all Kubernetes manifest files to be cloud-ready.
- Deployed services using:

```bash
kubectl apply -f accounts.yml
```

- Repeated the same for all other Kubernetes manifest files (loans, cards, gateway, configs, etc.).

Once applied:
- All microservices were successfully deployed on **Google Kubernetes Engine**.
- Kubernetes automatically created pods, services, and networking resources.

---

## 🔹 Accessing & Testing Cloud-Deployed Services

- From the **Services & Ingress** section in GKE:
  - Retrieved external endpoints for the deployed services.
- Used these endpoints to access microservices from outside the cluster.
- Tested APIs using **Postman**:
  - Created Accounts, Cards, and Loans.
  - Invoked the `fetchCustomer` API via **Gateway Service**.
  - Received a successful aggregated response from all services.

This confirmed that:
- Services were running correctly on GCP.
- Inter-service communication was working as expected.
- Gateway routing and cloud networking were properly configured.

---

## 📸 Screenshots (utils folder)

I captured screenshots for the entire deployment flow and stored them in the `utils` folder:

- **gcp1** – GCP Dashboard showing free tier credits  
- **gcp2** – Selecting Google Kubernetes Engine  
- **gcp3** – Account setup completed and project created  
- **gcp4** – Cloud SDK installation and local setup  
- **gcp5** – Kubernetes cluster creation  
- **gcp6** – All microservices deployed successfully on GKE  
- **gcp7** – Services & Ingress tab showing endpoints  
- **gcp8** – Successful API testing via Postman using GCP endpoint  

---

## 🔹 Key Takeaway

This deployment demonstrates how a **local Kubernetes-based microservices project** can be seamlessly migrated to a **cloud-managed Kubernetes platform (GKE)**, achieving scalability, reliability, and real-world production readiness.
