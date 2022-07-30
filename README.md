# Azure-DevOps-Tutorial-for-Beginners-CI-CD-with-Azure-Pipelines



https://azure.microsoft.com/pt-br/free/search/?&ef_id=Cj0KCQjwio6XBhCMARIsAC0u9aG6JTCzpv2tLXcDUshIsFoS_uyIKp6g0wo0b9AD7_f6LxGyzTm-A6oaAmQYEALw_wcB:G:s&OCID=AIDcmmzmnb0182_SEM_Cj0KCQjwio6XBhCMARIsAC0u9aG6JTCzpv2tLXcDUshIsFoS_uyIKp6g0wo0b9AD7_f6LxGyzTm-A6oaAmQYEALw_wcB:G:s&gclid=Cj0KCQjwio6XBhCMARIsAC0u9aG6JTCzpv2tLXcDUshIsFoS_uyIKp6g0wo0b9AD7_f6LxGyzTm-A6oaAmQYEALw_wcB

Azure Boards 

Azure Repositories 
Host your Code
GitHub 
GitLab
Based on Git
BitBucket 

Azure Repos
Devops Collaborate
Create Branch 
Pull Request 
They collaborate until the main Branch
So they need to be Released
Plan > Code > Test > Package > Single Artifact > Deploy 
Continuous Integration ( CI ) Test / Package 

Pipeline
Azure-pipelines.yml

Trigger:
master
Pool:
vmImage : ‘ubunto-22.04’

variables: 
buildConfiguration: ‘Release’

steps: 
script: dotnet test
displayName: Run until tests 

script: dotnet build - - configuration $(buildConfiguration)
           displayName: build application

script: docker build -t my-image:v1.0.
displayName: build image
script: docker push my-image:v1.0.
displayName: Push image 

Task
pipeline yml editor

Agent

jobs: 
job: Run on Windows
pool:
           vmImage: ‘windows-latest’
steps:
script: dotnet test
displayName: Run unit tests
 
jobs: 
job: Run on Linux
pool:
           vmImage: ‘ubuntu-latest’
steps:
script: dotnet test
displayName: Run unit tests




Azure Artifact 
Source Code > Artifact ( Jar, Nuget , mpm … ) 
Docker Images 

Azure Pipelines (Build)
Test > Build artifact > Push to container repository > ( Azure Container Registry, Amazon ECR ) > Deploy ( Continuous Deployment CD ) 

Build and Deploy 

job:
job:Build and test 
steps:
task:DotNetCoreCLI@2
            inputs:
             command: ‘test’ 
task:DotNetCoreCLI@2
inputs: 
command: ‘build’
arguments: ‘- configuration $(buildConfiguration)’
task: Docker@2
inputs: 
command: ‘buildAndPush’
 Dockerfile: ‘* * / Dockerfile’ age:v1.0 .
displayName: push image 
jobs:
job: Deploy to dev
    steps: 
task: AzureWebApp@1
             inputs: 
             appName: myapp
             package: ‘$(System.DefaultWorkingDirectory)/* * / * .zip’

Stages: 
-stage: Build
jobs:
job: Test and Build 
steps:
task: DotNetCoreCLI@2
…
task: DotNetCoreCLI@2
…
task: Docker@2
…

-stage: Deploy
          jobs:
job: Deploy to development
steps:
task: AzureWebApp@1
…

Release PipeLines 
Test > Build Image > Push to repository > 
Continuous Integration ( CI ) 

Deploy to Dev > Deploy to Testing > Deploy to PROD
Continuous Delivery ( CD ) 

Test Plans
Automated Tests
Manual Tests 
Exploratory Tests 
User Acceptance Tests 

Azure DevOps Architecture 
Running tests…
Building images
Deploy to dev

Software as a service from Microsoft 
Main part: Configurations, Pipelines, Repos created and stored // agents 
Microsoft hosted agents

Pricing // Free 
Plan > Code > Test > Package > Deploy 

Push Docker Image to Container Repository 

Deploy to Remote Server 
Microsoft Azure, Aws, Google Cloud, Kubernetes Cluster

Project Hosted on External Code Repository 

Feature Branch
Pull Request 
Build Pipeline 
Deployment 
