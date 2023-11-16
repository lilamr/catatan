Berikut adalah langkah-langkah untuk menginstal PostgreSQL dan PostGIS pada sistem operasi berbasis Debian/Ubuntu:

1.  Tambahkan repositori PostgreSQL ke sistem:

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

2. Instal PostgreSQL:

sudo apt-get update
sudo apt-get install postgresql-12 postgresql-client-12 postgresql-contrib-12

3. Instal PostGIS:

sudo apt-get install postgis


setelah itu lanjutkan dengan membuat user [[user]]


========================================

INSTALL:  
sudo apt search postgresql  
sudo apt install postgresql postgis  
sudo apt info postgresql  
sudo systemctl status postgresql  
  
sudo apt install net-tools  
netstat -na | grep LISTEN

//di ubuntu defaul user postgresql juga sebagai user di ubuntu yaitu postgres//
sudo su - postgres  

//sebagai user di ubuntu bisa membuat user db dan database tanpa perlu password (postgres@e450:~$). jika menggunakan sudo -u postgres psql akan masuk sebagai user db (postgres=#)//
createuser --help  
createuser -d -S -P pph  
createdb --help  
createdb -E UTF-8 -O pph sinkrondb

3. Install PostGIS  
sudo apt install postgis  
  
3b If missing packages:  
sudo apt install --fix-missing  
  
4. Set the system password for the "postgres" user  
sudo passwd postgres  
(fill in new password and confirm)  
  
5. Create a new database (I'm naming mine geodata)  
sudo -u postgres createdb geodata  
  
6. Connect to the database  
sudo -u postgres psql geodata  
  
7. Set the internal postgres user password  
\password postgres  
(fill in password and confirm)  
  
8. Log out of postgres, and log back in  
\q  
sudo -u postgres psql geodata  
  
9. Create the PostGIS extension  
create extension postgis;  
  
10. Check the PostGIS version  
select PostGIS_version();  
  
11. xit postgresql  
\\q  
  
12. Edit configfiles postgres.conf and pg_hba.conf  
sudo gedit /etc/postgresql/13/main/  
ls  
postgresql.conf => listen_addresses = '*'  
pg_hba.conf add => host all all 192.168.0.1/24 md5  
  
13. Restart postgresql  
sudo service postgresql restart  
  
14. cari ip adresss  
ifconfig




ACCESS CONTROL:  
ip a | grep inet | grep -v inet6  
/* cek ip di windows : ipconfig /all | findstr "IPv4" */  
sudo gedit /etc/postgresql/12/main/postgresql.conf  
/*mengatur ip yang boleh mengakes. hilangkan # pada baris listen_address dan ubah 'localhost' ke ip tertentu atau '*' untuk semua ip */  
sudo gedit /etc/postgresql/12/main/pg_hba.conf  
/* mengatur boleh tidak mengakses database. tambahkan baris pada # IPv4 local connections: host all all 192.168.10.0/24. jika belakangnya /24 maka segmen ip ke 4 bebas (0), jika /32 maka segmen ip ke 4 harus ditentukan (hanya boleh untuk satu ip tersebut) */  
sudo systemctl restart postgresql  
  
TWEAKING:  
[https://pgtune.leopard.in.ua](https://pgtune.leopard.in.ua)
sudo gedit /etc/postgresql/12/main/postgresql.conf  
/* edit sesuai parameter hasil tweaking */  
sudo systemctl restart postgresql