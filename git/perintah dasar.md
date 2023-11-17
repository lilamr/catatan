The most common way to use Git is via the “command line”. The command line is a simple program that you find on all computers. It allows you to write instructions for the computer in a very basic way, without pretty graphics, buttons and so on. You just write text commands. This can be a bit scary for a beginner, but using the command line is definitely the best way to use Git.

There are “graphic user interface” (GUI) programs available as an alternative programs that provide you with buttons to press and pretty interfaces but we encourage you at least to learn the basics of Git using the command line. All the same, you can find a useful list of GUI options at the official Git website (http://git-scm.com/downloads/guis).

So now you have your command line open, it’s time to begin using Git. However, before Git will allow you to interact with it on any project, you must set up two very simple configuration options: You will identify yourself within Git by adding your name and an email address. These can even be fabricated values if you prefer, such as “A User” and “User@email.com." At the command line, type the following:

`git config --global user.name "Your Name Here"`
`git config --global user.email "your_email@example.com"`

Once you've entered the required commands, you'll need to press Enter.

Now that you and Git have become acquainted, let’s start by creating a project directory (folder) on your system, and call it `HaloWhirled`. You can create this folder anywhere you like. Let’s say, for example, that there’s a folder on your computer called Documents, and that's where you want to store this test project. To do that, type the following in the command line:

`cd Documents`
`mkdir HaloWhirled`

Now that we have created the Halo Whirled folder, go into that folder by typing:

`cd HaloWhirled`

Now we are inside our new project folder. 

We haven’t used Git at all until now. So let's tell Git to get to work in this folder. Each command to Git consist of two words, and the first is always git. To get Git going in our new project, we simply need to enter:

`git init`

We've already set up a new project, and Git is ready to help us manage it!

Tahapan GIT:
1. Commit [[commit]]
2. Checkout [[checkout]]
3. Log [[git/log]]
4. Status [[git/status]]
5. 

