# Pipeline
Pipeline provides functionality to facilitates Continuous Delivery.
Pipeline as a code helps to streamline processes.

## Define a Pipeline 
It can be done either by the web UI or with a Jenkinsfile. 

(Project_name) > Pipeline
### Pipeline Script
You write pipeline in the Script section.  \
In this case, resulting Jenkinsfile will be store in Jenkins master.  \
Note: Managing this become more difficult as pipeline become more complex or large.

### Pipeline script from SCM (Jenkinsfile)
Manage pipeline as code (Jenkinsfile) through SCM. Jenkinsfile are used inside code repo to provide the configuration for a job.
- SCM: Git (Git Repo, Credential)
- Branch specifier
- Scriptpath: Jenkinsfile  # Path to Jenkinsfile, by default checks in root directory of repo.

## Types of Pipeline
Pipelines are made up of Stages.

### Scripted Pipelines
Begins with 'node'.  \
Uses Groovy (provides flexibility and control)  \
Follows imperative model -> Describe how something should be accomplished  \
[Sample Pipeline] (Project_name) > Pipeline > Pipeline Script > 'Try Sample Pipeline' > Scripted Pipeline

### Declarative Pipelines
Begins with 'pipeline'.  \
Uses Pipeline DSL    #  DSL is domain specific language for Jenkins Pipeline.  \
Follows declarative model -> Describe what will be desired result. (not concerned how we get result)  \
The smallest component of a pipeline is a step. Stages are made up of one or more steps.  \
[Sample Pipeline] (Project_name) > Pipeline > Pipeline Script > 'Try Sample Pipeline' > Hello World

Note: Declarative pipelines don’t go in as depth in comparison to Scripted pipelines. 
So some functionality is missing in the Declarative pipeline. 

Note: Use 'Pipeline syntax' to get required syntax.

## Pipeline Syntax
If helps in pipeline related syntax. You can customize pipeline based on the requirement.
### Snippet Generator
It will help you learn the Pipeline Script code which can be used to define various steps.
click 'Snippet Generator' > Sample Step
- checkout: Checkout from version control
- sh: Shell Script
- archiveArtifacts: Archive the artifacts        
- Tool: Use a tool from a predefined Tool installation
- withCredential: Bind credential to variables
etc

Copy the generated code into the pipeline. ex: ‘steps’ section of the desired stage,etc

### Declarative Directive generator:
It allows you to generate the Pipeline code for a Declarative Pipeline directive
click 'Declarative Directive generator' > Simple Directive: 
- agent: Agent
- tools: Tools
etc

These decorations are easy to read. There is no need for programming language understanding. 
Copy the generated code into the pipeline. ex: ‘steps’ section of the desired stage,etc

### Global Variable Reference: 
Global Variables that can be used in Pipeline jobs.
Examples: BRANCH_NAME, BUILD_NUMBER, etc.

### Declarative Online Documentation: 
Official Jenkins Doc. (click Index to see all topics)

### Steps Reference: 
Defines what steps are and how to construct them. 
DSL reference.

### Example References: 
Various Pipeline examples

## Pipeline Syntax
### Variables
Global variables define out of stage blocks. These variables are accessible to Pipeline (all stages).
Local variables are those defined inside the stage. These will be accessible within that stage.


## Executing Pipelines
(Project_name) > Pipeline > Pipeline Script > 'Try Sample Pipeline' > Hello World


## Multi Branch Pipeline
Jenkins > New Job > (Project_name) > Multibranch Pipeline > ok
Jenkins > (Project_name)
- Branch Sources: (GitHub)
- Credentials: (Project) Domain    [username, password(personal-access-token)]  -> permission: Repo control
- Repository
- Save

It scans the branches (based on condition - by default all) for Jenkinsfile, if file present then build.

Manually Scan branch:
Jenkins > (Project_name) > Scan Repository 
Jenkins > (Project_name) > Scan Repository Log  # To view logs.   

Note: If Jenkinsfile is removed then on next scan or build those builds (related to branch) won’t be visible.

If a branch is matching the criteria but doesn't have Jenkinsfile then Jenkins won’t build that branch.


## Pipeline Triggers
Trigger is a process that causes a pipeline job to run.
### Webhook
If commit occur in repo, SCM notifies Jenkins using webhook and Jenkins run job.
Developer  --Commit---> Git Repo ---Pushes to--> Jenkins webhook url---> Trigger Jenkins Build

**Configuring webhook**
Make sure SCMServer (ex: GitHub) configured (with manage hook) in 'Configure System'
Make sure Jenkins URL/hostname configured in 'Configure System' and it is available over internet.
(Project_name) > Pipeline > Pipeline Script from SCM
  - Script Path: Jenkinsfile
(Project_name) > Build Triggers
  - (tick) Github hook trigger GITScm polling
  
Verify on GitHub:
Github > Settings > Integration > WebHook
- URL: Jenkins webhook url   
  
### SCM Polling
Check for SCM on a schedule interval. If changes present then run job.
Jenkins ---polls on defined schedule---> Github ---If changes present---> Trigger Jenkins Build

(Project_name) > Build Triggers
  - (tick) Build Periodically: Schedule -> H/15 * * * * *    # Every 15 min

(Or)

Use Triggers in the Jenkins file, which accepts the cron syntax. 
cron(‘H/15 * * * *’)    # Every 15 min
Note: You need to Build once manually to reflect this trigger for future run. 

Note: H is used in syntax to represent Hashed value.
Note: Having shorter polling may overload the Jenkins so select the appropriate interval.

Tip: There are chances that webhook may not be reliable (Jenkins down, etc). 
So it is good strategy to configure both strategy as backup plan.

### Build Schedule
It runs job at a specific time regardless of changes. 

### Other Options
#### Triggering based on Other Job
This can help in deployment where build done by one job and based on the result Deployment job triggered.
Use Triggers in the Jenkins file
triggers {
   upstream "<job-name>"
}

#### Adding Triggers in Multi branch
Jenkins > (Project_name) > (branch) > Configure
Option to select Github hook triggers for GitScm polling. But no Save button. 
To achieve triggers in multibranch, you need to add triggers in Pipeline code.
triggers {
   githubPush()
}
Note: You need to ‘Scan Repository’ once manually to reflect this trigger for future run. 

You need to replicate the same thing for other branches.

## Global Libraries


## Using Docker in Pipelines
Make sure Docker is installed.

### Docker in Pipeline
In Agent declaration we get docker containers.
Ex: Specifying an agent to run docker image for node.
agent {
   docker { image 'node:7-alpine' }
}

Note: Build logs will specify that you are running [Pipeline] WithDockerContainer and Jenkins doesn’t seem to be running inside a container.
At the end, the pipeline stops docker and clean. 

Note: As docker image gets pulled for the first time. The pipeline can be slow in the first run but subsequent runs are faster as the docker cache pulls images. 

### Using different containers in different stage
We can declare different docker containers in each stage. 
For that we need to do agent declaration at each stage.

### Using Dockerfile to define docker steps
For this we need to set following:
agent { dockerfile true }
So when Jenkinsfile runs, it will also expect the Dockerfile in the same repo. 


## Groovy sandbox prevents any malicious code on Jenkins server.  
(Project_name) > Configure > Pipeline
Ex: Groovy code to print number
1.upto(9) {println “$it”}          
Error: Scripts not permitted to use staticMethod org.codehaus.groovy.runtime.DefaultGroovyMethods upto

(Project_name) > Configure > Pipeline > (untick) Use Groovy Sandbox.
Note: It disables security so don’t use it.