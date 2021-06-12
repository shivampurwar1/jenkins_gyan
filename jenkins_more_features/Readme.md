
# Artifacts
Artifact is data related to build or created as a side effect of build.
Artifact belongs to one build while one build can have multiple artifact.
Artifact can be archived to store outside of workspace. 

Note: If someone wipeout the workspace then no build data will be present. But if you archive artifact then it will be still available.

Note: Build environment also have setting to ‘delete workspace before build starts’ (By Default not enabled)
Jenkins > (Project) > Build Environment > 'Delete workspace before build starts'

Artifact can be setup as Post-build Actions.
(Project) > Post-build Actions > 'Archive Artifacts'
- Files to archive
- (tick) Fingerprint all archived artifacts.   # By default not enabled



# Fingerprints
It allows to track artifacts back to their build. 

Jenkins > (Project) > (job_num)
Build Artifacts > View 
See Fingerprint > more detail (md5) 
