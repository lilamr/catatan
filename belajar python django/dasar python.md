“Python supports the object-oriented programming paradigm. This means that Python considers data to be the focal point of the problem-solving process.” (Miller and Ranum, p. 8)
“in any other object-oriented programming language, we define a class to be a description of what the data look like (the state) and what the data can do (the behavior).” (Miller and Ranum, p. 8)
“Data items are called objects in the object-oriented paradigm. An object is an instance of a class.” (Miller and Ranum, p. 8)

**Object**
“An important part of coding is learning how to organize data.” (Lyman, p. 27)
“In code, you would do this with an object. An object is a bunch of pieces of data all organized together. We can also call this an associative array, a dictionary, or a map.” (Lyman, p. 28)
“Really all we’ve done is declare four variables” (Lyman, p. 28)
“And instead of calling them “variables,” we call them “properties” or “fields.” An object can have any properties you want” (Lyman, p. 28)

**Variable**
“Identifiers are used in programming languages as names. In Python, identifiers start with a letter or an underscore `(_)`, are case sensitive, and can be of any length.” (Miller and Ranum, p. 10) 
Identifier adalah nama yang digunakan dalam pemrograman untuk menamai variabel, fungsi, kelas, dan objek lainnya.  
underscore `(_)` di awal nama variabel biasanya digunakan untuk tujuan khusus, seperti:  
`_`var: Konvensi untuk variabel "private" (tidak seharusnya diakses langsung).  
`__`var: Digunakan untuk name mangling dalam kelas.  
`__init__`: Metode khusus dalam class Python.

“A Python variable is created when a name is used for the first time on the left-hand side of an assignment statement. Assignment statements provide a way to associate a name with a value. The variable will hold a reference to a piece of data and not the data itself.” (Miller and Ranum, p. 10) 
variabel dalam Python tidak langsung menyimpan nilai, tetapi menyimpan referensi ke lokasi memori di mana nilai tersebut disimpan.  
a = [1, 2, 3]  
b = a  
Di sini, b tidak menyimpan salinan data [1, 2, 3], tetapi hanya menjadi referensi ke a. Jika kita mengubah a, b juga ikut berubah karena mereka merujuk ke objek yang sama.  
Jadi, dalam Python, variabel hanya menjadi "label" yang menunjuk ke objek di memori, bukan menyimpan data secara langsung seperti di bahasa lain (misalnya C).  
Variabel menyimpan referensi ke lokasi memori, bukan lokasi memori itu sendiri. Ketika nilai variabel berubah, referensi tersebut diubah untuk menunjuk ke lokasi memori yang berbeda.

“This is a dynamic characteristic of Python. The same variable can refer to many different types of data.” (Miller and Ranum, p. 10)

“The most basic building block of a computer program is a variable. A variable is a name for a piece of data” (Lyman, p. 25)
“You have to name your data. There are two reasons you name your data:” (Lyman, p. 25)
“1. You don’t know what it is beforehand.” (Lyman, p. 25)
“2. You don’t want to forget what it means.” (Lyman, p. 25)

**API**
“Nobody starts from scratch. We’re all constantly using code we didn’t write—buckets of it, in fact. Even if you are a prolific coder and write millions of lines of code in your lifetime, you will use far more lines of code that someone else wrote. Most of this code will come from complete strangers.” (Lyman, p. 32)

“How do you use this zombie code? Copy and paste? Occasionally, yes, but not often. Most of the time you’ll access it through an Application Programming Interface or API. An API is a bundled-up set of properties and methods (purpose-built pieces of code) that are named, like variables, so you can refer to them by their name and let them do their thing.” (Lyman, p. 32)

“A method is like a property because you access it with a dot. A method is different from a property because you have to put ( parentheses ) after it. These parentheses are holding the data we want to add” (Lyman, p. 33)

“Building a working vocabulary in this API is an essential part of becoming a web developer.” (Lyman, p. 33)

**Function**
“Function is another word for method. It’s just a piece of code that does something and (usually) has a name.” (Lyman, p. 33)
“giveMeOne() is kind of like dumb_tweets.push(). The main differences are: 1. giveMeOne() is a function we wrote by ourselves. push() is a function that some strangers wrote. It’s okay, they don’t mind if we use it. 2. push() is a method of dumb_tweets (and any other array we’ll ever create). giveMeOne() is global, meaning that we don’t need to refer to a specific object in order to use it.” (Lyman, p. 34)

“You’ll notice one more thing that seems different about them: giveMeOne() uses empty parentheses, but push() expects us to put a piece of data in the parentheses. In fact, push() would be useless if we couldn’t tell it what to add to our array. The piece of data we give it is called an argument. An argument is just a piece of data that we drop into a function.” (Lyman, p. 34)

“This function isn’t too different from giveMeOne(). But instead of empty parentheses, these have variable names in them, separated by a comma. These are our arguments. The return statement does exactly what it looks like it’s doing: it adds number1 and number2 together, then pops out the result.” (Lyman, p. 34)

“This function does exactly the same thing. It just uses a variable named sum as a middleman, where the result is stored so we can return it later.” (Lyman, p. 35)
“There are many ways to write a function. You should choose the way that most clearly expresses what the code is doing. Code that is concise and easy to understand is often called expressive or elegant.” (Lyman, p. 35)

“Functions are very selfish. If you declare a variable inside of a function, the function won’t let any of the code outside of itself use the variable.” (Lyman, p. 38)

