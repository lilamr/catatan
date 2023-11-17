Use Markdown to display mathematical expressions on GitHub.

## [About writing mathematical expressions](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions#about-writing-mathematical-expressions)

To enable clear communication of mathematical expressions, GitHub supports LaTeX formatted math within Markdown. For more information, see [LaTeX/Mathematics](http://en.wikibooks.org/wiki/LaTeX/Mathematics) in Wikibooks.

GitHub's math rendering capability uses MathJax; an open source, JavaScript-based display engine. MathJax supports a wide range of LaTeX macros, and several useful accessibility extensions. For more information, see [the MathJax documentation](http://docs.mathjax.org/en/latest/input/tex/index.html#tex-and-latex-support) and [the MathJax Accessibility Extensions Documentation](https://mathjax.github.io/MathJax-a11y/docs/#reader-guide).

Mathematical expressions rendering is available in GitHub Issues, GitHub Discussions, pull requests, wikis, and Markdown files.

## [Writing inline expressions](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions#writing-inline-expressions)

There are two options for delimiting a math expression inline with your text. You can either surround the expression with dollar symbols (`$`), or start the expression with `` $` `` and end it with `` `$ ``. The latter syntax is useful when the expression you are writing contains characters that overlap with markdown syntax. For more information, see "[Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)."

```text
This sentence uses `$` delimiters to show math inline:  $\sqrt{3x-1}+(1+x)^2$
```

![Screenshot of rendered Markdown showing how a mathematical expression displays on GitHub. The equation is the square root of 3 x minus 1 plus open paren 1 plus x close paren squared.](https://docs.github.com/assets/cb-6685/images/help/writing/inline-math-markdown-rendering.png)

```text
This sentence uses $\` and \`$ delimiters to show math inline:  $`\sqrt{3x-1}+(1+x)^2`$
```

![Screenshot of rendered Markdown showing how a mathematical expression displays inline on GitHub. The equation is the square root of 3 x minus 1 plus open paren 1 plus x close paren squared.](https://docs.github.com/assets/cb-10142/images/help/writing/inline-backtick-math-markdown-rendering.png)

## [Writing expressions as blocks](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions#writing-expressions-as-blocks)

To add a math expression as a block, start a new line and delimit the expression with two dollar symbols `$$`.

```text
**The Cauchy-Schwarz Inequality**
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$
```

![Screenshot of rendered Markdown showing how a complex equation displays on GitHub. The bolded text reads "The Cauchy-Schwarz Inequality". Below the text, there is an equation showing open paren the sum from k equals 1 to n of a sub k b sub k close paren squared is less than or equal to open paren the sum from k equals 1 to n of a sub k squared close paren times open paren the sum from k equals 1 to n of b sub k squared close paren.](https://docs.github.com/assets/cb-4054/images/help/writing/math-expression-as-a-block-rendering.png)

Alternatively, you can use the ` ```math ` code block syntax to display a math expression as a block. With this syntax, you don't need to use `$$` delimiters. The following will render the same as above:

````text
**The Cauchy-Schwarz Inequality**

```math
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
```
````

## [Writing dollar signs in line with and within mathematical expressions](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions#writing-dollar-signs-in-line-with-and-within-mathematical-expressions)

To display a dollar sign as a character in the same line as a mathematical expression, you need to escape the non-delimiter `$` to ensure the line renders correctly.

- Within a math expression, add a `\` symbol before the explicit `$`.
    
    ```text
    This expression uses `\$` to display a dollar sign: $\sqrt{\$4}$
    ```
    
    ![Screenshot of rendered Markdown showing how a backslash before a dollar sign displays the sign as part of a mathematical expression.](https://docs.github.com/assets/cb-30316/images/help/writing/dollar-sign-within-math-expression.png)
    
- Outside a math expression, but on the same line, use span tags around the explicit `$`.
    
    ```text
    To split <span>$</span>100 in half, we calculate $100/2$
    ```
    
    ![Screenshot of rendered Markdown showing how span tags around a dollar sign display the sign as inline text rather than part of a mathematical equation.](https://docs.github.com/assets/cb-22387/images/help/writing/dollar-sign-inline-math-expression.png)
    

## [Further reading](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions#further-reading)

- [The MathJax website](http://mathjax.org)
- [Getting started with writing and formatting on GitHub](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github)
- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)