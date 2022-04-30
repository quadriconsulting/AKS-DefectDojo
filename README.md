# Introduction 
To deploy an open-source security app(vulnerability management tool) that contains 6 services with the docker-compose yml file and integrate it with the Azure pipeline.

TASK: Requirement

## Azure Container Deployment
1. AKS Deployment
2. Deployment with ARM
3. DevOps pipeline integration


Use and create managed azure mysql instance

Azure Kubernetes Service (AKS) simplifies deploying a managed Kubernetes cluster in Azure by offloading the operational overhead to Azure. As a hosted Kubernetes service, Azure handles critical tasks, like health monitoring and maintenance. Since Kubernetes masters are managed by Azure, you only manage and maintain the agent nodes. Thus, AKS is free; you only pay for the agent nodes within your clusters, not for the masters.


ARM is azure resource manager which is infra as code from Microsoft. It has good integration and modules for azure resources.
Terraform is Infra as code from hashicop and its very mature IAC and can be used in any platform. Sicne we want to build the infra one time only then we will use ARM template, since we dont want to make changes continuously then we will not use Terraform.

AKS auto scaling can be implemented on multiple levels like request per second, hpa, vpa and ca as well.

Backup is stored in ACR and storage we are keeping backups of redis with persistent volume claim. Also MySQL has enabled auto backup

aks master is manged by azure and they have a SLA for it we only have to mange our services .

To keep minimun 1 vm active. And we can schedule autoscale down of kubernetes vm and mysql. Mysql autoscale down and up is bit complex to implement.

implement cluster auto-scaling in test as well.


1. Autoscaling of mysql db instance.

2. Autoscaling on AKS cluster vm level autoscaling.

3. Auto shut down and start mysql database.

4. Auto shutdown of aks vm's.

5. Private load balance and implement express routes to access it.

## Test:
A simple docker version running on port 8000:

docker run -it -p 8000:8000 appsecpipeline/django-defectdojo bash -c "export LOAD_SAMPLE_DATA=True && bash /opt/django-DefectDojo/docker/docker-startup.bash"

Docker image: https://hub.docker.com/r/defectdojo/defectdojo-django

GITHUB: https://github.com/DefectDojo/django-DefectDojo

# Getting Started
TODO: Guide users through getting your code up and running on their own system. In this section you can talk about:
1.	Installation process
2.	Software dependencies
3.	Latest releases
4.	API references

# Build and Test
TODO: Describe and show how to build your code and run the tests. 

# Contribute
TODO: Explain how other users and developers can contribute to make your code better. 


acr : this include arm temp[late to create azure cointainer registry 
aks-template-network : this will create prerequisite network setup for aks
mysql it include ARM template to create the mysql instance in AZURE 

azurew-pipelines1.yml will create AKS network setup using arm TEMPLATES
azurew-pipelines2.YML WILL create acr in azure cloud 
azurew-pipelines-mysql.yml : will create mysql instance in azure 

azurew-pipelines.yml will azure k8s services 
