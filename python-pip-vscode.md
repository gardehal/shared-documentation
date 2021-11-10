# Python with PIP in Visual Studio Code

Python is a dynamically-typed object oriented high-level general-purpose language, easy to learn and popular with due to it's ease of use and versatility, including scrips, APIs, AI and much more. Combined with PIP, a package manager, and Visual Studio Code along with some relevant extentions, Python is a tool that's  

- [Python official](https://www.python.org)
- [PIP documentation](https://pip.pypa.io/en/stable/)
- [VS Code official](https://code.visualstudio.com)

## Python

## PIP packages

#### Common packages

- os, operating system functions, file manupulation and similar [documentation](https://docs.python.org/3/library/os.html)
- sys, system functions, script arguments, path [documentation](https://docs.python.org/3/library/sys.html)
- cv2/opencv-python, an image manipulation package [documentation](https://pypi.org/project/opencv-python/)
- requests, web requests [documentation](https://pypi.org/project/requests/)
- time, controlling time [documentation](https://docs.python.org/3/library/time.html)
- datetime, controlling dates and datetime [documentation](https://docs.python.org/3/library/datetime.html)
- enum, for enums [documentation](https://docs.python.org/3/library/enum.html)

#### Personal packages

- Utilities with miscellaneous methods [GitHub](https://github.com/grdall/python-packages/tree/main/myutil)

## PIP commands

> :information_source: **For some reason, the propper syntax ```pip help``` does not work for my environment, but ```python -m pip help``` does.**

- PIP help
  - $ `pip help`
- Install a package
  - $ `pip install [package-name]`
- Uninstall a package
  - $ `pip uninstall [package-name]`
- List all packages
  - $ `pip list`
- Update a package
  - $ `pip install --upgrade [package-name]`
- Update PIP
  - $ `pip install --upgrade pip`

## VS Code

Since VS Code is a general purpose editor, a lighter language like Python can be used along it without losing key features like integration to databases, server, or similar.
There are other editors which go along with Python, such as Sublime, Atom, or the heavier PyCharm from JetBrains.

#### VS Code extentions

- MagicPython
- Python Extension Pack
- Pylance
- Python
- Python for VSCode
- Code Spell Checker
- 