# Information about Credential
Credential plugin used to store and manage credential centrally.
Credential stored in primary instance.

## Credential Scope
### Global
Accessible everywhere.  \
Ex: Jenkins, Nodes, Items, All child items, etc
### System 
User to access specific area. (ex: Jenkins Administrator)
Ex: Jenkins and Nodes only
Note: Available for Pipeline.
### Pipelines
Present only in multibranch pipeline. Limited to project.
These credential available in Folder. 
Folder enables to organize build job in folders, which helps to organize and hide things between project.  

## Kind of Credentials
### Username with password
Instance of credential (username:password)
Ex: Github username and PersonalToken
### SSH Username with private key
SSH
### Secret file
Tokens (api token)
Ex: Github token
### Secret text
Content of secret stored in File.
### Certificate
PKCS#12 certificate file and password
### Github App
For Github app

## Id
If not specified then Jenkins generate UUID.
This will be reference by credentials.

# Generating Credentials

## Using Manage Credentials
Jenkins > Manage Jenkins > Manage Credentials > global > Add Credentials
- Kind (List can be based on plugins)
- Scope
- Id 

## Pipeline based
Jenkins > (Project) > (branch) > Credential

# Security
- Encrypted at Rest.
- obfuscated/masked on build logs.
- Not visible on Jenkins console.