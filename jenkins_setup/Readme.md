# Jenkins Post-Installation Setup
Use admin-password and JenkinsURL (localhost:8080) for jenkins_setup.

## Step1: Browse JenkinsURL and Unlock Jenkins
http://localhost:8080 \
Unlock Jenkins using admin-password

## Step2: Customize Jenkins - Add Plugins
### Install suggested Plugins (Preferred)
It installs all the necessary plugins and related dependencies.

### Select Plugins to install
You need to decide which plugins you want. \
It can led to some missing features.

## Step3: Create First Admin User 
### Configure new user details
Fill user information.  \
Note: Jenkins will remove the default admin user.

### Skipping user configuration
If you skip adding new Admin user. You have to use the default Admin user to login. \
Note: This is not good security practice as plaintext password is present on server.

# Jenkins Setup

## Manage Plugins
Jenkins with no plugin does not do anything.   \
Plugins add functionality to Jenkins.  

Refer Readme.md in manage_plugins directory.

## Manage Credentials
Credential plugin used to store and manage credential centrally.
You can store SSH, Github, etc credential in Jenkins.

Refer Readme.md in manage_credential directory to manage credentials.

## Source Code Management Integration
SCM helps to store code with versions (revertible). \
SCM helps to track the changes.  

Refer Readme.md in global_tool_configuration directory to setup Git path.  \
Refer Readme.md in configure_system directory to setup Git Server.

## Configure System
Configure global setting and path.
- Jenkins URL
- Github Server
- Extended E-mail Notification
- E-mail Notification, etc

Refer Readme.md in configure_system directory to setup global setting. 

## Global Tool Configuration
Configure tools, their locations and automatic installers. 
- Git
- Maven
- Gradle
- NodeJS, etc

Refer Readme.md in global_tool_configuration directory to setup tools. 

## Configure Global Security
Secure Jenkins, define who is allowed to access/use the system.
- Authentication
- Authorization  

Refer Readme.md in configure_global_security directory to setup authentication and authorization. 

## Notifications
Jenkins helps to notify the appropriate member timely about success or failure with customize message.

You need to define the team to be notified:
- Dev and QA: Notify for failure so they can respond. (Continuous Delivery)
- DevOps: build status (can indicate issue with Jenkins)

Type of Notifications:
- Email # Email Notification or Extended Email Notification
- Instant messaging / SMS   # Slack Integration
- Dashboard view  (For Non-tech person)

Refer Readme.md in configure_system directory to setup Simple or Extended Email Notification.

To let team know about **scheduled maintenance**.
Refer Readme.md in configure_system directory to setup scheduled maintenance info.

## Monitoring
Monitor important metrics.

