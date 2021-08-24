# Virtual environments

- [Virtual environments](#virtual-environments)
  - [Install virtualenv](#install-virtualenv)
  - [Install virtualenvwrapper](#install-virtualenvwrapper)
  - [Create a virtual environment](#create-a-virtual-environment)
  - [Install project dependencies](#install-project-dependencies)

Virtual environments are local—project specific—containers which holds Python packages so you don't pollute your global system.

It also makes managing multiple package and Python versions easy. You can set a virtual environment's Python version without worrying about other installed versions.

Check out this [virtual environments guide](http://docs.python-guide.org/en/latest/dev/virtualenvs/) for an in-depth explanation on the subject.

## Install virtualenv
```shell
pip install virtualenv
```

## Install virtualenvwrapper  
`virtualenvwrapper` provides a set of commands which makes working with virtual environments _a lot_ easier. It also places all your virtual environments in one place.

For MacOS:
```shell
pip install virtualenvwrapper

# set the location to store virtualenvs, name it whatever you want
export WORKON_HOME=~/.virtual_envs
source /usr/local/bin/virtualenvwrapper.sh
```

For Windows:
```shell
pip install virtualenvwrapper-win
# in Windows, the default path for WORKON_HOME is %USERPROFILE%Envs
```

## Create a virtual environment
These are all virtualenvwrapper commands.  
Where `python_project` is the name of your project:

This creates the python\_project folder inside WORKON_HOME, e.g. ~/Envs.
```shell
mkvirtualenv python_project
```

Any time you start a new session, for example, you'll need to work on a virtual environment:
```shell
workon python_project
```

Deactivate a virtual environment:
```shell
deactivate
```

Delete a virtual environment:
```shell
rmvirtualenv python_project
```

### Python 3
To make a virtual environment using Python 3, use the `--python` flag.

On macOS, simply run
```shell
mkvirtualenv --python=`which python3` python_project
```

On Windows, find the path of Python 3 first
```shell
which python3
# output: /usr/bin/python3
mkvirtualenv --python=/usr/bin/python3 python_project
```

## Install project dependencies
Assuming the project has been setup properly with a requirements.txt file; install the required python modules (inside the virtualenv):
```shell
pip install -r requirements.txt
```
