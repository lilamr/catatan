“algorithms require two important control structures: iteration and selection.” (Miller and Ranum, p. 22)

*Logical branches and comparisons*
“Selection statements allow programmers to ask questions and then, based on the result, perform different actions. Most programming languages provide two versions of this useful construct: the ifelse and the if.” (Miller and Ranum, p. 24)

“Selection constructs, as with any control construct, can be nested so that the result of one question helps decide whether to ask the next.” (Miller and Ranum, p. 24)

“Programs have to respond to different situations. They have to make decisions. And that’s where things like if statements come in.” (Lyman, p. 35)
“We do that using an if statement. if is a keyword that looks a little bit like a method. The argument it expects is an expression of some kind, usually a comparison. Comparisons take two values and compare them to each other, resulting in a value of true (if the comparison is true) or false (if it’s not true). These two values are called booleans and they’re the only two booleans in existence. Lucky they’ve got each other.” (Lyman, p. 36)

“if statements evaluate the comparison you give them. If it evaluates to true, they execute the code inside their block (the lines of code inside { curly brackets }). If it evaluates to false, they skip that code.” (Lyman, p. 36)
“if statements can also have an else statement attached to their tail end. The else statement has a block that will be executed if the comparison is false.” (Lyman, p. 36)

*Loops*
“For iteration, Python provides a standard while statement and a very powerful for statement.” (Miller and Ranum, p. 22)

“The while statement repeats a body of code as long as a condition is true.” (Miller and Ranum, p. 22)

“another iterative structure, the for statement, can be used in conjunction with many of the Python collections. The for statement can be used to iterate over the members of a collection, so long as the collection is a sequence (lists, tuples, and strings).” (Miller and Ranum, p. 23)
“A common use of the for statement is to implement definite iteration over a range of values.” (Miller and Ranum, p. 23)
“The range function will return a range object representing the sequence” (Miller and Ranum, p. 24)

“Sometimes, especially when you’re working with an array, you want to execute a block of code several times in a row. This is not the time to use copy and paste. Instead, you should use a loop.” (Lyman, p. 37)

“while loops use the same syntax as if statements. You use parentheses, you pass in a comparison, you follow it up with a block. But an if block only executes the code inside of it once (or zero times, if the comparison evaluates to false). A while block executes the code inside of it over and over again until the condition is false. That is, it evaluates the condition; if it’s true, it executes the block; then it evaluates the condition again; if true, it executes the block again; then it evaluates the condition again; and so on, forever.” (Lyman, p. 37)