“Good code doesn’t just work. It’s simple, modular, testable, maintainable, thoughtful.” (Lyman, p. 41)

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
