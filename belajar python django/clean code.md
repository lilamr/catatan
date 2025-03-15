“Good code doesn’t just work. It’s simple, modular, testable, maintainable, thoughtful.” (Lyman, p. 41)

“A good question to ask yourself when writing code is: will this be easy to delete when we don’t need it any more? If it’s deeply nested, copied-and-pasted all over the place, dependent on various levels of state and lines of code throughout the program, and otherwise confusing, people will be unable to understand its purpose and impact and they’ll be uncomfortable deleting it. But if it’s immediately clear how it’s used and what other code it interacts with, people will be able to delete it confidently when its usefulness runs out.” (Lyman, p. 50)

**Naming things**
“An important part of this is well-named variables, classes, files, and methods. When naming something, it’s far more important to be descriptive than brief” (Lyman, p. 42)
“It’s useful to be able to know what something is immediately, right when you look at it, even if you haven’t read the rest of the file or project.” (Lyman, p. 42)
“Make sure you know the naming conventions of your team and project—if they use underscores or capital letters to separate words” (Lyman, p. 42)

**Separation of concerns**
“A fair analogy for coding is writing a recipe. In simple recipes, each step depends on the one before it, and once all the steps are complete, the recipe is done.” (Lyman, p. 42)
“The worst form of code is like a simple recipe: a bunch of steps in order, each written out in the same space, and listed from top to bottom. In order to understand it and modify it, you have to read the whole thing a couple of times. A variable on line 2 could affect an operation on line 832, and the only way to find out is to read the entire program.” (Lyman, p. 43)
“The best form of code is like splitting a recipe into sub-recipes, usually called “modules” or “classes” in code. Each module is concerned with a single simple operation or piece of data.” (Lyman, p. 43)
“The benefits to this are significant. Suppose a coder needs to modify the program later” (Lyman, p. 43)
“That coder will only need to read, understand and modify one small part of the program.” (Lyman, p. 43)
“contained in a single small class with a few well-defined inputs and outputs” (Lyman, p. 43)
“The goal here is to make sure that, to make any given change, the coder has to think about as few parts of the program as possible, instead of all the parts at once.” (Lyman, p. 43)

**Global variables (are bad)**
“put username where it belongs: inside of a container (e.g. an object) that gets imported or passed as an argument to the classes and methods that need it. This container can also hold similar pieces of data—anything that’s set at login is a good candidate (but don’t store the password. Don’t ever store a password without encryption).” (Lyman, p. 43)

**DRY**
“There’s a better way: next time you build a website, don’t be so quick to copy and paste. Write the code for the first page, then if you need some of that code in other pages, put it in a class method or a function and let each page refer to it, passing in arguments to handle any little differences between them. DRY stands for “Don’t Repeat Yourself.”” (Lyman, p. 44)
“The goal is this: if an operation needs to change in some way, you should only have to modify a single class or method.” (Lyman, p. 44)
“Don’t take it too far, though—if two operations are really different, let them be different. Trying to force two distinct pieces of code into the same function can result in strange and confusing code.” (Lyman, p. 44)

**Hiding complexity**
“When you build a class or method, the first thing you write should be the interface: the part that a different piece of code (a caller) would need to know about in order to use the class or method.” (Lyman, p. 45)
“what you’re seeing is the interface—only what you need to know to use it, without any of the code it contains.” (Lyman, p. 45)
“all methods and data that are in a class but can be accessed from outside of that class are part of its interface. This means you should make as many methods and fields private as you possibly can.” (Lyman, p. 45)
“Only make data public on a need-to-know basis.” (Lyman, p. 46)

**Proximity**
“Declare things as close as possible to where they’re used.” (Lyman, p. 46)
“In a small method like this, you may be forgiven for thinking the code is well-organized and easy to read. But it’s not. d, for some reason, is declared on line 5 even though it isn’t used until line 10, which means you have to read almost the entire method to make sure it isn’t used anywhere else.” (Lyman, p. 46)
“clear when a variable is going to be used: immediately after it’s declared.” (Lyman, p. 47)

“If you do this consistently, you’ll sometimes find that part of a method is completely independent from the code above and beneath it. This is a good opportunity to extract it into its own method. Even if that method is only used once, it will be valuable as a way to enclose all the parts of an operation in an easily understandable, well-named block.” (Lyman, p. 47)

**Deep nesting (is bad)**
“Count the pairs of { curly braces }. Six, five of which are nested. That’s too many. This block of code is hard to read” (Lyman, p. 48)
“This is a bad idea because if something goes wrong, we have no way of knowing.” (Lyman, p. 48)
“We can clearly see the “normal path” for the code to follow, and only in abnormal situations does the code stray off into an if block. Debugging is much simpler. And if we want to add extra code to handle error conditions, it will be easy to add a couple of lines” (Lyman, p. 49)

**Pure functions**
“A pure function (or functional method) is a function that does not alter or use external data (it’s stateless). In other words, for a given input, it will always provide exactly the same output, no matter what has changed outside of it, and all your other variables will be completely unaffected by what happens inside of it. All pure functions have at least one argument and return at least one value.” (Lyman, p. 49)
“If you want to debug the function, everything you need is right there in three lines of code. You can paste it into a separate environment” (Lyman, p. 49)
“Not all methods can be pure; if your application didn’t have state, its usefulness would be limited. But you should write pure functions often. This will make your program easy to maintain and scale.” (Lyman, p. 49)

**Automated tests**
“An automated test is a piece of code that executes another piece of code and checks the results to make sure it’s working.” (Lyman, p. 50)
“Every major programming language has tools and libraries to help you write these tests. Some are called unit tests, which test a small, self-contained piece of code (like a class or method), and others are integration tests, which test the way different pieces of code interact.” (Lyman, p. 50)
