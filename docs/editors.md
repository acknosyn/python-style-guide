# IDE's and Editors

> TL;DR: Use PyCharm.

"The best IDE or editor" is a subjective topic. In short, if you know what you're doing with Python (including adhering to the style guide), use whatever you're most efficient with. Otherwise, I'd almost always recommend JetBrains' [PyCharm](https://www.jetbrains.com/pycharm/).

## Why PyCharm?
PyCharm is a **complete IDE** dedicated to Python. **It works out of the box**, with minimal configuration, and already includes almost everything mentioned in the [Style Guide](style-guide.md).
* Free
* Pre-configured with a [PEP8](https://www.python.org/dev/peps/pep-0008/) code linter
* Everything you'd expect from an IDE, including
  * Language-aware code completion, error detection, and on-the-fly code fixes
  * Go to declarations, usages, implementations variables and functions
  * Intelligent refactoring
  * Built in terminal
* Built for Python, every feature is with Python in mind

## Change PyCharm docstring style
PyCharm generates a new template docstring every time you type `""" + <enter>` 3 quotes and then enter at the top of a function. You can change the docstring style used for templates.

To do this, go to preferences  
`PyCharm > Preferences` (`⌘,`)  
Then Python Integrated Tools  
`Tools > Python Integrated Tools`  
Under `Docstrings` you can change docstring format there.

## Other suggestions
If you don't use PyCharm, you'll have to install a few plugins for your editor. There's too many out there to give specific advice. Just remember, with any text editor, the more plugins you install, the slower it gets.

Some essential and recommended plugins
- Python language support
- A Python code linter
- Docstring templating support
