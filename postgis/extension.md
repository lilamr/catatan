Dalam PostgreSQL, Anda dapat membuat extensi dan schema dalam urutan apa pun. Tergantung pada kebutuhan dan desain database Anda, Anda dapat memutuskan untuk membuat extensi terlebih dahulu atau membuat schema terlebih dahulu.

Jika Anda ingin menambahkan fitur tambahan seperti spasial atau full-text search ke database Anda, Anda dapat membuat extensi terlebih dahulu. Extensi adalah modul tambahan yang dapat memperluas fungsi database Anda. Misalnya, untuk menambahkan dukungan spasial, Anda dapat membuat extensi PostGIS.

Jika Anda ingin membagi database Anda menjadi bagian yang berbeda dengan hak akses yang berbeda, Anda dapat membuat schema terlebih dahulu. Schema adalah struktur logis yang membagi database menjadi bagian yang berbeda. Anda dapat membuat schema baru dan menempatkan tabel, view, dan objek database lainnya dalam schema tersebut.

Pada dasarnya, Anda dapat membuat extensi atau schema sesuai dengan kebutuhan dan desain database Anda. Kedua-duanya dapat dibuat setelah membuat database atau setelah menambahkan tabel, indeks, dan objek database lainnya.

Untuk menginstal extensi PostGIS, Anda harus menjalankan perintah berikut pada CLI psql:

CREATE EXTENSION postgis;

Catatan: Anda harus masuk sebagai superuser atau memiliki hak akses CREATE EXTENSION untuk menjalankan perintah ini. Jika Anda mencoba menjalankan perintah sebagai pengguna biasa, Anda mungkin akan melihat pesan kesalahan berikut:

ERROR: permission denied to create extension "postgis"

Untuk menjalankan perintah ini sebagai superuser, Anda dapat menggunakan perintah berikut:

sudo -u postgres psql -c "CREATE EXTENSION postgis;" nama_database

Setelah menjalankan perintah ini, extensi PostGIS akan ditambahkan ke database Anda dan Anda dapat memulai menggunakan fitur spasial.


======================================

-- Enable PostGIS (as of 3.0 contains just geometry/geography)  
CREATE EXTENSION postgis;  
-- enable raster support (for 3+)  
CREATE EXTENSION postgis_raster;  
-- Enable Topology  
CREATE EXTENSION postgis_topology;  
-- Enable PostGIS Advanced 3D  
-- and other geoprocessing algorithms  
-- sfcgal not available with all distributions  
CREATE EXTENSION postgis_sfcgal;  
-- fuzzy matching needed for Tiger  
CREATE EXTENSION fuzzystrmatch;  
-- rule based standardizer  
CREATE EXTENSION address_standardizer;  
-- example rule data set  
CREATE EXTENSION address_standardizer_data_us;  
-- Enable US Tiger Geocoder  
CREATE EXTENSION postgis_tiger_geocoder;