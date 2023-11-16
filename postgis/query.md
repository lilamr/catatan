/* menampilkan semua isi tabel dari suatu database*/  
SELECT *  
FROM namascheme.namaTabel  
  
/* menampilkan semua kolom dalam suatu tabel data base */  
SELECT *  
FROM namascheme.namaTabel  
WHERE namaKolom  
  
/* menampilkan semua kata tertentu dari suatu kolom dalam suatu tabel data base */  
SELECT *  
FROM namascheme.namaTabel  
WHERE namaKolom = 'kataKunci'  
  
SELECT *  
FROM namascheme.namaTabel  
WHERE namaKolom = 'kataKunci' AND namaKolom2 = 'kataKunci2'  
  
SELECT *  
FROM namascheme.namaTabel  
WHERE namaKolom = 'kataKunci' OR namaKolom = 'kataKunci2'  
  
  
  
  
You have to add the schema first e.g.  
SELECT * FROM place.user_place;  
  
If you don't want to add that in all queries then try this:  
SET search_path TO place;  
  
Now it will works:  
SELECT * FROM user_place;






PEMANGGILAN DATA (select, from, where)  
- SELECT memilih kolom  
- FROM memilih tabel  
- WHERE memilih nilai  
- ORDER BY mengurutkan berdasarkan nilai suatu kolom  
- DISTINCT menampilkan nilai yang sama hanya satu kali  
- LIMIT membatasi jumlah data yang ditampilkan  
- OFFSET menampilkan sisa data  
- BETWEN memilih data diantara rentang waktu tertentu  
- LIKE mencari kata tertentu/ ILIKE untuk tidak case sensitif  
  
//tampilkan kolom dari tabel  
SELECT kolom1, kolom2, kolom3  
FROM tabel1  
LIMIT 10  
  
//tampilkan kolom1 dengan mengganti nama kolom  
SELECT kolom1 as kolom  
FROM tabel1  
  
//tampilkan semua atribut pada tabel1  
SELECT DISTINCT *  
FROM tabel1  
ORDER BY kolom1 DESC  
  
//tampilkan kolom1 tanpa pengulangan pada nilai  
SELECT DISTINCT kolom1  
FROM tabel1  
  
//tampilkan semua atribut untuk nilai tertentu dari kolom1 pada tabel1  
SELECT *  
FROM tabel1  
WHERE kolom1 = 'nilai' AND (kolom2 ='nilai2' OR kolom2 ='nilai3')  
//atau// WHERE kolom2 IN ('nilai2', 'nilai3', 'nilai4')  
BETWEN DATE 'nilai1' AND 'nilai2'  
  
//tampilkan semua atribut untuk kata/karakter tertentu dari kolom1 pada tabel1  
SELECT *  
FROM tabel1  
WHERE kolom1 LIKE '%kata1'



//tampilkan semua nilai dan kolom pada tabel anggota//  
namadb=# SELECT *  
namadb-# FROM anggota;  
  
//tampilkan nilai semua kolom pada tabel anggota untuk data yang bernama depan ulil//  
namadb=# SELECT *  
namadb-# FROM anggota  
namadb-# WHERE nama_depan='ulil';  
  
//tampilkan nilai kolom jenis kelamin untuk data dengan nama dengan sri//  
namadb=# SELECT jenis_kelamin  
namadb-# FROM anggota  
namadb-# WHERE nama_depan = 'sri';  
  
//tampilkan data kolom1 dikelompokkan dan diurutkan berdasarkan nilai dan tambahkan kolom sementara yang menampilkan perhitungan jumlah tiap nilai//  
SELECT kolom1, COUNT(*) FROM tabel1 GROUP BY kolom1 ORDER BY kolom1;  
  
//tampilkan nilai diurutkan z-a berdasarkan nilai pada kolom nama depan//  
namadb=# SELECT * FROM anggota  
namadb-# ORDER BY nama_depan DESC;  
  
//hilangkan kolom kosong  
SELECT COALESCE(email, 'Data kosong') FROM person;