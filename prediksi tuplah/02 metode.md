## MOLUSCE 4.0

MOLUSCE (Modules for Land Use Change Evaluation) adalah plugin untuk QGIS yang dirancang untuk menganalisis perubahan penggunaan lahan dan tutupan hutan antara periode waktu yang berbeda, memodelkan potensi transisi penggunaan/tutupan lahan, dan mensimulasikan perubahan penggunaan dan tutupan lahan di masa mendatang. Plugin ini menggabungkan beberapa algoritma yang terkenal, termasuk Jaringan Syaraf Tiruan.

### 1. Cara menyiapkan data input

Data masukan yang digunakan oleh plugin:
Peta penggunaan/penutup lahan awal dan akhir. Ini adalah gambar raster yang nilai pikselnya sesuai dengan kode penggunaan/penutup lahan (misalnya 1=hutan, 2=lahan pertanian, 3=perkotaan, dst.).

Minimum:
1. Peta keadaan awal (tanggal_initial)
2. peta langkah akhir (tanggal_awal+N)
3. peta validasi (initial_date+2N). Sebaiknya gunakan peta ketiga untuk memvalidasi prakiraan simulasi.

N singkatan dari Kedalaman Prakiraan, yaitu waktu antara keadaan daratan, diukur dalam satuan hari, minggu, tahun dan seterusnya, tergantung pada tugas yang dikerjakan.

Peta variabel spasial yang memengaruhi penggunaan lahan. Peneliti berhipotesis tentang faktor-faktor apa yang mungkin memengaruhi perubahan yang diamati dan memasukkan peta intensitas faktor-faktor ini. Misalnya, jika seorang peneliti sedang meneliti masalah kepunahan hutan, faktor-faktor tersebut mungkin adalah: jenis tanah (setiap jenis tanah diberi kode dengan angka), jarak dari jalan (piksel peta berisi angka - jarak terpendek dari titik yang terkait dengan piksel tersebut ke jalan), kepadatan penduduk, dll.

Semua raster input harus memiliki yang sama:
- resolusi
- cakupan
- ukuran dalam piksel

Kami sarankan untuk membuat tabel atribut raster dari simbologi terkini untuk setiap lapisan. Dengan cara ini Anda dapat melihat nama kelas menggunakan alat Identifikasi. Kami juga sarankan untuk menyetel gaya ke nilai Palet/Unik. Setiap kelas akan ditandai pada peta dengan warna tersendiri.

### 2. Memuat data dan pelatihan model

Plugin memiliki beberapa tab yang digunakan satu demi satu.

#### 2.1. Masukan

Di sebelah kiri terdapat daftar semua lapisan raster dalam proyek. Dari daftar tersebut, pilih peta status awal dan peta status akhir. Kemudian, tambahkan variabel spasial di bagian kanan bawah tab. Tekan **Periksa geometri** . Setelah pemeriksaan geometri berhasil, tab lain akan tersedia.

