# Tutorial how to use Markdown and Githubpages
Welcome to short tutorial of how to create Markdown-based documents.

> Documentation is like sex: when it is good, it is very, very good;
and when it is bad, it is better than nothing. 

## Formatting Guide:

# <- Title
## <- Subtitle
### <- heading1
#### <- heading 2.. You get the idea...

**bold text** / _cursive_ / ~~strikedtrough~~ / 

## Code
`
python -m "print('Hello World')"
`
> cd here and there
>

~~~~~~~~
Here comes some code.
~~~~~~~~


## Cross - referencing
[link to file](README.md)

[linkt to website](https://www.optophysiology.uni-freiburg.de/)

## adding image
![test_image.png](images%2Ftest_image.png)


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
