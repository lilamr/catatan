### 1. Install TeX Live

TeX Live is a TeX distribution to get up and running with the TeX document production system. To install it, once you're in the terminal, enter the following command:

`sudo apt-get install texlive-full`

Then, type your _sudo_ password and you'll have installed Tex Live. This operation takes time.

### 2. Install Texmaker

I recommend using a specific editor for LaTeX. My favorite is Texmaker, a cross-platform open source LaTeX editor. To install it, go to the terminal and execute this command:

`sudo apt-get install texmaker`

### 3. Create your first document

Open Texmaker and click on **File, New**. Then put the following code:

`\documentclass{article} \begin{document} Hello, world! \end{document}`

Now save the document as a _tex_ file going to **File, Save**. Finally, compile the document clicking on **Tools, PDFLaTeX**. Make sure the PDF file has been created and it's working. And that's it! You've created your first LaTeX document!