[![../../_images/molusce_inputs_en.png](https://docs.nextgis.com/_images/molusce_inputs_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_inputs_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)
Gambar 8.20. Mengunggah data masukan

#### 2.2. Mengevaluasi korelasi

Di tab ini, jika perlu, Anda dapat menghitung sejauh mana faktor-faktor pengaruh saling terkait. Jika korelasi antara dua faktor kuat, mungkin cukup untuk menggunakan salah satunya saja. Untuk variabel kontinu, Anda dapat menghitung korelasi Pearson, dan untuk variabel nominal, koefisien Cramer atau JIU (ketidakpastian informasi bersama). Pilih dua faktor dari menu tarik-turun atau centang opsi “Periksa semua raster”.

[![../../_images/molusce_correlation_en.png](https://docs.nextgis.com/_images/molusce_correlation_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_correlation_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)
Gambar 8.21. Menghitung korelasi

#### 2.3. Perubahan wilayah

Pada tab “Perubahan area” tekan **Perbarui tabel** .

Dua tabel akan dibuat: “Statistik kelas” dan “Matriks transisi” (menunjukkan proporsi piksel yang berubah dari satu penggunaan/penutup lahan ke yang lain). Informasi ini dapat digunakan sendiri untuk tugas-tugas tertentu.

Selanjutnya tekan tombol **Buat peta perubahan** dan pilih jalur dan nama untuk raster baru. Setiap kelas transisi akan ditandai pada peta dengan warna tertentu. Kami sarankan untuk membuat tabel atribut raster untuk lapisan tersebut juga.

[![../../_images/molusce_area_change_en.png](https://docs.nextgis.com/_images/molusce_area_change_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_area_change_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)
Gambar 8.22. Tabel perubahan luas

#### 2.4. Pemodelan potensi transisi

Tersedia empat metode:
- Jaringan Syaraf Tiruan (JST),
- Bobot Bukti (WoE)
- Evaluasi Multi Kriteria (MCE),
- Regresi Logistik (LR)

[![../../_images/molusce_modeling_en.png](https://docs.nextgis.com/_images/molusce_modeling_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_modeling_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)
Gambar 8.23. Pelatihan jaringan saraf

Pertama, konfigurasikan parameter pengambilan sampel berikut:

**Mode pengambilan sampel:**
- semua - menggunakan semua piksel dan membutuhkan banyak waktu;
- acak - metode paling umum dan cepat, tetapi mungkin mengabaikan beberapa jenis transisi;
- berstrata - berguna untuk memastikan bahwa setiap subkelompok terwakili secara memadai dalam sampel.

Anda juga dapat mengonfigurasi **jumlah sampel** . Hal ini memengaruhi akurasi model dan kecepatan pembelajaran.

Berikutnya, sesuaikan pemodelan ANN:
- Lingkungan menentukan jumlah piksel tetangga di sekitar piksel saat ini (biasanya nilai 1 atau 0 digunakan);
- Tingkat pembelajaran (nilai yang lebih rendah membuat model lebih hati-hati);
- Jumlah iterasi maksimum - jumlah siklus pembelajaran. Jika nilainya terlalu tinggi, dapat mengakibatkan overfitting;
- Lapisan tersembunyi - mendefinisikan kompleksitas model.

Tekan **Train neural network** . Pada grafik, Anda akan melihat kurva pembelajaran dan kurva kesalahan. Jika Anda melihat bahwa pelatihan tidak berjalan dengan baik, Anda dapat menekan **Stop** dan mengubah parameter.

Jika pelatihan berhasil, kedua kurva turun dengan lancar dan Kappa Validasi Saat Ini sekitar 0,8 atau lebih tinggi.

[![../../_images/molusce_curves_en.png](https://docs.nextgis.com/_images/molusce_curves_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_curves_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)
Gambar 8.24. Kurva pembelajaran yang umum

Setelah melatih model, Anda dapat menyimpan sampel sebagai lapisan terpisah. Ini memungkinkan untuk memeriksa apakah semua jenis transisi telah diambil sampelnya untuk pelatihan.

### 3. Simulasi Automata Seluler

Setelah model dilatih, model tersebut dapat digunakan untuk membuat prakiraan.

Pada tab “Cellular Automata Simulation”, atur jumlah iterasi simulasi, yaitu jumlah periode waktu untuk membuat prakiraan (1 secara default), dan jalur untuk file yang dibuat. Untuk memulai simulasi, tekan **Start** .

Selain peta simulasi penggunaan/penutup lahan, Anda juga dapat membuat:
- Peta potensi transisi menunjukkan probabilitas atau potensi perubahan dari satu kelas penggunaan/penutup lahan ke kelas lain. Nilai berkisar dari 0 (potensi rendah) hingga 100 (potensi transisi tinggi).
- Fungsi kepastian menunjukkan tingkat kepastian prakiraan. Nilai berkisar dari 0 (kepastian rendah) hingga 100 (kepastian tinggi). Kepastian rendah kemungkinan berarti bahwa jenis transisi tertentu tidak diambil sampelnya.

[![../../_images/molusce_simulation_en.png](https://docs.nextgis.com/_images/molusce_simulation_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_simulation_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)
Gambar 8.25. Pengaturan simulasi

### 4. Validasi

Validasi dapat dilakukan jika Anda memiliki peta referensi dengan data aktual untuk periode tersebut. Pada tab ini Anda juga dapat menghitung kappa.

Peta kesalahan dapat dibuat. Peta ini berisi tiga jenis piksel:
- Tetap (kelas piksel tidak berubah sejak tanggal awal dan perkiraannya akurat)
- Kosong (prediksi benar)
- Kesalahan (prediksi tidak sesuai dengan data sebenarnya)

[![../../_images/molusce_validation_en.png](https://docs.nextgis.com/_images/molusce_validation_en.png)](https://docs-nextgis-com.translate.goog/_images/molusce_validation_en.png?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=en&_x_tr_pto=wapp)


## Bahan

Analisa ini menggunakan citra tutupan lahan dan juga data spasial lain sebagai driving factor yang dianggap mempengaruhi perubahan tutupan lahan.

### 1. Citra Tuplah
GLC_FCS30D adalah produk dinamis penutup lahan global pertama dengan resolusi 30 meter yang mengadopsi deteksi perubahan berkelanjutan. Produk ini menggunakan sistem klasifikasi yang disempurnakan yang berisi 35 kategori penutup lahan dan mencakup rentang waktu dari tahun 1985 hingga 2022. Sebelum tahun 2000, siklus pembaruan dilakukan setiap 5 tahun, sedangkan setelah tahun 2000, produk ini diperbarui setiap tahun. Secara khusus, produk ini dikembangkan dengan menggabungkan metode deteksi perubahan berkelanjutan, model pembaruan adaptif lokal, dan algoritma pengoptimalan spasiotemporal dari citra Landsat deret waktu padat, dan divalidasi untuk mencapai akurasi keseluruhan sebesar 80,88% (±0,27%) untuk sistem klasifikasi dasar (10 jenis penutup lahan utama) dan 73,24% (±0,30%) untuk sistem validasi LCCS level-1 (17 jenis penutup lahan LCCS).

https://zenodo.org/records/8239305

https://essd.copernicus.org/articles/13/2753/2021/

### 2. Drive factor
- DEM Jalan
- pemukiman
- lahan budidaya

Peta Rupabumi Skala 1:50.000 ini merupakan peta digital rupabumi hasil pekerjaan oleh Pusat Pemetaan Rupabumi dan Toponim (PPRT)-Badan Informasi Geospasial. Volume pekerjaan ini meliputi seluruh wilayah Indonesia dan telah di dipublikasikan pada tanggal 27-Nop 2019.  
  
[https://tanahair.indonesia.go.id/sdi/dataset/indeks_rbi_50k](https://tanahair.indonesia.go.id/sdi/dataset/indeks_rbi_50k)

### 3. Areal 
- Provinsi NTB
