Let’s say we now want to use Git to access a previous state of our project. To do so, we can use the checkout command. In the command line, type the following:

`git checkout HEAD^`

To see the effect of checkout, open the `TheFirstFile.txt` file in your text editor again. You'll see that it has returned to its previous state.

It’s important to note here that we haven't deleted any of our project's history by running the checkout command. The commits you make to your history are permanent. Indeed, there's nothing you can do in Git to make them disappear.

It's also worth noting that using checkout in this way isn't how we'd normally return to a project's earlier state. It's just a little cheat we're employing here to keep things simple.