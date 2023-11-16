Untuk membuat schema baru dalam database PostgreSQL, Anda dapat menggunakan perintah berikut pada CLI psql:

CREATE SCHEMA nama_schema;

Catatan: Anda harus masuk sebagai superuser atau memiliki hak akses CREATE SCHEMA untuk menjalankan perintah ini. Jika Anda mencoba menjalankan perintah sebagai pengguna biasa, Anda mungkin akan melihat pesan kesalahan berikut:

ERROR: permission denied to create schema

Untuk menjalankan perintah ini sebagai superuser, Anda dapat menggunakan perintah berikut:

sudo -u postgres psql -c "CREATE SCHEMA nama_schema;" nama_database

Setelah menjalankan perintah ini, schema baru dengan nama "nama_schema" akan ditambahkan ke database Anda. Anda dapat membuat tabel, view, dan objek database lainnya dalam schema ini.



========================================

CREATE SCHEMA schema_name;  
DROP SCHEMA schema_name;


CREATE SCHEMA gc;
CREATE EXTENSION postgis SCHEMA gc;


UPDATE pg_extension 
  SET extrelocatable = TRUE 
    WHERE extname = 'postgis';

ALTER EXTENSION postgis 
  SET SCHEMA gc;