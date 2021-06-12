# Configure System
Configure global setting and path. \
Jenkins > Manage Jenkins > Configure System

## Jenkins Location
Jenkins > Manage Jenkins > Configure System > Jenkins Location 
- Jenkins URL: localhost:8080  # Default
Note: If want GitHub Hooks work then need to have public accessible URL.
Ex: (Public IP:port or Public hostname)

## Github
Jenkins > Manage Jenkins > Configure System > GitHub
- GitHub Server: <Any-Name>
- Credential:  SecretText:<personal-access-token-from-git>
- (tick) Manage Hook

### Generating personal access token on GitHub
GitHub > Settings > Developer Setting > Personal Access Token
- Name:
- Select Scope: 
  - Repo
  - Admin:repo_hook
  - User-email    # If using Ocean Blue
- Generate Token
Note: Copy the token.

## System Message
Jenkins > Manage Jenkins > Configure System > System Message
- Write message to notify for maintenance

## Extended E-mail Notification
Jenkins > Manage Jenkins > Configure System > Extended E-mail Notification
- Content type
- Default Subject
- Default content

## E-mail Notification
Jenkins > Manage Jenkins > Configure System > E-mail Notification
- SMTP Server
- Default user e-mail suffix
