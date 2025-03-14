“Python supports the object-oriented programming paradigm. This means that Python considers data to be the focal point of the problem-solving process.” (Miller and Ranum, p. 8)
“in any other object-oriented programming language, we define a class to be a description of what the data look like (the state) and what the data can do (the behavior).” (Miller and Ranum, p. 8)
“Data items are called objects in the object-oriented paradigm. An object is an instance of a class.” (Miller and Ranum, p. 8)

**Built-in Atomic Data Types**
“Python has two main built-in numeric classes that implement the integer and floating point data types. These Python classes are called int and float. The standard arithmetic operations, +, −, `*`, /, and ** (exponentiation), can be used with parentheses forcing the order of operations away from normal operator precedence. Other very useful operations are the remainder (modulo) operator, %, and integer division, //. Note that when two integers are divided, the result is a floating point. The integer division operator returns the integer portion of the quotient by truncating any fractional part.” (Miller and Ranum, p. 8)

“Boolean data objects are also used as results for comparison operators such as equality `(==)` and greater than (>). In addition, relational operators and logical operators can be combined together to form complex logical questions.” (Miller and Ranum, p. 9)

![[Pasted image 20250315072341.png]]

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

**Built-in Collection Data Types**
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

