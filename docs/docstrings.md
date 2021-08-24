# Docstrings

> Any docstring is a good docstring

## Why?
Adding a docstring to your function helps anyone looking at your code understand what the function does without analysing the code itself.  

It also helps **you** remember what a function does. For example if you stop working on the project and come back to it, you will know instantly what the function does if it has a docstring. Otherwise you most likely would have forgotten.

## Docstring styles
There are a few docstring styles
- reST
- Google
- NumPy

Which style you choose is completely up to you. It all comes down to personal preference. Generally, I like using the **Google** style. It looks clean, is easy to read, easy to write, and well—it's Google (so you know it's good).

## Google vs NumPy
[Google vs NumPy](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/index.html#google-vs-numpy) concisely compared.

## Example docstrings
I often refer to these examples when I don't know how a component of a docstring should look.  
- [Google example](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html#example-google)
- [NumPy example](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html#example-numpy)

```Python
def google_docstring(param1, param2):
    """This is an example of a Google style docstring.

    Args:
        param1 (str): The first param, it's a string.
        param2 (int): The second param, it's an int.

    Returns:
        This is a description of what is returned.

    Raises:
        KeyError: Raises an exception.
    """

    return 'Use me'
```

```Python
def numpy_docstring(param1, param2):
    """This is an example of a NumPy style docstring.

    Parameters
    ----------
    param1 : list
        The first param, it's a list.
    second : dict
        The second param, it's an dictionary.

    Returns
    -------
    string
        A value in a string.

    Raises
    ------
    KeyError
        Raises an exception when True.
    """

    return 'Or me'
```

## Editor docstring integration
See [IDE's and Editors](editors.md#change-pycharm-docstring-style) for how to get PyCharm to use a docstring style for automatic formatting.
