# Logging

- [Logging](#logging)
  - [Logzero](#logzero)
  - [Setup logging — Basic](#setup-logging-basic)
  - [Setup logging — Better](#setup-logging-better)
  - [Use logging in multiple files](#use-logging-in-multiple-files)

`print` statements are useful for quick debugging, but are terrible for informative logging.

Sometimes, you can get away with using `print` statements if your script is small. But anything involving multiple modules (files) should use some form of logging.

Use the `logging` built-in library. It lets you set the level of severity of a message and gives you context of the time and the module where the message came from.

Alternatively, use a logging package to make things easier.

## Logzero
Logzero provides a ready-to-use logging configuration with good settings. It extends the logging module so you can still do things like set the logging level.

```console
$ pip install logzero
```

### Examples

```python
from logzero import logger

logger.debug('hello')
logger.info('info')
logger.warn('warn')
logger.error('error')
```

Easy! See github.com/metachris/logzero for more info. Keep reading for a more detailed guide on logging.


## Setup logging — Basic
To use the `logging` module, you need to configure it first. At a minimum, set the level of logging, otherwise it defaults to WARNING.

```python
import logging


logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

logger.debug('This will not be logged')
logger.info('This will be logged as INFO')
logger.warning('This will be logged as WARNING')
logger.error('This will be logged as ERROR')
```
```
INFO:__main__:This will be logged as INFO
WARNING:__main__:This will be logged as WARNING
ERROR:__main__:This will be logged as ERROR
```

## Setup logging — Better
[Good logging practice in Python](https://fangpenlin.com/posts/2012/08/26/good-logging-practice-in-python/) is a good article on setting up logging.

```python
import logging


logger = logging.getLogger(__name__)
logger.setLevel(logging.DEBUG)

# create a file handler
handler = logging.FileHandler('hello.log')
handler.setLevel(logging.INFO)

# create a logging format
console_format = '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
formatter = logging.Formatter(console_format)
handler.setFormatter(formatter)

# add the handlers to the logger
logger.addHandler(handler)

logger.debug('Check out this log')
```
```
2017-06-14 16:39:47,989 - __main__ - DEBUG - Check out this log
```

## Use logging in multiple files
To use logging with multiple files without having to repeat the setup code, use a configuration file.

`logging.yaml`
```yaml
version: 1
disable_existing_loggers: False
formatters:
    simple:
        format: "%(asctime)s - %(name)s - %(levelname)s - %(message)s"

handlers:
    console:
        class: logging.StreamHandler
        level: DEBUG
        formatter: simple
        stream: ext://sys.stdout

    info_file_handler:
        class: logging.handlers.RotatingFileHandler
        level: INFO
        formatter: simple
        filename: info.log
        maxBytes: 10485760 # 10MB
        backupCount: 20
        encoding: utf8

    error_file_handler:
        class: logging.handlers.RotatingFileHandler
        level: ERROR
        formatter: simple
        filename: errors.log
        maxBytes: 10485760 # 10MB
        backupCount: 20
        encoding: utf8

loggers:
    my_module:
        level: ERROR
        handlers: [console]
        propagate: no

root:
    level: DEBUG
    handlers: [console, info_file_handler, error_file_handler]
```

Load the configuration file in your main file to configure the logger.

**Note**: You will need to install the `yaml` package. Don't forget to add it to your [requirements](requirements.md) file. 
```
pip install yaml
```

```python
import logging.config

import yaml


def setup_logging():
    """Setup logging configuration.
    """
    with open('logging.yaml', 'rt') as f:
        config = yaml.safe_load(f.read())
    logging.config.dictConfig(config)


if __name__ == '__main__':
    setup_logging()
```

Then create a logger in every file you want to log in.
```python
import logging


logger = logging.getLogger(__name__)


def log():
    logger.info('Check out this log')
```
