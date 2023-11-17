When you want to see the entire history of your project, and locate a particular point to check out, simply issue the command:

`git log`

You may notice that each entry—regardless of the commit message you created for it—has a unique signature, called a hash, which looks something like this:

`c178771270d4`

Your hashes will be different than the ones shown above. Each hash is generated automatically by Git, and each one uniquely identifies a particular commit. You can use these signatures to revert to the various states in the project’s history.

When we made our commits earlier, you might recall that we added messages to them to make them easier to find. Below, you'll learn a better way to access your project's various states.

Try it out using our current project. Although the actual hash you use will be different, the command will look something like this:

`git checkout c178771270d4`

Whenever you issue the checkout command, the set of files that are contained in that commit are restored to whatever state they were at the time of the commit. This means any files you currently have with the same name as those in that commit will be completely overwritten.

You don't actually need to type out the full (very long!) hash. Git is smart enough to work out which commit you mean if you only type out the first few characters, as long as that short string is unambiguous (in other words, no other commit also starts with those characters). The first few characters will often suffice, and 8 characters is normally more than enough.
