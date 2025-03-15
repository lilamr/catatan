“Every error message will usually contain: 
1. The error message: what actually went wrong. These can vary from a few cryptic words to a full paragraph containing suggestions on what you might be able to do to fix the bug. 
2. The location where the error occurred: the file, line number, and sometimes the function name where your program was when it crashed.
3. The stack trace: all the lines in your code that the program executed until getting to the function in number 2. This can help trace where your function was called and with which parameters.” (Lyman, p. 66)

“There are two types of errors that typically occur when writing programs. The first, known as a syntax error, simply means that the programmer has made a mistake in the structure of a statement or expression.” (Miller and Ranum, p. 26)

“The other type of error, known as a logic error, denotes a situation where the program executes but gives the wrong result. This can be due to an error in the underlying algorithm or an error in your translation of that algorithm.” (Miller and Ranum, p. 26)
“In this case, the logic error leads to a runtime error that causes the program to terminate. These types of runtime errors are typically called exceptions.” (Miller and Ranum, p. 26)

“When an exception occurs, we say that it has been “raised.” You can “handle” the exception that has been raised by using a try statement.” (Miller and Ranum, p. 27)
“We can handle this exception by calling the print function from within a try block. A corresponding except block “catches” the exception and prints a message back to the user in the event that an exception occurs.” (Miller and Ranum, p. 27)
“It is also possible for a programmer to cause a runtime exception by using the raise statement.” (Miller and Ranum, p. 27)