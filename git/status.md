When you're in the process of making changes, and committing them to save various states, it's easy to lose track of what has been updated, changed or committed. Git has a solution this kind of version blindness: a useful command—and arguably the second most used in Git—called status. It enables you to see what changes have been made and whether they've been committed to the Git repository. Try this:

`git status`

Now modify one of the files that's being tracked by Git. Then issue the `git status` command a second time. Make another commit, and check the status again.

Finally, add another file to your project (you could create a new text file, such as README), and check the status one more time. Next, add the file to Git for tracking with:

`git add <filename>`

And, yes, you guessed it, check the status again:

`git status`

As you can see, this command allows you to find out what changes have been made and committed and so maintain your bearings on what Git believes it's tracking.

