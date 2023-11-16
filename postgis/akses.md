Untuk masuk ke shell PostgreSQL sebagai pengguna yang berbeda dari `postgres`, Anda dapat menggunakan perintah `psql` dengan spesifikasi nama pengguna yang diinginkan. Berikut adalah contohnya:

psql -U nama_pengguna nama_database

Ganti `nama_pengguna` dengan nama pengguna yang diinginkan dan `nama_database` dengan nama database yang akan dikoneksikan. Jika Anda belum memiliki password untuk pengguna tersebut, Anda akan diminta untuk memasukkan password.

Selain `nama_pengguna` dan `nama_database`, ada beberapa opsi lain yang dapat digunakan bersama dengan perintah `psql` untuk mengakses shell PostgreSQL:

1.  `-h` atau `--host`: menentukan alamat host PostgreSQL. Misalnya: `psql -h localhost -U nama_pengguna nama_database`.
    
2.  `-p` atau `--port`: menentukan port yang digunakan oleh PostgreSQL. Misalnya: `psql -p 5432 -U nama_pengguna nama_database`.
    
3.  `-W` atau `--password`: meminta password saat memulai koneksi. Misalnya: `psql -W -U nama_pengguna nama_database`.
    
4.  `-d` atau `--dbname`: sama dengan opsi `nama_database` di atas. Misalnya: `psql -d nama_database -U nama_pengguna`.
    
5.  `-f` atau `--file`: menjalankan perintah SQL dari file yang ditentukan. Misalnya: `psql -f nama_file.sql`.

================================

\\dSpsql -U pph -h 127.0.0.1 -d sinkrondb  
  
\\l - list of database  
\\c - Connect to database  
\\c namadblain - connect to another db  
  
\\dn - list of schemas  
SET search_path TO data - pindah schema  

sinkrondb=# SET search_path TO sinkrondb, spasial;

  
\\dt - List tables inside public schemas  
\\dt schema1. - List tables inside particular schemas. For eg: 'schema1'.  
\\d - melihat daftar tabel
\\d nama_table - melihat detail suatu tabel
  
q - keluar dari tampilan list  
\\q - keluar dari psql