# Python
:::{info}
There are a billion of better explanations and tutorials on the internet. This is just a quick overview. Please use your
google skilz to find more information.
:::

Python is a high-level, interpreted, interactive and object-oriented scripting language. Python is designed to be highly readable. It uses English keywords frequently where as other languages use punctuation, and it has fewer syntactical constructions than other languages.
It's a quasi standard in scientific computing and data analysis, as well as neuroscience.
Its has a generally similar syntax to Matlab, but is more powerful and flexible.

## What is Python?
Python is an *interpreted* language, which means you write and run the code directly without needing to compile it first. It is also an open-source language, meaning it is free to use, and there is a large community of developers contributing to it.
Python is known for its clean, readable syntax, which is designed to be easy to write and understand, even if you're new to programming.

## Installation
On linux python is usually preinstalled. To check if you have python installed, open a terminal and type `python --version`. If you don't have python installed, you can download it from the [official website](https://www.python.org/downloads/).

There are many ways to execute python code. 
- Python Interpreter (REPL). To start the 
interpreter, open a terminal and type `python`. You can now type python code and execute it by pressing enter. 
This is easiest for small scripts or for testing code, but tedeous for larger projects.
- Scripts can be executed by running `python script.py` in the terminal. script.py is the name of the text file that contains the python code.
This is useful for larger projects or for scripts that you want to run multiple times.
- For larger projects, you can use an IDE (integrated development environment). There are many IDEs available, 
some of the most popular ones are [PyCharm](https://www.jetbrains.com/pycharm/), [Spyder](https://www.spyder-ide.org/), 
[Jupyter](https://jupyter.org/),  [Atom](https://atom.io/),  etc. Some of those come with a graphical user interface, 
and many additional features like debugging, code completion, git integration, etc.
- Jupyter is a web-based interactive development environment. It's very popular in the scientific community, 
because it allows to combine code, text, and plots in one document. It's also very useful for sharing code and results with others.

## Python packages and pip
Python has a large standard library, but there are many additional packages available that extend the functionality of 
python. These packages can be installed using `pip`, which is the package installer for python.
For example, to install the package `numpy`, you can run `pip install numpy` in the terminal.

## Environment management 
Python has a lot of packages and sometimes different projects require different versions of the same package.
To manage different environments, you can use `conda` or `virtualenv`. 
`conda` is a package manager that can install packages from the Anaconda repository, as well as from other repositories.
`virtualenv` is a tool to create isolated python environments.
Packages installed in one environment are not available in other environments, which can help to avoid conflicts between packages.

- To activate a conda environment, you can run `conda activate environment_name` in the terminal.
- To activate a virtualenv environment, you can run `source environment_name/bin/activate` in the terminal.

## Python 2
just dont 

## Tutorials on using shell terminal
<https://swcarpentry.github.io/shell-novice/>

## Tutorials on git
<https://book.the-turing-way.org/reproducible-research/vcs/vcs-git>



