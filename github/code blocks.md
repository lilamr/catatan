Share samples of code with fenced code blocks and enabling syntax highlighting.

## [Fenced code blocks](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#fenced-code-blocks)

You can create fenced code blocks by placing triple backticks ` ``` ` before and after the code block. We recommend placing a blank line before and after code blocks to make the raw formatting easier to read.

```
function test() {
  console.log("notice the blank line before this function?");
}
```

![Screenshot of rendered GitHub Markdown showing how triple backticks cause a code block to render in raw formatting. The block begins with "function test() {."](https://docs.github.com/assets/cb-30176/images/help/writing/fenced-code-block-rendered.png)

**Tip:** To preserve your formatting within a list, make sure to indent non-fenced code blocks by eight spaces.

To display triple backticks in a fenced code block, wrap them inside quadruple backticks.

````
```
Look! You can see my backticks.
```
````

![Screenshot of rendered GitHub Markdown showing how quadruple backticks cause triple backticks surrounding a code block to remain visible. The block reads, "Look! You can see my backticks."](https://docs.github.com/assets/cb-4747/images/help/writing/fenced-code-show-backticks-rendered.png)

If you are frequently editing code snippets and tables, you may benefit from enabling a fixed-width font in all comment fields on GitHub. For more information, see "[About writing and formatting on GitHub](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github#enabling-fixed-width-fonts-in-the-editor)."

## [Syntax highlighting](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting)

You can add an optional language identifier to enable syntax highlighting in your fenced code block.

Syntax highlighting changes the color and style of source code to make it easier to read.

For example, to syntax highlight Ruby code:

````
```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```
````

This will display the code block with syntax highlighting:

![Screenshot of three lines of Ruby code as displayed on GitHub. Elements of the code display in purple, blue, and red type, making the lines more visually scannable.](https://docs.github.com/assets/cb-19382/images/help/writing/code-block-syntax-highlighting-rendered.png)

We use [Linguist](https://github.com/github-linguist/linguist) to perform language detection and to select [third-party grammars](https://github.com/github-linguist/linguist/blob/master/vendor/README.md) for syntax highlighting. You can find out which keywords are valid in [the languages YAML file](https://github.com/github-linguist/linguist/blob/master/lib/linguist/languages.yml).

## [Creating diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#creating-diagrams)

You can also use code blocks to create diagrams in Markdown. GitHub supports Mermaid, GeoJSON, TopoJSON, and ASCII STL syntax. For more information, see "[Creating diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams)."

## [Further reading](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#further-reading)

- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)
- "[Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)"