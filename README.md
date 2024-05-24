# Setup pipeline using CircleCI, update GitHub Kubernetes manifest repo, and push image on Docker Hub

✨This repository contains the code of the Kubernetes manifest files.

## Architecture

![Architecture Diagram](https://cdn-images-1.medium.com/max/800/1*T5IRoSoiqT8qnYLUprsRUQ.png)


## Synopsis
- When CircleCI notices any changes in the application code, it executes the jobs we have set up. There are a total of four jobs:

### Test: 
- This job tests the code. After the test job is completed, CircleCI proceeds to the next job. 
- Note: I didn't add this job to save time. 

### Build: 
- In the build job, CircleCI pulls the base Docker images and packages our application code inside the image.

### Push: 
- The push job pushes the newly generated images to Docker Hub with a new tag.

### Update Manifest: 
- After completing the push job, the last job is executed, which updates the Kubernetes manifest repository with the new tag. This enables ArgoCD to detect the change and apply it to the cluster.

Following this pipeline ensures that our application code is thoroughly tested, built into Docker images, and deployed with the updated manifest using the GitOps approach.

**Contains Three GitHub repositories**

➡️ [App Code] (https://github.com/hectorlopezv/circle-ci-eks-argocd)

➡️ [Terraform code] (https://github.com/hectorlopezv/s3-terraform-eks-vpc-natgw-nodegroup-argo-cd-lab/tree/main)

➡️ [Manifest Repo] (https://github.com/hectorlopezv/eks-manifest-todo-app)
