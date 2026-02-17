# Graded-Project-on-Orchestration-and-Scaling-Assignment
“The MERN application was containerized using Docker, CI was implemented using Jenkins, images were pushed to Amazon ECR, and the application was deployed on Amazon EKS using Helm charts. The backend service was exposed via a Load Balancer and verified through external access.”

## Project Objective

The objective of this project is to:

Containerize a MERN-based application

Implement CI using Jenkins

Store Docker images in Amazon ECR

Deploy the application on Amazon EKS using Helm

Expose the application publicly using Kubernetes LoadBalancer

## Tools & Technologies Used

Git & GitHub – Version control

Docker – Containerization

Jenkins – Continuous Integration (CI)

AWS CLI – AWS access & authentication

Amazon ECR – Docker image repository

Amazon EKS – Kubernetes cluster

Helm – Kubernetes package manager

kubectl – Kubernetes CLI

## Step 1: Version Control with Git
Forked the main repository:
https://github.com/UnpredictablePrashant/StreamingApp.git
![streamingApp repo forked snapshot](https://github.com/user-attachments/assets/7809821b-28bf-42fc-b035-d444436134c6)

## Created my own working repository on GitHub
   Used Git to commit and push all changes
git clone <my-forked-repo>
git add .
git commit -m "Initial setup"
git push origin main
![1- Cloning git Repo snapshot](https://github.com/user-attachments/assets/73c59b23-79e2-4bc2-9025-e999c2c88ae6)
## Version control successfully implemented.

## Step 2: Dockerizing the Application
Created separate Dockerfiles for backend services
Used Node.js base image
Ensured application listens on 0.0.0.0 for Kubernetes compatibility
Docker build command: docker build -t streaming-chat-backend .
![7-Docker images pushed snapshot](https://github.com/user-attachments/assets/7a7a3995-e38d-4a4a-bd2f-10f2dfc9115f)
Application successfully containerized.

## Step 3: Amazon ECR (Elastic Container Registry)
Created ECR repositories for backend images
Logged into ECR using AWS CLI
Tagged and pushed Docker images
Commands used: aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <account-id>.dkr.ecr.us-east-1.amazonaws.com
docker tag streaming-chat-backend:latest <ecr-repo-url>:latest
docker push <ecr-repo-url>:latest
![5-ECR and Nginx logged in Snapshot](https://github.com/user-attachments/assets/c2a3503e-5a7f-4fae-aeb8-7bcd1b722b14)
![6-ECR local image Snapshot](https://github.com/user-attachments/assets/6d307ed8-7c6b-4c6d-983d-ab8edfbb261d)
![8-AWS Console ECR images created snaphot](https://github.com/user-attachments/assets/3a6e4d83-b992-46ab-8742-a2338fbff5eb)
## Images successfully pushed to ECR

## Step 4: AWS CLI Setup 
Installed AWS CLI v2
Configured IAM user credentials
Command used: aws sts get-caller-identity
![17-Iam New polices for EKS cluster snapshot](https://github.com/user-attachments/assets/006aa387-cd8c-4603-b6d2-049a5488ee6d)
![16- AWS k8s policies snapshot](https://github.com/user-attachments/assets/605ce2bd-04c4-457b-bd7d-40385fd11c54)
![streamingapp Ec-2 instance 1 snapshot](https://github.com/user-attachments/assets/62277ce5-2ce8-4492-96bf-5e06d4783524)
![streamingapp Ec-2 instance 2 snapshot](https://github.com/user-attachments/assets/e9f34a9e-3c79-4b45-8f50-84a023a890f0)
AWS CLI configured successfully.

## Step 5: Jenkins CI Pipeline
Jenkins installed on AWS EC2 instance
Jenkins pipeline created
Clone GitHub repository
Build Docker images
Push images to Amazon ECR
Pipeline executed successfully
![9-EC2 Jenkins Server snapshot](https://github.com/user-attachments/assets/dbe898a8-27b2-44e2-8bfa-77ea98e1f6f5)
![9-EC2 Jenkins login page snapshot](https://github.com/user-attachments/assets/c3723295-f2d0-4309-b506-7b2029440af8)
![10-Jenkins Instance configuration snapshot](https://github.com/user-attachments/assets/a2b1ac29-bc8f-45a1-9f5b-738e30c0b9ce)
![13- Jenkins (Streamingapp-ci success console output snapshot](https://github.com/user-attachments/assets/c05ef230-8bb9-473a-a01f-4eca0eaf3a85)
![12- Jenkins (Streamingapp-ci success build pipeline snapshot](https://github.com/user-attachments/assets/8078b9fc-0ead-4b90-a561-76cd62696860)
## Continuous Integration demonstrated successfully.

## Step 6: Amazon EKS Cluster Creation

Created EKS cluster using eksctl
Added managed node group
Configured kubectl access
Command used: eksctl create cluster --name streamingapp-eks --region us-east-1
              kubectl get nodes
![19- EKS cluster deployment-1](https://github.com/user-attachments/assets/0291aef2-73cc-4911-b97b-1130fba85e66)
![20- EKS cluster deployment-2](https://github.com/user-attachments/assets/110f1bdf-0da7-4b06-9aa0-6a191b7800b4)
![20- EKS cluster deployment-3](https://github.com/user-attachments/assets/11c23dcd-4fd1-4d86-b970-ef7e2d0cf8f3)
![20- EKS cluster final deployment snapshot](https://github.com/user-attachments/assets/43edcd3f-429e-49d8-a536-af8ad3dc32fc)
![18-AWS EKS cluster created snapshot](https://github.com/user-attachments/assets/2d6c152c-81ab-4860-bb87-be4a0f497599)
## EKS cluster created and operational.

## Step 7: Kubernetes Deployment using Helm
Created Helm chart: helm create streamingapp
Fixed Helm template issues
Deployed application using Helm
Commands used: helm lint .
helm install streamingapp .
helm upgrade streamingapp .
Verified deployment: kubectl get pods and kubectl get svc
![23- Helm creation snapshot](https://github.com/user-attachments/assets/62d3417f-2c1d-4166-931e-ebd233a65583)
![24- Helm linting](https://github.com/user-attachments/assets/8e234154-f2af-411b-aa4f-f2f3eb8da46c)
![25- helm streamingapp deployment](https://github.com/user-attachments/assets/fe3157e9-f110-4ac5-89fc-47bd6fe57bf5)
![26-Streamingapp backend snapshot](https://github.com/user-attachments/assets/b180af4d-b337-4c29-a4e7-7f9fb15bd08e)
## Application deployed successfully using Helm.

## Step 8: Service Exposure & Validation
Exposed backend service using LoadBalancer
AWS automatically created an ELB
Verified public access using browser
![28- Final browser test  Deployment done ](https://github.com/user-attachments/assets/52d14aab-8849-4e35-bd4a-8f61bc2319d3)
Example output: Cannot GET /
This confirms: 
Application is running
Service is reachable from the internet
## Final validation successful.

## Monitoring & Logging
Kubernetes metrics server enabled
Pod status and logs monitored using kubectl
![22- K8s kube system snapshot](https://github.com/user-attachments/assets/ceee2a13-9c6e-4f2e-bed7-5b7af2c574ee)
![27-Final pods runing snapshot](https://github.com/user-attachments/assets/d6226470-4032-4546-aae3-296e0e13f022)

## Final Result

Application successfully containerized
CI/CD pipeline implemented
Images stored in ECR
Application deployed on EKS
Helm used for orchestration
Service publicly accessible

## I would like to thank Hero Vired for providing this learning opportunity.












































