## What is Markdown?[](https://www.markdownguide.org/getting-started/#what-is-markdown)

Markdown is a lightweight markup language that you can use to add formatting elements to plaintext text documents. Created by [John Gruber](https://daringfireball.net/projects/markdown/) in 2004, Markdown is now one of the world’s most popular markup languages.

Using Markdown is different than using a [WYSIWYG](https://en.wikipedia.org/wiki/WYSIWYG) editor. In an application like Microsoft Word, you click buttons to format words and phrases, and the changes are visible immediately. Markdown isn’t like that. When you create a Markdown-formatted file, you add Markdown syntax to the text to indicate which words and phrases should look different.

For example, to denote a heading, you add a number sign before it (e.g., `# Heading One`). Or to make a phrase bold, you add two asterisks before and after it (e.g., `**this text is bold**`). It may take a while to get used to seeing Markdown syntax in your text, especially if you’re accustomed to WYSIWYG applications. The screenshot below shows a Markdown file displayed in the [Visual Studio Code text editor](https://www.markdownguide.org/tools/vscode/).

![Markdown file in the Visual Studio Code text editor](https://mdg.imgix.net/assets/images/vscode.png)

You can add Markdown formatting elements to a plaintext file using a text editor application. Or you can use one of the many Markdown applications for macOS, Windows, Linux, iOS, and Android operating systems. There are also several web-based applications specifically designed for writing in Markdown.

Depending on the application you use, you may not be able to preview the formatted document in real time. But that’s okay. [According to Gruber](https://daringfireball.net/projects/markdown/), Markdown syntax is designed to be readable and unobtrusive, so the text in Markdown files can be read even if it isn’t rendered.

> The overriding design goal for Markdown’s formatting syntax is to make it as readable as possible. The idea is that a Markdown-formatted document should be publishable as-is, as plain text, without looking like it’s been marked up with tags or formatting instructions.

## Why Use Markdown?[](https://www.markdownguide.org/getting-started/#why-use-markdown)

You might be wondering why people use Markdown instead of a WYSIWYG editor. Why write with Markdown when you can press buttons in an interface to format your text? As it turns out, there are several reasons why people use Markdown instead of WYSIWYG editors.

- Markdown can be used for everything. People use it to create [websites](https://www.markdownguide.org/getting-started/#websites), [documents](https://www.markdownguide.org/getting-started/#documents), [notes](https://www.markdownguide.org/getting-started/#notes), [books](https://www.markdownguide.org/getting-started/#books), [presentations](https://www.markdownguide.org/getting-started/#presentations), [email messages](https://www.markdownguide.org/getting-started/#email), and [technical documentation](https://www.markdownguide.org/getting-started/#documentation).
    
- Markdown is portable. Files containing Markdown-formatted text can be opened using virtually any application. If you decide you don’t like the Markdown application you’re currently using, you can import your Markdown files into another Markdown application. That’s in stark contrast to word processing applications like Microsoft Word that lock your content into a proprietary file format.
    
- Markdown is platform independent. You can create Markdown-formatted text on any device running any operating system.
    
- Markdown is future proof. Even if the application you’re using stops working at some point in the future, you’ll still be able to read your Markdown-formatted text using a text editing application. This is an important consideration when it comes to books, university theses, and other milestone documents that need to be preserved indefinitely.
    
- Markdown is everywhere. Websites like [Reddit](https://www.markdownguide.org/tools/reddit/) and GitHub support Markdown, and lots of desktop and web-based applications support it.
    

## Kicking the Tires[](https://www.markdownguide.org/getting-started/#kicking-the-tires)

The best way to get started with Markdown is to use it. That’s easier than ever before thanks to a variety of free tools.

You don’t even need to download anything. There are several online Markdown editors that you can use to try writing in Markdown. [Dillinger](https://dillinger.io/) is one of the best online Markdown editors. Just open the site and start typing in the left pane. A preview of the rendered document appears in the right pane.

![Dillinger Markdown editor](https://mdg.imgix.net/assets/images/dillinger.png)

You’ll probably want to keep the Dillinger website open as you read through this guide. That way you can try the syntax as you learn about it. After you’ve become familiar with Markdown, you may want to use a Markdown application that can be installed on your desktop computer or mobile device.

## How Does it Work?[](https://www.markdownguide.org/getting-started/#how-does-it-work)

Dillinger makes writing in Markdown easy because it hides the stuff happening behind the scenes, but it’s worth exploring how the process works in general.

When you write in Markdown, the text is stored in a plaintext file that has an `.md` or `.markdown` extension. But then what? How is your Markdown-formatted file converted into HTML or a print-ready document?

The short answer is that you need a _Markdown application_ capable of processing the Markdown file. There are lots of applications available — everything from simple scripts to desktop applications that look like Microsoft Word. Despite their visual differences, all of the applications do the same thing. Like Dillinger, they all convert Markdown-formatted text to HTML so it can be displayed in web browsers.

Markdown applications use something called a _Markdown processor_ (also commonly referred to as a “parser” or an “implementation”) to take the Markdown-formatted text and output it to HTML format. At that point, your document can be viewed in a web browser or combined with a style sheet and printed. You can see a visual representation of this process below.

**Note:** The Markdown application and processor are two separate components. For the sake of brevity, I've combined them into one element ("Markdown app") in the figure below.

![The Markdown Process](https://mdg.imgix.net/assets/images/markdown-flowchart.png)

To summarize, this is a four-part process:

1. Create a Markdown file using a text editor or a dedicated Markdown application. The file should have an `.md` or `.markdown` extension.
2. Open the Markdown file in a Markdown application.
3. Use the Markdown application to convert the Markdown file to an HTML document.
4. View the HTML file in a web browser or use the Markdown application to convert it to another file format, like PDF.

From your perspective, the process will vary somewhat depending on the application you use. For example, Dillinger essentially combines steps 1-3 into a single, seamless interface — all you have to do is type in the left pane and the rendered output magically appears in the right pane. But if you use other tools, like a text editor with a static website generator, you’ll find that the process is much more visible.

## What’s Markdown Good For?[](https://www.markdownguide.org/getting-started/#whats-markdown-good-for)

Markdown is a fast and easy way to take notes, create content for a website, and produce print-ready documents.

It doesn’t take long to learn the Markdown syntax, and once you know how to use it, you can write using Markdown just about everywhere. Most people use Markdown to create content for the web, but Markdown is good for formatting everything from email messages to grocery lists.

Here are some examples of what you can do with Markdown.

### Websites[](https://www.markdownguide.org/getting-started/#websites)

Markdown was designed for the web, so it should come as no surprise that there are plenty of applications specifically designed for creating website content.

If you’re looking for the simplest possible way to create a website with Markdown files, check out [blot.im](https://blot.im). After you sign up for Blot, it creates a Dropbox folder on your computer. Just drag and drop your Markdown files into the folder and — poof! — they’re on your website. It couldn’t be easier.

If you’re familiar with HTML, CSS, and version control, check out [Jekyll](https://www.markdownguide.org/tools/jekyll/), a popular static site generator that takes Markdown files and builds an HTML website. One advantage to this approach is that [GitHub Pages](https://www.markdownguide.org/tools/github-pages/) provides free hosting for Jekyll-generated websites. If Jekyll isn’t your cup of tea, just pick one of the [many other static site generators available](https://jamstack.org/generators/).

**Note:** I used Jekyll to create the _Markdown Guide_. You can view the source code on [GitHub](https://github.com/mattcone/markdown-guide).

If you’d like to use a content management system (CMS) to power your website, take a look at [Ghost](https://www.markdownguide.org/tools/ghost/). It’s a free and open-source blogging platform with a nice Markdown editor. If you’re a WordPress user, you’ll be happy to know there’s [Markdown support](https://wordpress.com/support/wordpress-editor/blocks/markdown-block/) for websites hosted on WordPress.com. Self-hosted WordPress sites can use the [Jetpack plugin](https://jetpack.com/support/jetpack-blocks/markdown/).

### Documents[](https://www.markdownguide.org/getting-started/#documents)

Markdown doesn’t have all the bells and whistles of word processors like Microsoft Word, but it’s good enough for creating basic documents like assignments and letters. You can use a Markdown document authoring application to create and export Markdown-formatted documents to PDF or HTML file format. The PDF part is key, because once you have a PDF document, you can do anything with it — print it, email it, or upload it to a website.

Here are some Markdown document authoring applications I recommend:

- **Mac:** [MacDown](https://www.markdownguide.org/tools/macdown/), [iA Writer](https://www.markdownguide.org/tools/ia-writer/), or [Marked 2](https://www.markdownguide.org/tools/marked-2/)
- **iOS / Android:** [iA Writer](https://www.markdownguide.org/tools/ia-writer/)
- **Windows:** [ghostwriter](https://kde.github.io/ghostwriter/) or [Markdown Monster](https://markdownmonster.west-wind.com/)
- **Linux:** [ReText](https://github.com/retext-project/retext) or [ghostwriter](https://kde.github.io/ghostwriter/)
- **Web:** [Dillinger](https://www.markdownguide.org/tools/dillinger/) or [StackEdit](https://www.markdownguide.org/tools/stackedit/)

**Tip:** [iA Writer](https://ia.net/writer/templates/) provides templates for previewing, printing, and exporting Markdown-formatted documents. For example, the "Academic – MLA Style" template indents paragraphs and adds double sentence spacing.

### Notes[](https://www.markdownguide.org/getting-started/#notes)

In nearly every way, Markdown is the ideal syntax for taking notes. Sadly, [Evernote](https://evernote.com/) and [OneNote](https://www.onenote.com/), two of the most popular note applications, don’t currently support Markdown. The good news is that several other note applications _do_ support Markdown:

- [Obsidian](https://www.markdownguide.org/tools/obsidian/) is a popular Markdown note-taking application loaded with features.
- [Simplenote](https://www.markdownguide.org/tools/simplenote/) is a free, barebones note-taking application available for every platform.
- [Notable](https://www.markdownguide.org/tools/notable/) is a note-taking application that runs on a variety of platforms.
- [Bear](https://www.markdownguide.org/tools/bear/) is an Evernote-like application available for Mac and iOS devices. It doesn’t exclusively use Markdown by default, but you can enable Markdown compatibility mode.
- [Joplin](https://www.markdownguide.org/tools/joplin/) is a note taking application that respects your privacy. It’s available for every platform.
- [Boostnote](https://www.markdownguide.org/tools/boostnote/) bills itself as an “open source note-taking app designed for programmers.”

If you can’t part with Evernote, check out [Marxico](https://marxi.co/), a subscription-based Markdown editor for Evernote, or use [Markdown Here](https://www.markdownguide.org/tools/markdown-here/) with the Evernote website.

### Books[](https://www.markdownguide.org/getting-started/#books)

Looking to self-publish a novel? Try [Leanpub](https://leanpub.com/), a service that takes your Markdown-formatted files and turns them into an electronic book. Leanpub outputs your book in PDF, EPUB, and MOBI file format. If you’d like to create paperback copies of your book, you can upload the PDF file to another service such as [Kindle Direct Publishing](https://kdp.amazon.com). To learn more about writing and self-publishing a book using Markdown, read [this blog post](https://medium.com/techspiration-ideas-making-it-happen/how-i-wrote-and-published-my-novel-using-only-open-source-tools-5cdfbd7c00ca).

### Presentations[](https://www.markdownguide.org/getting-started/#presentations)

Believe it or not, you can generate presentations from Markdown-formatted files. Creating presentations in Markdown takes a little getting used to, but once you get the hang of it, it’s a lot faster and easier than using an application like PowerPoint or Keynote. [Remark](https://remarkjs.com) ([GitHub project](https://github.com/gnab/remark)) is a popular browser-based Markdown slideshow tool, as are [Cleaver](https://jdan.github.io/cleaver/) ([GitHub project](https://github.com/jdan/cleaver)) and [Marp](https://marp.app/) ([GitHub project](https://github.com/marp-team/marp)). If you use a Mac and would prefer to use an application, check out [Deckset](https://www.decksetapp.com/) or [Hyperdeck](https://hyperdeck.io/).

### Email[](https://www.markdownguide.org/getting-started/#email)

If you send a lot of email and you’re tired of the formatting controls available on most email provider websites, you’ll be happy to learn there’s an easy way to write email messages using Markdown. [Markdown Here](https://www.markdownguide.org/tools/markdown-here/) is a free and open-source browser extension that converts Markdown-formatted text into HTML that’s ready to send.

### Collaboration[](https://www.markdownguide.org/getting-started/#collaboration)

Collaboration and team messaging applications are a popular way of communicating with coworkers and friends at work and home. These applications don’t utilize all of Markdown’s features, but the features they do provide are fairly useful. For example, the ability to bold and italicize text without using the WYSIWYG interface is pretty handy. [Slack](https://www.markdownguide.org/tools/slack/), [Discord](https://www.markdownguide.org/tools/discord/), [Wiki.js](https://www.markdownguide.org/tools/wiki-js/), and [Mattermost](https://www.markdownguide.org/tools/mattermost/) are all good collaboration applications.

### Documentation[](https://www.markdownguide.org/getting-started/#documentation)

Markdown is a natural fit for technical documentation. Companies like GitHub are increasingly switching to Markdown for their documentation — check out their [blog post](https://github.com/blog/1939-how-github-uses-github-to-document-github) about how they migrated their Markdown-formatted documentation to [Jekyll](https://www.markdownguide.org/tools/jekyll/). If you write documentation for a product or service, take a look at these handy tools:

- [Read the Docs](https://readthedocs.org) can generate a documentation website from your open source Markdown files. Just connect your GitHub repository to their service and push — Read the Docs does the rest. They also have a [service for commercial entities](https://readthedocs.com/).
- [MkDocs](https://www.markdownguide.org/tools/mkdocs/) is a fast and simple static site generator that’s geared towards building project documentation. Documentation source files are written in Markdown and configured with a single YAML configuration file. MkDocs has several [built in themes](https://www.mkdocs.org/user-guide/styling-your-docs/), including a port of the [Read the Docs](https://readthedocs.org/) documentation theme for use with MkDocs. One of the newest themes is [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).
- [Docusaurus](https://www.markdownguide.org/tools/docusaurus/) is a static site generator designed exclusively for creating documentation websites. It supports translations, search, and versioning.
- [VuePress](https://vuepress.vuejs.org/) is a static site generator powered by [Vue](https://vuejs.org/) and optimized for writing technical documentation.
- [Jekyll](https://www.markdownguide.org/tools/jekyll/) was mentioned earlier in the section on websites, but it’s also a good option for generating a documentation website from Markdown files. If you go this route, be sure to check out the [Jekyll documentation theme](https://idratherbewriting.com/documentation-theme-jekyll/).

## Flavors of Markdown[](https://www.markdownguide.org/getting-started/#flavors-of-markdown)

One of the most confusing aspects of using Markdown is that practically every Markdown application implements a slightly different version of Markdown. These variants of Markdown are commonly referred to as _flavors_. It’s your job to master whatever flavor of Markdown your application has implemented.

To wrap your head around the concept of Markdown flavors, it might help to think of them as language dialects. People in New York City speak English just like the people in London, but there are substantial differences between the dialects used in both cities. The same is true for people using different Markdown applications. Using [Dillinger](https://www.markdownguide.org/tools/dillinger/) to write with Markdown is a vastly different experience than using [Ulysses](https://www.markdownguide.org/tools/ulysses/).

Practically speaking, this means you never know exactly what a company means when they say they support “Markdown.” Are they talking about only the [basic syntax elements](https://www.markdownguide.org/basic-syntax/), or all of the basic and [extended syntax elements](https://www.markdownguide.org/extended-syntax/) combined, or some arbitrary combination of syntax elements? You won’t know until you read the documentation or start using the application.

If you’re just starting out, the best advice I can give you is to pick a Markdown application with good Markdown support. That’ll go a long way towards maintaining the portability of your Markdown files. You might want to store and use your Markdown files in other applications, and to do that you need to start with an application that provides good support. You can use the [tool directory](https://www.markdownguide.org/tools/) to find an application that fits the bill.

## Additional Resources[](https://www.markdownguide.org/getting-started/#additional-resources)

There are lots of resources you can use to learn Markdown. Here are some other introductory resources:

- [John Gruber’s Markdown documentation](https://daringfireball.net/projects/markdown/). The original guide written by the creator of Markdown.
- [Markdown Tutorial](https://www.markdowntutorial.com/). An open source website that allows you to try Markdown in your web browser.
- [Awesome Markdown](https://github.com/mundimark/awesome-markdown). A list of Markdown tools and learning resources.
- [Typesetting Markdown](https://dave.autonoma.ca/blog/2019/05/22/typesetting-markdown-part-1). A multi-part series that describes an ecosystem for typesetting Markdown documents using [pandoc](https://pandoc.org/) and [ConTeXt](https://www.contextgarden.net/).