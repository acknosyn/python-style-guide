# Project Requirements
Every project should have a `requirements.txt` file. This file contains the Python modules that were installed for the project, and the versions.

Create a blank `requirements.txt` file in the project root.

## Add modules
Every time you install a module with pip, remember to add it to the `requirements.txt` file. Copy the module name and the version.

## Install project requirements
When setting up a new project for example, you'll want to install the project dependencies (after setting up a [virtual environment](virtual-environments.md)).

Make sure you `cd` to the project root first.
```shell
pip install -r requirements.txt
```

## Example
Here's what an example requirements.txt file could look like.

```
requests==2.14.2
configparser==3.5.0
PyYAML==3.12
```

## Comments
Feel free to add comments for module sections. If the file contains a lot of modules, comments would be recommended so people understand why a module was installed, what it's used for, and if they would still need it.

```
# API calls and such
requests==2.14.2
...

# logging configuration
PyYAML==3.12
...

# secretes management
configparser==3.5.0
```
