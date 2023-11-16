FUNGSI AGREGASI (count, sum, avg, max, min)  
- COUNT menghitung banyak row  
- SUM menjumlahkan nilai  
- AVG rata-rata nilai  
- MAX nilai terbesar  
- MIN nilai terkecil  
// akan menambah kolom baru //  
SELECT SUM(price) FROM car; // tampilkan total harga dari tabel car  
SELECT make, SUM(price) FROM car GROUP BY make; // dari tabel car, tampilkan kolom make, tambahkan kolom total price untuk masing-masing nilai pada kolom make.