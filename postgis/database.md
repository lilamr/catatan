Untuk membuat database pada PostgreSQL, Anda dapat menggunakan perintah `CREATE DATABASE` di shell PostgreSQL. Berikut adalah langkah-langkah membuat database pada PostgreSQL:

1.  Masuk ke shell PostgreSQL:

sudo -u postgres psql

2. Gunakan perintah `CREATE DATABASE` untuk membuat database:

CREATE DATABASE nama_database;

Ganti `nama_database` dengan nama database yang diinginkan.

3. koneksi ke database:

postgres=# \\c nama_database


Secara umum, lebih aman untuk membuat database dengan menggunakan user `postgres` dibandingkan dengan menggunakan user lain. User `postgres` memiliki hak akses superuser yang memungkinkan mereka melakukan tindakan apa pun yang mereka inginkan di database. Hal ini membuat mereka dapat membuat database dengan mudah dan tanpa kendala.

Namun, meskipun lebih aman, membuat database dengan user `postgres` juga memiliki beberapa risiko. Karena hak akses superuser, user `postgres` dapat membuat perubahan besar dan merugikan pada database, seperti menghapus data atau memodifikasi tabel. Oleh karena itu, sangat penting untuk menjaga keamanan akun user `postgres` dengan menggunakan password yang kuat dan menjaga informasi login aman.

Sebaliknya, membuat database dengan user lain memiliki beberapa keuntungan dalam hal keamanan. Pengguna dapat diberikan hak akses yang lebih terbatas pada database, membatasi potensi kerusakan yang dapat dibuat. Namun, pengguna juga mungkin memiliki kendala dalam membuat database karena hak akses yang terbatas.

Secara keseluruhan, lebih baik untuk membuat database dengan user `postgres` jika Anda memerlukan hak akses superuser, namun pastikan untuk melakukan tindakan keamanan yang diperlukan untuk menjaga akun aman. Jika tidak, lebih baik membuat database dengan user lain dengan hak akses yang terbatas.

Jadi bisa membuat database dengan user postgres, kemudian untuk user lain bisa diberikan akses tertentu dengan perintah GRANT.

=======================================

CREATE DATABASE namadb;  
DROP DATABASE namadb;