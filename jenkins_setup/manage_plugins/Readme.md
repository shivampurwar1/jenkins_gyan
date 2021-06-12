Jenkins with no plugin does not do anything.   \
Plugins add functionality to Jenkins.  \

# Manage Plugins
Few plugins are installed during setup (predefined or selected).
You can mange plugins using 'Manage Plugins' wizard. 
Jenkins > Manage Jenkins > Manage Plugins

Update Tab: 
- You can see the pending update. 
- You can use ‘check now’ to see any new pending update
- You can download and install the update.

Available Tab: 
- You can search for plugins.
- You can get detail about plugin: ex: Last release, documentation, etc.

Installed Tab:
- You can see the installed plugin and it's version.
- You can uninstall the plugins.
Note: Grey Uninstall button means that Plugin have some other dependency.

Advanced Tab:
- You can configure custom plugin server (instead of official jenkins).
- Manually install plugins using .hpi file.
- You can set other update site to check for plugin updates.

# Useful Plugins
## Copy Artifact
Adds a build step to copy artifacts from another project. 

## Blue Ocean
Graphical pipeline editor to create declarative pipelines.
Jenkins > Open Blue Ocean > Create a new pipeline 
- Where do you store your code: Git
- Connect to Github: (github_token)
- Organization
- Choose Repo
- Complete
Use UI to create stages (give stage name and Select steps to do). 
It will automatically generate the Jenkinsfile and commit it to the Repo.


# Tip
## Downgrade Plugins
Jenkins > Manage Jenkins > Manage Plugins > Installed > (GitHub API Plugin ) 
Get old plugin versions: http://updates.jenkins-ci.org/download/plugins/ 
Search for specific plugin (ex: GitHub api) > Select (ex: GitHub API) > Select specific old version (ex:1.x) - Copy link address.
On Jenkins machine:
```
#wget <version-of-file>      # github-api.hpi
# cd /var/lib/jenkins/plugins
# ls -la | grep github
# mv -v ./github-api ./github-api.old
# mv -v ./github-api.jpi ./github-api.jpi.old  
# cp -v ~/github-api.hpi ./
# sudo chown jenkins:jenkins github-api.hpi
#sudo systemctl restart jenkins
Jenkins > Manage Jenkins > Manage Plugins > Installed > (GitHub API Plugin ) # notice version will be older.
```

## Uninstall Plugins
What happens in X plugin get removed?
Jobs can fail if they are depending on the functionality provided by the plugin.
