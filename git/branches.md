Often, in software development, a new feature or an attempt to solve a problem may lead the code development process off on a tangent. This concept, known as branching, is so common it's part of the fundamental design philosophy of Git.

Assuming you have no uncommitted changes in your project (create a new commit if necessary) try this command:

`git checkout -b trial_by_fire`

This creates a new branch representing the current point in the history. Having a branch allows you to continue from this point without affecting the base point from which this stems.

Let’s make this clearer by taking a look at an example. Get a list of all the files Git is tracking in this project:

`git ls-files`

Now, issue the delete command for each file:

`git rm <filename>`

Then, verify you have removed everything with:

`git status`

And make a new commit:

`git commit -am “Deleted everything”`

Now we can restore our project:

`git checkout master`

Voila! We've restored everything back to its original state.

`master` is always the name of the main branch—the one from which you always start. Everything else branches from that. If you form an image in your mind of a railway system it might help to understand the concept of branching. Each station on the railway is like a commit in the Git history. You can travel to any station (commit) along the system (branches) to arrive at a previous location (which, in our case, is a state of the set of files). And there's no limit to the number of branches you can create. You can always see the list of branches with:

`git branch`

There will be an asterisk to show you which branch is current. In order to check out a branch so you can work on it you simply enter:

`git checkout <branchname>`
