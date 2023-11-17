The commit is fundamental to Git and source control, and is the most common action you will take using it. A commit is a snapshot in time, and represents a reproducible state of your project. The various commits you make during a project constitute the project’s history.

Let’s add some files to our project, and then look at how to tell Git which files you want it to keep track of. We will create a text file called `TheFirstFile.txt`. In Linux this is as easy as typing:

`touch TheFirstFile.txt`

Now let’s add some content to this file. Navigating on your computer to the `Documents > HaloWhirled` folder. Open the new `TheFirstFile.txt` file in a text editor and type the year you were born. On a new line, type your favorite flavor of ice cream, for example:

`I was born in 1842.`
`My favorite flavor of ice cream is vanilla.`

Once you’re done, save the file. Now let’s return to the command line tool and tell Git to start tracking the history of this new file. Type the command:

`git add TheFirstFile.txt`

Git has happily accepted your command and executed it instantly. Git now knows that you are going to track the progress of this file. Let’s capture the current state of this file for all time by performing our first commit. Enter the following:

`git commit -am "Initial Commit"`

A commit has at least two parts: the file(s) to be included and a commit "message." The message is just a handy label (one or more tags, a description, or whatever) that we add to help us when searching through a long list of commits in the history.

Once again, open `TheFirstFile.txt` file in your text editor. Delete the text you typed earlier and add some new text. It doesn't matter what it is. Save and close it, then, back in your command line tool, type this:

`git commit -am "Changed all the text"`

You have just begun to develop a history in Git. The command above has committed the new changes to this project’s history. This example of using Git has involved only one file, but this process applies equally to any number of files and/or folders in your project.

Let's make it a bit more "real world" project. Go to your `HaloWhirled` project folder and place a new web page file inside, calling it `index.html`. (Use your preferred text editor to create this file.) While you're at it, create a new folder called images inside the HaloWhirled folder. Now go back to your command line tool to commit these changes by typing:

`git add index.html`
`git add images/`
`git commit -am "A Simple Web Project"`

Our little project is now the beginnings of a simple web site. Next we’ll explore how to view the history of what we’ve done so far.