# Global Tool Configuration
Configure tools, their locations and automatic installers. \
Jenkins > Manage Jenkins > Global Tool Configuration

Note: These tool list vary based on the plugins. \
To add new tool first need to add plugin.

## Installing the tool
If plugin is already present then tool will be visible. \
Example: Installing Maven

Jenkins > Manage Jenkins > Global Tool Configuration > Maven > Maven Installation
- Name: Maven
- (tick) install automatically
- version
- Save

# Important Tools
## Git
Jenkins > Manage Jenkins > Global tool configuration > Git
- Name
- Path to Git executable

## Maven
Jenkins > Manage Jenkins > Global tool configuration > Maven

## Gradle
Jenkins > Manage Jenkins > Global tool configuration > Gradle

## NodeJS
Jenkins > Manage Jenkins > Global tool configuration > NodeJS


# Tips
## If UI not able to detect tool path 
Example: git path
Then verify on jenkins server ‘which git’  -> If git present add the path.
If not then install git ‘sudo yum install git -y’ and get the path.


