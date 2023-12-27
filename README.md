## Provisioning an-EKS cluster using terraform and Deployment of an -ecommerce application


### Goal:

### Automating infrastrucure provisioning of an eks cluster using terraform and deploying an e-commerce application  

### The project workflow is shown below:

![work-flow](https://github.com/Noettie/End-to-End-automated-CI-CD-Pipeline-utilizing-GitOps-PART-ONE/assets/108426517/3d57814c-3de4-4664-964f-d4887f5f30c0)

### Objectives

1. Create an eks cluster using terraform.
2. Configure jenkins server
3. Deploy ecommerce application onto cluster.
   

### Tools:

<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/terraform/terraform-original-wordmark.svg" width="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/kubernetes/kubernetes-plain.svg" width="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" width="80"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/jenkins/jenkins-original.svg" width="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/github/github-original.svg" width="60"/>
<div>


### Steps:
Part 1: Testing the application locally
1. Provision the eks cluster by running terraform commands:
: $ terraform fmt
: $ terraform init
: $ terraform validate
: $ terraform plan
: $ terraform apply
_The cluster will take approximately 10-15 minutes to provision.
3. Update the kube config file with your region and cluster name as in the terraform file. This will enable you to connect to the cluster.
$ aws eks update-kubeconfig --region <eu-west-2> --name <eks_cluster>
4. Confirm the nodes were created.
$ kubectl get nodes
5. Deploy the application onto the cluster
$ kubectl apply -f deployment.yml
6. Access the application locally using the load balancer url
$ kubctl get svc
   

The application should be live:

![google-application](https://github.com/Noettie/End-to-End-automated-CI-CD-Pipeline-utilizing-GitOps-PART-ONE/assets/108426517/d92309cd-7ab8-4714-b137-4abd4a38131e)

### Congratulations! You have successfully provisioned an eks cluster and deployed an ecommerce application, and tested it locally.

7. Delete the application:
$ kubectl delete -f deployment.yml
8. Destroy the cluster
$ terraform destroy --auto-approve 

   Part 2: Jenkins configuration

10. Install Jenkins on a remote server.
11. Navigate to Manage Jenkins > manage credentials > System > Global credentails > Add credentials
* Add secret textt credential and add ypur aws secret_access_key and access_key
* Jenkins will use these credentials to authemtical with your aws account.
* Use the name of the key on Jenkins on the Jenkinksfile  environment section for proper authentication. 







