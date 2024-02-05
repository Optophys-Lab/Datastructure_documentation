# Tutorial how to use Markdown and Githubpages
> Documentation is like sex: when it is good, it is very, very good;
and when it is bad, it is better than nothing. 

This page is currently being hosted via github pages. The html is build using [jupyter-book](https://jupyterbook.org).

~~~~~~~~
pip install -U jupyter-book
~~~~~~~~

This adds search and index functionality. Furthermore, it allows straightforward integration of jupyter notebooks.
Currently the main branch only contains text and jupyter_book one additionally contains the required files for building the site.
**_toc.yaml** defines the table of contents of the book and **_config.yaml** the configuration.
**deploy.yaml** defines the workflow for github-actions to build and deploy the pages.

To integrate new content from main, merge main into jupyter_book and add new files to **_toc.yaml**.
You can try to build locally using jupyter-book from inside the repository:

~~~~~~~~
jupyter-book build ./
~~~~~~~~



## Formatting Guide for markdown(MD) files
see also <https://jupyterbook.org/en/stable/customize/config.html>

# <- Title
## <- Subtitle
### <- heading1
#### <- heading 2.. You get the idea...

**bold text** / _cursive_ / ~~strikedtrough~~ / 

## Lists

- item1
- item2
  - subitem1
    - subsubitem1

## Code
`
python -m "print('Hello World')"
`
> cd here and there
>

~~~~~~~~
Here comes some code.
~~~~~~~~
using language specific highlighting
~~~~~~~~{python}
import time
time.sleep(int(5))
print(sleep.__dict__)
~~~~~~~~


## Cross - referencing
[link to file](README.md)

[linkt to website](https://www.optophysiology.uni-freiburg.de/)

## adding image
![logo-optophysiology-light.svg](images/logo-optophysiology-light.svg)

## math

$$
\begin{aligned}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{aligned}
$$

## How to document code
Write docstrings ! 
