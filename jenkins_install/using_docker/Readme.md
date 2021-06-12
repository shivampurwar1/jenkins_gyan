# Pre-requisite
Docker should be installed.

# Search Jenkins image on DockerHub
[Deprecated-official] https://hub.docker.com/_/jenkins

[Maintained] https://hub.docker.com/r/jenkins/jenkins     
[Documentation] https://github.com/jenkinsci/docker/blob/master/README.md

```
# Starting Jenkins Container
docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

Command Overview:
- Exposing Jenkins port 8080
- Exposing Master slave port 50000
- Detach mode (-d) run in background
- Name volume binding, the volume will be created inside the container to persists the data.

```
# Verifying the process
docker ps

# Check logs for admin-password (Refer initial setup section)
docker logs <container-id>

# Verifying/Debugging inside container 
docker run -it <container-id> bash
```

Use admin-password and Jenkins url (localhost:8080) for jenkins_setup.