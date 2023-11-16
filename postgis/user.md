Untuk membuat pengguna baru pada PostgreSQL, Anda dapat menggunakan perintah `CREATE USER` melalui terminal atau melalui aplikasi client PostgreSQL seperti `psql`. Berikut adalah contoh membuat pengguna baru melalui terminal:

1.  Masuk ke shell PostgreSQL:

sudo -u postgres psql

2. Buat pengguna baru dengan perintah `CREATE USER`:

CREATE USER nama_pengguna WITH PASSWORD 'kata_sandi';

Ganti `nama_pengguna` dengan nama pengguna yang diinginkan, dan `kata_sandi` dengan kata sandi yang diinginkan.

Itu saja langkah-langkah untuk membuat pengguna baru pada PostgreSQL. Jika Anda memerlukan hak istimewa seperti mengakses database atau membuat database baru, Anda harus memberikan hak istimewa yang sesuai melalui perintah `GRANT`.

3. Berikan hak akses pengguna dengan perintah `GRANT`:

GRANT ALL PRIVILEGES ON DATABASE nama_database TO nama_pengguna;

Ganti `nama_database` dengan nama database yang diinginkan, dan `nama_pengguna` dengan nama pengguna yang akan diberikan hak akses.

4. Mengatur hak akses pada tabel tertentu:

GRANT ALL PRIVILEGES ON TABLE nama_database.nama_tabel TO nama_pengguna;

Ganti `nama_database` dengan nama database yang diinginkan, `nama_tabel` dengan nama tabel yang diinginkan, dan `nama_pengguna` dengan nama pengguna yang akan diberikan hak akses.

5. mengatur privilage

Untuk memberikan privileges tertentu pada tabel atau database pada PostgreSQL, Anda dapat menggunakan perintah `GRANT` dengan spesifikasi privileges yang diinginkan. Berikut adalah beberapa contoh memberikan privileges tertentu:

a. Memberikan privileges SELECT, INSERT, UPDATE, dan DELETE pada tabel:

GRANT SELECT, INSERT, UPDATE, DELETE ON TABLE nama_tabel TO nama_pengguna;

b. Memberikan privileges SELECT pada database:

GRANT SELECT ON DATABASE nama_database TO nama_pengguna;

Ganti `nama_tabel` dengan nama tabel yang diinginkan, `nama_database` dengan nama database yang diinginkan, dan `nama_pengguna` dengan nama pengguna yang akan diberikan hak akses.



=======================================

CREATE USER nama_user;  
DROP USER nama_user;