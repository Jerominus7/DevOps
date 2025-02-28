## Using Git

Git is the local client, that can pull and push updates to the Github repo. An alternative to Github can also be Gitlab or Bitbucket.
Git also allows multiple users to push and pull updates from the Github code repository, etc.


# Home Scenario
## Build Steps

1. Develop Code (on laptop, or etc.)
2. Build Code into an Executable or Binary
3. Deploy

Note: This is just basic steps.

########################################################################
# Sample Scenario 1

## Build Steps
1. Develop code
2. Push code to Build Server
	1. Manual copy code to build to create the exe
3. Test Code 
	1. This is a manual push to Dev for testing
4. Push to production
	1. This is a manual push to Prod for test

Note: This could be done once a week, but that is unacceptable. It could even take a week for the deployment of changes to take place. The key here is: you want to push code with new features faster, and more frequently, with less manual effort. 

### Sample CI/CD Pipeline:
Every time code is pushed, it is automatically pulled from the Github repo, automatically pulled to the build server, automatically pushed to the test environment/server and then tested, and then finally automatically deployed to Prod.

### Sample Scenario Issues
If the development requires specific dependencies or libraries to run on any system, it needs to ensure the build, test, and production servers are configured the exact same way. If one is misconfigured, it could cause issues and outages.

This can be fixed by utilizing container images.

# Docker (Containers) #docker
## Docker is a containerization application that allows you to containerize your app with all of the required dependencies and libraries.
One of the container apps that helps build a container that includes the dependencies and libraries into a container file that can run on any server.

Dockerfile will contain the dependencies and be used during the build phase, which then can create the container image for the test and production server which will then run the container. Kind of like a template for the build server to create the containers.

![[Pasted image 20240731131912.png]]

#### Note
Main function of a container is to provide isolation between processes. Can run multiple containers each having their own instance of the application running on the same server. I.e. Test can have 3 containers providing the same app.

# Kubernetes #kubernetes
## Kubernetes is an container orchestration tool for the applications being ran.
Kubernetes is a container orchestration tool. It can manage all of the Docker containers and can spin them up and spin them down as the demand for the application rises and falls.

![[Pasted image 20240731135748.png]]

# Terraform #terraform
## Terraform is a tool that automates the provisioning and configuration of the servers regardless of what cloud platform they are one. This is why it is considered IaC or Infrastructure as Code.

It ensures the servers configured are always in the same state. If someone changes the configuration of the server via manual means, it will automatically change it back to ensure the state defined is preserved. 

Due to it being code, it can be stored inside of a code repository with version control, permissions, etc. If changes are needed, you can then update the repository where the code exists and run the terraform apply command.


Terraform sample manifest file:
![[Pasted image 20240731152934.png]]

# Ansible #ansible

Where Terraform is more of an infrastructure provisioning tool, Ansible is more of a automation tool that helps configure the infrastructure once it is provisioned.

Note: There are many overlaps between Ansible and Terraform, both can provision and automate software configuration, Ansible is still mostly used for post provision.

Ansible uses code called Ansible Playbooks which are in the yaml format. It is also stored in the github repo. 

![[Pasted image 20240731154622.png]]


# Prometheus #prometheus
## Collects metrics and monitors the servers, looks for CPU usage, memory, processes, etc. and then stores the data centrally.

Once it is stored it can be sent to tools like Grafana to visualize the data.

# Grafana #grafana

A tool used to take the data from other tools, and then visualize and graph it out for analysis.

![[Pasted image 20240731155127.png]]