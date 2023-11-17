When you're in the process of making changes, and committing them to save various states, it's easy to lose track of what has been updated, changed or committed. Git has a solution this kind of version blindness: a useful command—and arguably the second most used in Git—called status. It enables you to see what changes have been made and whether they've been committed to the Git repository. Try this:

`git status`

Now modify one of the files that's being tracked by Git. Then issue the `git status` command a second time. Make another commit, and check the status again.

Finally, add another file to your project (you could create a new text file, such as README), and check the status one more time. Next, add the file to Git for tracking with:

`git add <filename>`

And, yes, you guessed it, check the status again:

`git status`

As you can see, this command allows you to find out what changes have been made and committed and so maintain your bearings on what Git believes it's tracking.

By this stage your original file, `TheFirstFile.txt`, should have gone through many changes—all of which have been stored in the Git history. Make sure you have committed any recent changes. Double-check there are no outstanding changes with the status command:

`git status`

It should say "nothing to commit, working directory clean." if there are no outstanding changes. Take a look at your history to locate the hash of the very first commit you made:

`git log`

The command to check out that “Initial Commit” would be the following (but don't do it now):

`git checkout c178771270d`

Instead, try this command:

`git diff c178771270d`

The diff command is intended to show you the differences between two commits. Specifically, it'll show exactly what changed in each and every file. Notice the plus (+) and minus (-) symbols. They indicate which files and which lines within each file were added and removed, respectively. This can be valuable information. Git provides the capability to retrieve those individual changes en masse or selectively. That's where some of the more complex commands (and the concept of merging) would apply.

