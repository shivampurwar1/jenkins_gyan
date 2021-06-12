

# Example for impact of plugins uninstall. (ex: Copy Artifact)



# Webhook setup
Note: Make sure Git Server and git path configured.
Jenkins > (Project) > Build Triggers 
GitHub hook trigger for GITScm polling  # react to git commit (push)
Poll SCM  # poll in the scheduled interval
Build Periodically  # Build periodically even there is no change

Github > settings > WebHook 
It will have webhook info if Jenkins configured with ‘GitHub hook trigger for GITScm polling’
