buka *code editor* gee (https://code.earthengine.google.com), dan coba masukan perintah:
`print('Hello World');`

pada tab *console* akan menghasilkan keluaran:
`Hello World`

### Variable
Pada contoh di atas kita langsung memasukan nilai `Hello World` kedalam perintah `print`. Pada umumnya nilai disimpan dalam sebuah variabel. sebuah variabel ditandai dengan kata kunci `var` diikuti oleh nama variable yang kita inginkan. Contoh dibawah ini, data berupa teks (string) `San Francisco` disimpan dalam sebuah variabel bernama `city`. Untuk nilai data berupa string harus diletakkan diantara tanda kutip, baik itu ' (*single quotes*) atau " (*double quotes*).
`var city = 'San Francisco';`

Jika kita memasukan variabel `city` kedalam perintah `print`, kita akan mendapatkan nilai/data yang disimpan di dalamnya yaitu kata `San Francisco)` yang akan ditampilkan didalam *Console*.
`print(city);`

Untuk tipe data berupa angka tidak perlu menggunakan tanda kutip.
`var population = 873965;`

### List
It is helpful to be able to store multiple values in a single variable. JavaScript provides a data structure called a list that can hold multiple values. We can create a new list using the square brackets [] and adding multiple values separated by a comma.
`var cities = ['San Francisco', 'Los Angeles', 'New York','Atlanta'];`

Kemudian lanjutkan dengan perintah:
`print(cities);`

akan menghasilkan keluaran:
![[Screenshot from 2023-11-09 09-28-50.png]]

If you look at the output in the Console, you will see “List” with an expander arrow (▷) next to it. Clicking on the arrow will expand the list and show you its content. You will notice that along with the four items in the list, there is a number next to each value. This is the index of each item. It allows you to refer to each item in the list using a numeric value that indicates its position in the list.
`print(cities[0]);`

Keluarannya akan menghasilkan nilai indeks `0` yaitu kata `San Francisco`.

### Object

### Function

### Comment

### Dasar-dasar code GEE

