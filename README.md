# Ubuntu Commands

1. [Heroku](#heroku)
2. [Processes](#processes)
3. [Python](#python)
    * [Pip](#pip)
    * [Virtual Environments](#virtual-environments)
4. [Github](#github)
    * [Branches](#branches)
    * [Project History](#project-history)
    * [Misc](#misc)

## Heroku
Install [Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up).
```
sudo add-apt-repository "deb https://cli-assets.heroku.com/branches/stable/apt ./"
curl -L https://cli-assets.heroku.com/apt/release.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install heroku
```

To login.
```
heroku login
```

To link a git repo to an existing heroku project.
```
git remote add heroku git@heroku.com:[project_name].git
```

## Processes
Using fuser.

To see processes and details (-v) of each process using a particular directory or executable.
```
fuser [path]
fuser -v [path]
```
Kill a process (interactively, -i) that's using a particular executable.
```
fuser -v -k [path]
fuser -v -k -i [path]
```
To see which processes are using a particular port with TCP.
```
fuser -v -n tcp [port]
```
Kill a process using TCP running in a particular port.
```
fuser -k [port]/tcp
```


## Python
Some python utilities.

#### Pip
To save the Python modules installed with pip to a file that we'll call *requirements.txt* (needed for virtual environments and collaborating on a project). This command is the same for any pip version, just substitute pip for, say, pip2.
```
pip freeze > requirements.txt
```
To install from a file, let's say our *requirements.txt*.
```
pip install -r requirements.txt
```

#### Virtual Environments

First install virtual environments, substitute pip with conda if you're using Anaconda.
```
pip install virtualenv
```

To create a Virtual Environment named virtual_env.
```
virtualenv virtual_env
```

To enter and exit a Virtual Environment; our *virtual_env*.
```
source activate virtual_env
source deactivate
```

Once inside this is the pipeline to follow so that everybody can have the *same* Virtual Environment:
* Install modules using pip, let's say we want to install *Flask*.
```
pip install flask
```
* Write the modules in use to a *requirements.txt*.
```
pip freeze > requirements.txt
```
* To delete the Virtual Environment, one just needs to remove the directory (always source deactivate before doing this).
```
rm -rf virtual_env/
```
* Now this is how the working directory would look like for someone who doesn't have your personal Virtual Environment, so they'll do the following.
```
virtualenv my_env
source activate my_env
pip install -r requirements.txt
```

## Github

##### Branches
Create a new branch:
```
git checkout -b <branch_name>
```
```
git branch <branch_name>
```
To see all branches:
```
git branch
```
for local branches, for remote branches:
```
git branch -r
```
To change to a branch:
```
git checkout <branch_name>
```
To pull a remote branch:
```
git checkout -b <new-local-branch-name> origin/remote-branch-name
```
Or:
```
git checkout -t origin/remote-branch-name
```
To remove a remote branch:
```
git push origin --delete <branch_name>
```
Or:
```
git push origin :<branch_name>
```
Then to propagate changes in local machines execute the following:
```
git fetch --all --prune
```
#### Project History
You can view a timeline of your changes using:
```
git log
```
If you also want to see complete diffs at each step, use
```
git log -p
```
Often the overview of the change is useful to get a feel of each step:
```
git log --stat --summary
```
To just see the title and id of each commit.
```
git log --pretty=oneline
```
We can give this id to git show to see the details about this commit.
```
git show <number of the commit>
```
#### Misc
* Removes files from your index and your working directory so they will not be tracked.
```
git rm <file_name>
```
* This will remove the file from git but not from the Disk:
```
git rm --cached <file_name>
```
* Move or rename a file, directory, or symlink.
```
git mv <file_name>
```
* Unstage a file
```
git reset HEAD <file_name>
```
* Delete a commit (HEAD~1 means one commit before HEAD)
```
git reset --hard HEAD~1
```
* Reset HEAD to a commit.
```
git reset --hard <sha1-commit-id>
```