**Logical branches and comparisons**
“Programs have to respond to different situations. They have to make decisions. And that’s where things like if statements come in.” (Lyman, p. 35)
“We do that using an if statement. if is a keyword that looks a little bit like a method. The argument it expects is an expression of some kind, usually a comparison. Comparisons take two values and compare them to each other, resulting in a value of true (if the comparison is true) or false (if it’s not true). These two values are called booleans and they’re the only two booleans in existence. Lucky they’ve got each other.” (Lyman, p. 36)

“if statements evaluate the comparison you give them. If it evaluates to true, they execute the code inside their block (the lines of code inside { curly brackets }). If it evaluates to false, they skip that code.” (Lyman, p. 36)
“if statements can also have an else statement attached to their tail end. The else statement has a block that will be executed if the comparison is false.” (Lyman, p. 36)

**Loops**
“Sometimes, especially when you’re working with an array, you want to execute a block of code several times in a row. This is not the time to use copy and paste. Instead, you should use a loop.” (Lyman, p. 37)

“while loops use the same syntax as if statements. You use parentheses, you pass in a comparison, you follow it up with a block. But an if block only executes the code inside of it once (or zero times, if the comparison evaluates to false). A while block executes the code inside of it over and over again until the condition is false. That is, it evaluates the condition; if it’s true, it executes the block; then it evaluates the condition again; if true, it executes the block again; then it evaluates the condition again; and so on, forever.” (Lyman, p. 37)

**Comments**
“It isn’t always obvious what a piece of code is doing, or what still needs to be done with it. If you need to break out of the computer language and have some real talk about what’s going on in the code (or just drop some dope lyrics), you can use a comment, or a line of code that the computer will ignore.” (Lyman, p. 38)

**Built-in Atomic Data Types**
“Python has two main built-in numeric classes that implement the integer and floating point data types. These Python classes are called int and float. The standard arithmetic operations, +, −, `*`, /, and ** (exponentiation), can be used with parentheses forcing the order of operations away from normal operator precedence. Other very useful operations are the remainder (modulo) operator, %, and integer division, //. Note that when two integers are divided, the result is a floating point. The integer division operator returns the integer portion of the quotient by truncating any fractional part.” (Miller and Ranum, p. 8)

“Boolean data objects are also used as results for comparison operators such as equality `(==)` and greater than (>). In addition, relational operators and logical operators can be combined together to form complex logical questions.” (Miller and Ranum, p. 9)

![[Pasted image 20250315072341.png]]

**Built-in Collection Data Types**
“Sometimes you don’t want to think up a unique name for every property in an object, especially if they’re all very similar. Or you don’t know how many there are going to be. That’s when it’s time to use an array, which is a list of similar pieces of data. Arrays can grow or shrink as needed.” (Lyman, p. 28)
“use an array to hold them all” (Lyman, p. 28)
“it’s a variable just like anything else.” (Lyman, p. 29)
“anywhere in your code, and it will refer to the array we defined” (Lyman, p. 29)
“If you want to refer to a specific string in the array” (Lyman, p. 29)
“we use the number (or index) of the thing (or element) we want to refer to.” (Lyman, p. 29)
“Each of the above expressions (an expression is any code that turns into a piece of data when you run it) is a variable. You can assign something new to it, if you want.” (Lyman, p. 29)
“Arrays can hold strings, numbers, dates, objects, and even other arrays. You can put arrays inside of arrays inside of arrays inside of arrays.” (Lyman, p. 29)
“Arrays can also be properties of objects. An object can have a property that is an array of objects, each of which has a property that is an array of objects...and I’ve done it again.” (Lyman, p. 30)

“Lists, strings, and tuples are ordered collections that are very similar in general structure but have specific differences that must be understood for them to be used properly. Sets and dictionaries are unordered collections.” (Miller and Ranum, p. 11)

![[Pasted image 20250315072454.png]]

“A list is an ordered collection of zero or more references to Python data objects.” (Miller and Ranum, p. 11)
“Lists are heterogeneous, meaning that the data objects need not all be from the same class and the collection can be assigned to a variable” (Miller and Ranum, p. 11)
“when Python evaluates a list, the list itself is returned. However, in order to remember the list for later processing, its reference needs to be assigned to a variable.” (Miller and Ranum, p. 11)
“lists are considered to be sequentially ordered” (Miller and Ranum, p. 11)

![[Pasted image 20250315072004.png]]

“You should also notice the familiar “dot” notation for asking an object to invoke a method. my_list.append(False) can be read as “ask the object my_list to perform its append method and send it the value False.”” (Miller and Ranum, p. 13)

“One common Python function that is often discussed in conjunction with lists is the range function. range produces a range object that represents a sequence of values. By using the list function, it is possible to see the value of the range object as a list.” (Miller and Ranum, p. 13)
“The range object represents a sequence of integers. By default, it will start with 0. If you provide more parameters, it will start and end at particular points and can even skip items.” (Miller and Ranum, p. 13)

“Strings are sequential collections of zero or more letters, numbers and other symbols. We call these letters, numbers and other symbols characters.” (Miller and Ranum, p. 13)
“Literal string values are differentiated from identifiers by using quotation marks (either single or double).” (Miller and Ranum, p. 13)
“strings are sequences” (Miller and Ranum, p. 14)

![[Pasted image 20250315072121.png]]

“Tuples are very similar to lists in that they are heterogeneous sequences of data. The difference is that a tuple is immutable, like a string. A tuple cannot be changed.” (Miller and Ranum, p. 15)

“A set is an unordered collection of zero or more immutable Python data objects. Sets do not allow duplicates” (Miller and Ranum, p. 16)

![[Pasted image 20250315072221.png]]

