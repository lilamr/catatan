Setelah membuat database, langkah selanjutnya adalah mengatur tabel dan data yang akan disimpan dalam database. Berikut adalah beberapa langkah yang dapat dilakukan:
1.  Membuat tabel: Anda dapat membuat tabel baru dengan menjalankan perintah SQL CREATE TABLE. Setiap tabel memiliki kolom yang menentukan jenis data yang akan disimpan dan baris yang menentukan entri data individu.
2.  Mengisi tabel: Setelah membuat tabel, Anda dapat mengisi tabel dengan data baru dengan menjalankan perintah SQL INSERT INTO.
3.  Memodifikasi tabel: Jika diperlukan, Anda dapat memodifikasi tabel yang ada dengan menjalankan perintah SQL ALTER TABLE atau menambah kolom baru, menghapus kolom, atau memodifikasi tipe data kolom.
4.  Membuat vies: Views adalah tampilan virtual dari data dalam tabel. Anda dapat membuat view dengan menjalankan perintah SQL CREATE VIEW.
5.  Membuat indeks: Indeks adalah cara untuk mempercepat pencarian data dalam database. Anda dapat membuat indeks dengan menjalankan perintah SQL CREATE INDEX.
6.  Menjalankan query: Setelah membuat tabel dan mengisi mereka dengan data, Anda dapat menjalankan query untuk mengambil data spesifik dari database dengan menjalankan perintah SQL SELECT.

Itulah beberapa langkah yang dapat dilakukan setelah membuat database. Pastikan untuk melakukan backup secara berkala untuk menjaga integritas data dan memastikan bahwa data Anda tetap aman.

Untuk membuat tabel baru dalam database PostgreSQL, Anda dapat menggunakan perintah berikut pada CLI psql:

CREATE TABLE nama_schema.nama_tabel (
    kolom1 nama_tipe_data1,
    kolom2 nama_tipe_data2,
    ...
);

Catatan: Anda harus masuk sebagai superuser atau memiliki hak akses CREATE TABLE untuk menjalankan perintah ini. Jika Anda mencoba menjalankan perintah sebagai pengguna biasa, Anda mungkin akan melihat pesan kesalahan berikut:

ERROR: permission denied to create table

Untuk menjalankan perintah ini sebagai superuser, Anda dapat menggunakan perintah berikut:

sudo -u postgres psql -c "CREATE TABLE nama_schema.nama_tabel (kolom1 nama_tipe_data1, kolom2 nama_tipe_data2, ...);" nama_database

Contoh membuat tabel baru dengan 2 kolom, yaitu "id" dengan tipe data integer dan "nama" dengan tipe data character varying:

CREATE TABLE nama_schema.tabel_baru (
    id integer,
    nama character varying
);

Setelah menjalankan perintah ini, tabel baru dengan nama "nama_tabel" akan ditambahkan ke schema "nama_schema". Anda dapat mulai memasukkan data ke tabel ini.



=======================================

CREATE TABLE anggota (  
id BIGSERIAL NOT NULL PRIMARY KEY,  
nama_depan VARCHAR(50) NOT NULL,  
nama_belakang VARCHAR(50) NOT NULL,  
jenis_kelamin VARCHAR(10) NOT NULL,  
tanggal_lahir DATE NOT NULL,  
email VARCHAR(150)  
);  
DROP TABLE anggota;