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