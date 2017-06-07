# Ubuntu Commands

1. [Heroku](#heroku)
2. [Processes](#processes)
3. [Python](#pip)

## Heroku
Install [Heroku CLI].
[Heroku CLI]: https://devcenter.heroku.com/articles/getting-started-with-python#set-up.

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
1. [Pip](python-pip)
2. [Virtual Environments](python-virtualenv)

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
