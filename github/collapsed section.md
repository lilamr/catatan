You can streamline your Markdown by creating a collapsed section with the `<details>` tag.

## [Creating a collapsed section](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections#creating-a-collapsed-section)

You can temporarily obscure sections of your Markdown by creating a collapsed section that the reader can choose to expand. For example, when you want to include technical details in an issue comment that may not be relevant or interesting to every reader, you can put those details in a collapsed section.

Any Markdown within the `<details>` block will be collapsed until the reader clicks

to expand the details.

Within the `<details>` block, use the `<summary>` tag to let readers know what is inside. The label appears to the right of

.

````markdown
<details>

<summary>Tips for collapsed sections</summary>

### You can add a header

You can add text within a collapsed section. 

You can add an image or a code block, too.

```ruby
   puts "Hello World"
```

</details>
````

The Markdown inside the `<summary>` label will be collapsed by default:

![Screenshot of the Markdown above on this page as rendered on GitHub, showing a right-facing arrow and the header "Tips for collapsed sections."](https://docs.github.com/assets/cb-5300/images/help/writing/collapsed-section-view.png)

After a reader clicks

, the details are expanded:

![Screenshot of the Markdown above on this page as rendered on GitHub, indicating that a collapsed section can contain headers, sentences of text, images, and code blocks.](https://docs.github.com/assets/cb-46219/images/help/writing/open-collapsed-section.png)

## [Further reading](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections#further-reading)

- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)
- "[Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)"