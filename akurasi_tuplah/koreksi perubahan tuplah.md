KOREKSI AKURASI PERUBAHAN PENUTUPAN LAHAN

Perubahan penutupan lahan dibagi menjadi 5 kelas yaitu, yaitu deforestation (deforestasi), forest degradation (degradasi hutan), forest gain (pertumbuhan hutan), stable forest (tutupan hutan yang tetap/tidak berubah), dan stable non-forest (tutupan non-hutan yang tetap/tidak berubah). Dalam proses penghitungan akurasi dan uncertainty data perubahan penutupan lahan, klasifikasi perubahan penutupan lahan diperoleh dari hasil overlay data penutupan lahan dua periode tahun yang berbeda (misal: tahun T-1 dan tahun T-2). Untuk contoh perhitungan dalam buku ini akan menggunakan 4 (empat) kelas perubahan penutupan lahan, yaitu deforestation, forest degradation, stable forest, dan stable non-forest.

![[Pasted image 20240517110630.png]]
Skema dinamika perubahan penutupan lahan

Titik sampel dibuat berdasarkan luas masing-masing kelas perubahan penutupan lahan dengan metode stratified random sampling, dimana jumlah sampel setiap kelas ditentukan oleh estimasi user’s accuracy-nya. Setiap titik sampel diinterpretasi secara visual menggunakan data referensi. Interpretasi dilakukan pada sampel poligon yang berbentuk lingkaran dengan luas 6,25 ha yang dibangun berdasarkan titik sampel (point) hasil stratified random sampling. Interpretasi ini menggunakan ketentuan “benar” atau “salah” pada setiap sampel, sesuai dengan klasifikasi kelas perubahan penutupan lahan yaitu deforestation, forest degradation, forest gain, stable forest, dan stable non-forest. Hasil interpretasi sampel kemudian dihitung akurasi (user’s accuracy, producer’s accuracy, dan overall accuracy) dan uncertainty-nya dengan confusion matrix/error matrix. Angka uncertainty setiap strata ini dapat digunakan untuk adjustment (penyesuaian) luas masing-masing kelas perubahan penutupan lahan.

![[Pasted image 20240517110659.png]]
Alur perhitungan akurasi dan uncertainty perubahan penutupan lahan

Penentuan jumlah sampel dan sebarannya dilakukan dengan menggunakan metode equal allocation, dimana setiap kelas mempunyai jumlah sampel yang sama dan tersebar secara acak di semua poligon dalam kelas tersebut. Metode ini dipilih dengan pertimbangan, kelas stable forest dan stable non-forest secara umum mempunyai ukuran kelas yang besar, sedangkan pada kelas perubahan lahan berupa deforestation, forest degradation, dan forest gain mempunyai luasan yang kecil.

Interpretasi (pengamatan) perubahan penutupan lahan dilakukan pada unit sampling berupa titik/point pada poligon (lingkaran) dengan luas 6,25 ha. Penentuan kelas perubahan penutupan lahan menggunakan skema luas mayoritas (majority), yaitu dengan luas ≥50% dari MMU seperti disajikan pada gambar 5. Sebagai contoh, apabila hasil interpretasi pada sampel menunjukkan ada perubahan dari kelas hutan alam primer pada T1 menjadi kelas non hutan pada T2 dengan luas ≥50% dari luas sampel poligon lingkaran, maka perubahan penutupan lahan pada sampel tersebut adalah deforestation.

Apabila luas perubahan penutupan lahan ˂50%, namun piksel di pusat lingkaran (titik sampel) mengalami perubahan, maka sampel tersebut dikelaskan berdasarkan perubahan yang terjadi pada piksel tersebut. Sebagai contoh, luas perubahan dari kelas hutan alam primer pada T1 menjadi kelas non-hutan kurang dari 50%, namun pada piksel pusat lingkaran mengalami deforestasi, maka sampel tersebut dikelaskan sebagai kelas deforestasi. Jika piksel pada titik sampel tidak berubah selama 2 (dua) periode waktu pengamatan, maka sampel dikelaskan sesuai kelas perubahan penutupan lahan yang dominan pada sampel tersebut (≥50% luas poligon lingkaran 6,25 ha).

![[Pasted image 20240517110735.png]]
Interpretasi sampel perubahan penutupan lahan

Penyebaran sampel secara acak menyebabkan posisi sampel tidak selalu berada di pusat poligon, sehingga dapat menyebabkan bias pada saat interpretasi sampel, contohnya sampel yang berada di batas poligon atau tertutup awan. Pada kelas perubahan penutupan lahan yang mempunyai luasan kecil, sampel dapat saling menumpuk karena jumlah sampel yang disebar sama untuk semua kelas perubahan penutupan lahan. Untuk mengurangi bias pada saat interpretasi sampel, penentuan kelas perubahan penutupan lahan untuk setiap sampel dilakukan dengan metode decision tree.

![[Pasted image 20240517110807.png]]
Interpretasi sampel dengan metode decision tree

Sampel yang diinterpretasi harus clear, dalam arti tidak boleh tertutup awan, di batas poligon dan saling menumpuk (overlap). Apabila sampel tertutup awan, maka dapat diamati dengan citra lain yang dapat menerangkan kondisi pada periode pengamatan sampel tersebut. Apabila tidak ditemukan citra lain yang bebas awan pada lokasi sampel, maka sampel dapat digeser sesuai dengan ketentuan pada metode inventarisasi hutan. Pergeseran sampel ini juga berlaku untuk sampel di batas poligon dan sampel bertumpuk.

Analisa sampel dilakukan berdasarkan urutan No_ID sampel, dari nomor kecil hingga ke nomor besar. Hal ini akan mempermudah saat menentukan parameter sampel yang bertumpuk/overlap dengan sampel yang sudah dianalisa. Sebagai contoh, sampel No_ID 8 overlap dengan sampel No_ID 20, maka sampel yang akan dianalisa pertama adalah sampel dengan No_ID 8, sehingga sampel No_ID 20 disebut sebagai sampel yang bertumpuk/overlap dengan sampel yang sudah dianalisa, yaitu sampel No_ID 8.

Sampel digeser ke Utara (0⁰) dengan jarak 1 km, apabila tidak memungkinkan digeser ke arah timur (90⁰) dengan jarak 1 km hingga arah 270⁰. Apabila masih belum dapat menempatkan sampel pada area yang bebas awan, batas poligon dan bertumpuk dengan sampel lain, maka sampel dapat digeser ke arah 45⁰ dengan jarak 1 km, hingga ke arah 315⁰. Pergeseran masih bisa dilakukan apabila sampel masih bermasalah dengan arah sama, namun dengan jarak 500 m dan dilanjutkan dengan jarak 2 km. Pergeseran tersebut hanya dapat dilakukan pada poligon kelas perubahan penutupan lahan untuk sampel yang sama dengan sampel yang digeser. Apabila sampel tersebut tidak dapat digeser karena poligon yang diwakilinya mempunyai luasan kecil/terbatas dan sampelnya hanya 1 (satu), maka sampel tersebut tetap digunakan sebagai sampel dari poligon kelas perubahan lahan tersebut. Apabila sampel tidak dapat digeser sesuai ketentuan tersebut dan dalam poligon tersebut sudah ada sampel yang lain, maka sampel tersebut tidak akan digunakan dan dapat diganti dengan sampel lain. Penggantian sampel dilakukan dengan metode yang sama dengan metode pergeseran sampel, namun dapat berpindah poligon dengan kelas perubahan penutupan lahan yang sama dengan poligon sebelumnya.

![[Pasted image 20240517110831.png]]
Metode pergeseran sampel

Ukuran atau jumlah sampel minimum adalah 20 hingga 100 sampel di setiap strata (Congalton & Green, 2008). Penentuan ukuran sampel dihitung berdasarkan persamaan Cochran (1977) sebagaimana persamaan 1. Target Standard Error untuk overall accuracy (𝑆(𝑂)) adalah 0,01. Sementara itu, 𝑊i dan 𝑆i dihitung dengan menggunakan persamaan 2 dan persamaan 3.

![[Pasted image 20240517110920.png]]
![[Pasted image 20240517110933.png]]
![[Pasted image 20240517111010.png]]

Target user’s accuracy (𝑈i) untuk deforestation adalah 0,70, forest gain 0,60, stable forest 0,90, dan stable non-forest 0,95 (Olofsson et al., 2014; Olofsson et al., 2013). Untuk nilai user’s accuracy forest degradation adalah 0,70, dimana nilai ini sama dengan nilai untuk deforestation. Kedua kelas perubahan penutupan lahan ini dikategorikan sebagai disturbance, yaitu kerusakan bentang alam hutan akibat intervensi manusia. Di samping itu, banyak sistem pemantauan hutan yang tidak melakukan penghitungan forest degradation, karena uncertainty yang dihasilkan masih sangat tinggi (Hosonuma et al., 2012; Pan et al., 2011). Nilai user’s accuracy yang digunakan untuk semua kelas perubahan penutupan lahan ini ditetapkan berdasarkan banyak penelitian yang sudah dilakukan sebelumnya dengan sampel dari berbagai negara.

Semua penghitungan dalam buku ini menggunakan contoh 4 (empat) kelas perubahan penutupan lahan Provinsi Nusa Tenggara Barat periode tahun 2000-2022, yaitu deforestation, forest degradation, stable forest dan stable non-forest. Sebelum menghitung jumlah sampel pada masing-masing kelas, luas dari setiap kelas dihitung berdasarkan data spasial perubahan penutupan lahannya.

![[Pasted image 20240517111048.png]]
Contoh penghitungan sebaran jumlah sampel dengan metode Equal Allocation

![[Pasted image 20240517111103.png]]
Contoh hasil penghitungan sebaran jumlah sampel dengan berbagai metode Equal Allocation

Langkah-langkah pembuatan peta perubahan penutupan lahan dan penghitungan luas masing-masing strata adalah sebagai berikut:
    1. Membuat file “geodatabase” yang merupakan tempat penyimpanan informasi geografis yang komprehensif dengan menggunakan DBMS. Seluruh data spasial yang digunakan dalam proses penghitungan akurasi dan uncertainty perubahan penutupan lahan dibuat dalam format geodatabase.
    2. Melakukan overlay (tumpang susun) 2 (dua) periode peta penutupan lahan (misalnya: peta penutupan lahan Provinsi NTB tahun 2000 dan 2022)
    3. Menambah “field” untuk kelas perubahan penutupan lahan pada tabel peta hasil overlay, misalnya dengan nama “LCC” (Land Cover Change) dalam type “text” dan length “5”.
    4. Menentukan kelas perubahan penutupan lahan menggunakan skema perubahan penutupan lahan yang sudah disusun, misalnya untuk kelas “deforestation”.
    5. Klik “select by attributes” pada tabel hasil overlay. Pilih setiap area kelas perubahan penutupan lahan berdasarkan perubahan ID kelas penutupan lahan pada 2 periode waktu pengamatan. Rumus yang digunakan untuk menentukan kelas perubahan penutupan lahan menggunakan ID dari setiap kelas penutupan lahannya yang mengacu pada tabel klasifikasi penutupan lahan dan dikelompokkan sebagai berikut:
        a) Kelas Deforestation: perubahan dari kelas penutupan lahan hutan alam (primer dan sekunder) menjadi kelas penutupan lahan non hutan.
           `( "PL06_ID" = 2001 OR "PL06_ID" = 2002 OR "PL06_ID" = 2004 OR "PL06_ID" = 2005 OR "PL06_ID" = 20041 OR "PL06_ID" = 20051 ) AND ( "PL16_ID" = 2006 OR "PL16_ID" = 2007 OR "PL16_ID" = 2010 OR "PL16_ID" = 2012 OR "PL16_ID" = 2014 OR "PL16_ID" = 3000 OR "PL16_ID" = 5001 OR "PL16_ID" = 20071 OR "PL16_ID" = 20091 OR "PL16_ID" = 20092 OR "PL16_ID" = 20093 OR "PL16_ID" = 20094 OR "PL16_ID" = 20121 OR "PL16_ID" = 20122 OR "PL16_ID" = 20141 OR "PL16_ID" = 50011 )`
        b) Kelas Forest degradation: perubahan dari kelas penutupan lahan hutan alam primer (hutan lahan kering, hutan rawa dan hutan mangrove) menjadi kelas penutupan lahan hutan alam sekunder.
          `( "PL06_ID" = 2001 OR "PL06_ID" = 2004 OR "PL06_ID" = 2005 ) AND ( "PL16_ID" = 2002 OR "PL16_ID" = 20041 OR "PL16_ID" = 20051 )`
        c) Kelas Forest Gain: perubahan penutupan lahan dari kelas hutan alam sekunder menjadi kelas hutan alam primer dan perubahan dari kelas penutupan lahan non hutan menjadi kelas penutupan lahan hutan alam (primer dan sekunder). Sebagai catatan, perubahan dari kelas penutupan lahan non hutan menjadi kelas penutupan lahan hutan alam primer dimungkinkan, namun memerlukan waktu yang cukup lama (minimal 45 tahun), tergantung dengan kondisi biofisik lingkungannya.
            ▪ Forest to Forest:
              `( "PL06_ID" = 2002 OR "PL06_ID" = 20041 OR "PL06_ID" = 20051 ) AND ( "PL16_ID" = 2001 OR "PL16_ID" = 2004 OR "PL16_ID" = 2005 )`
            ▪ Non Forest to Forest:
              `( "PL06_ID" = 2006 OR "PL06_ID" = 2007 OR "PL06_ID" = 2010 OR "PL06_ID" = 2012 OR "PL06_ID" = 2014 OR "PL06_ID" = 3000 OR "PL06_ID" = 5001 OR "PL06_ID" = 20071 OR "PL06_ID" = 20091 OR "PL06_ID" = 20092 OR "PL06_ID" = 20093 OR "PL06_ID" = 20094 OR "PL06_ID" = 20121 OR "PL06_ID" = 20122 OR "PL06_ID" = 20141 OR "PL06_ID" = 50011 ) AND ( "PL16_ID" = 2001 OR "PL16_ID" = 2002 OR "PL16_ID" = 2004 OR "PL16_ID" = 2005 OR "PL16_ID" = 20041 OR "PL16_ID" = 20051 )`
        d) Kelas Stable Forest: kelas penutupan lahan hutan alam (primer dan sekunder) yang tetap/tidak berubah. Untuk perubahan pada kelas stable forest, perubahan pada kelas hutan alam primer dan kelas hutan alam sekunder perlu dipisahkan, sehingga tidak bercampur dengan kelas forest degradation.
            ▪ Stable Primary Forest
              `( "PL06_ID" = 2001 OR "PL06_ID" = 2004 OR "PL06_ID" = 2005 ) AND ( "PL16_ID" = 2001 OR "PL16_ID" = 2004 OR "PL16_ID" = 2005 )`
            ▪ Stable Secondary Forest
              `( "PL06_ID" = 2002 OR "PL06_ID" = 20041 OR "PL06_ID" = 20051 ) AND ( "PL16_ID" = 2002 OR "PL16_ID" = 20041 OR "PL16_ID" = 20051 )`
        e) Kelas Stable Non-forest : kelas penutupan lahan non hutan yang tetap/tidak berubah
          `( "PL17_ID" = 2006 OR "PL17_ID" = 2007 OR "PL17_ID" = 2010 OR "PL17_ID" = 2012 OR "PL17_ID" = 2014 OR "PL06_ID" = 3000 OR "PL17_ID" = 5001 OR "PL17_ID" = 20071 OR "PL17_ID" = 20091 OR "PL17_ID" = 20092 OR "PL17_ID" = 20093 OR "PL17_ID" = 20094 OR "PL17_ID" = 20121 OR "PL17_ID" = 20122 OR "PL17_ID" = 20141 OR "PL17_ID" = 50011 ) AND ( "PL18_ID" = 2006 OR "PL18_ID" = 2007 OR "PL18_ID" = 2010 OR "PL18_ID" = 2012 OR "PL18_ID" = 2014 OR "PL16_ID" = 3000 OR "PL18_ID" = 5001 OR "PL18_ID" = 20071 OR "PL18_ID" = 20091 OR "PL18_ID" = 20092 OR "PL18_ID" = 20093 OR "PL18_ID" = 20094 OR "PL18_ID" = 20121 OR "PL18_ID" = 20122 OR "PL18_ID" = 20141 OR "PL18_ID" = 50011 )`
    6. Klik kanan pada kolom “LCC” > field calculator kemudian ketikkan “DEF” pada box “LCC” sebagai ID dari kelas perubahan penutupan lahan “Deforestation”.
    7. Melakukan dissolve poligon kelas perubahan penutupan lahan (field “LCC”) menggunakan menu “Geoprocessing” dengan tujuan menggabungkan poligon pada setiap kelas perubahan penutupan lahan menjadi menjadi 1 (satu) poligon utuh.
    8. Menghitung luas masing-masing kelas perubahan penutupan lahan dengan satuan unit hektar (ha). Data penutupan lahan nasional yang digunakan dalam buku ini mempunyai sistem koordinat Geografi (Geographic Coordinate System)-WGS 1984, sehingga proyeksinya perlu diubah menjadi WGS 1984 PDC Mercator, untuk mendapatkan luas dalam satuan hektar. Setelah itu dilakukan penambahan field “Luas” untuk masing-masing kelas
    9. perubahan penutupan lahan dan dilanjutkan dengan penghitungan luasnya.
    10. Menyajikan peta areal stratifikasi perubahan penutupan lahan.

Langkah-langkah pembuatan peta sebaran sampel adalah sebagai berikut:
    1. Membuat titik sampel dengan fasilitas “Create Random Points” untuk semua kelas perubahan penutupan lahan berdasarkan data hasil dissolve dalam format geodatabase.
    2. Sampel untuk setiap kelas perubahan penutupan lahan dibuat dengan jumlah/ukuran yang sama, yaitu 150 sampel, sesuai dengan hasil penghitungan titik sampel per kelas pada tabel contoh hasil perhitungan sebaran sampel. Semua titik sampel masih berupa ID (pada field “CID”), yaitu ID=1 untuk kelas deforestation (DEF), ID=2 untuk kelas forest degradation (DEG), ID=3 untuk kelas stable forest (SF), dan ID=4 untuk kelas stable non-forest (SNF).
    3. Membuat buffer dengan luas 6,25 ha untuk semua titik sampel. Buffer yang dibuat dalam bentuk lingkaran, sehingga jari-jari (r) untuk setiap lingkaran adalah 141 meter.
    4. Untuk memudahkan proses interpretasi titik sampel pada setiap kelas perubahan penutupan lahan, setiap sampel kelas perubahan diekspor menjadi file terpisah. Hal ini juga akan memudahkan ketika proses penghitungan uncertainty maupun penambahan sampel untuk setiap kelas perubahan penutupan lahan jika diperlukan. Proses ekspor data spasial dapat dilakukan dengan cara “Select by Attributes” pada tabel kemudian pilih ID sampel kelas perubahan penutupan lahan, misalnya kelas deforestation (CID=1). Kemudian klik kanan pada “nama file sampel (layers)”, pilih Data > Export Data > nama output data (misal: Sampel_DEF_NTB_00_22). Tahapan ini dilakukan untuk semua kelas perubahan penutupan lahan dan data buffer-nya.
    5. Menambah field (kolom) pada tabel data sampel setiap kelas perubahan penutupan lahan yang akan digunakan dalam proses interpretasi/analisa sampel.
       
       ![[Pasted image 20240517111735.png]]
       ![[Pasted image 20240517111749.png]]

Analisa/pengamatan dilakukan pada titik sampel yang sudah disebar secara acak pada setiap kelas perubahan penutupan lahan (stratified) dengan menggunakan metode analisa decision tree. Kegiatan ini dilakukan dengan mengamati secara visual setiap sampel pada 2 periode mosaik citra Landsat. Data citra resolusi tinggi tahun yang bersangkutan dan citra mosaik Landsat periode tahun sebelum dan sesudah pengamatan juga digunakan untuk memastikan kelas perubahan penutupan lahannya. Analisa dilakukan pada sampel berupa poligon buffer. Hasil analisa sampel dimasukkan dalam tabel yang sudah dibuat sebagai data atribut dari sampel. Dalam buku ini, hanya sampel clear yang digunakan dalam proses analisa data sampel dan akan diperhitungkan dalam penentuan akurasi dan uncertainty perubahan penutupan lahan. Sampel clear adalah titik sampel dan poligon buffer-nya yang sebagai MMU tidak berada di garis batas/delineasi poligon kelas perubahan penutupan lahan yang berbeda, tidak tertutup awan (tidak ada citra lain yang dapat menerangkan kondisi sampel pada saat periode pengamatan), dan tidak overlap/menumpuk dengan sampel yang sudah dianalisa sebelumnya.

Sampel kelas perubahan penutupan lahan yang diamati harus clear sesuai dengan persyaratan di metode decision tree. Dengan demikian jika ada sampel yang berada di perbatasan poligon kelas perubahan penutupan lain, tertutup awan di semua data citra, dan bertumpuk dengan sampel yang sudah dianalisa harus digeser sesuai dengan ketentuan, kecuali pada beberapa kasus. Apabila sampel tidak clear dan tidak dapat digeser karena berbagai kondisi yang tidak memenuhi persyaratan yang sudah ditentukan, maka sampel tidak akan digunakan. Sampel ini akan diganti dengan sampel lain yang penentuannya sesuai Metode Penggantian Sampel.

Sampel harus diganti agar jumlah sampel optimal yang diperlukan dapat terpenuhi. Sampel pengganti ditentukan secara sistematik berdasarkan sampel yang sudah clear pada kelas perubahan penutupan lahan yang sama. Sampel pengganti akan mempunyai ID yang sama dengan sampel yang tidak digunakan atau sampel yang sudah dihapus. Prosedur penggantian sampel ditentukan dengan cara sebagai berikut:
    1. Jumlah sampel yang diganti sama dengan jumlah sampel yang tidak digunakan/dihapus.
    2. Perlu dihitung interval penentuan sampel yang akan digunakan sebagai dasar dalam penggantian sampel, yaitu dengan membagi jumlah sampel clear dengan jumlah sampel yang tidak digunakan. Sebagai contoh, jumlah sampel yang tidak digunakan adalah 3 (tiga), sedangkan jumlah sampel yang clear adalah 147. Dengan demikian interval sampel adalah 49, yang merupakan hasil pembagian 147 dengan 3. Apabila hasil pembagian angkanya tidak bulat, maka dapat dibulatkan ke atas atau ke bawah dengan ketentuan ≥ 0,5 akan dibulat ke atas, misalnya ketemu hasil 48,6, maka interval penggantian sampel adalah 49.
    3. Berdasarkan poin 2 tersebut, penentuan posisi sampel pengganti pertama akan dimulai pada sampel dengan No_ID 49, yang kemudian berlanjut ke sampel berikutnya dengan interval 49 hingga semua sampel yang tidak digunakan dapat diganti. Penggantian sampel ini dilakukan secara urut dari sampel dengan No_ID terkecil pada sampel yang tidak digunakan, hingga No_ID sampel terbesar. Sebagai contoh, apabila ada 3 sampel yang tidak digunakan dengan No_ID sampel 25, 80, dan 123, maka penggantian sampel dimulai dari sampel dengan No_ID 25 hingga ke sampel terakhir adalah sampel No_ID 123. Ketiga sampel tersebut diganti dengan sampel yang ditempatkan berdasarkan sampel No_ID 50, 99 dan 150.
    4. Apabila ada sampel pengganti yang tetap tidak memenuhi persyaratan atau sampel tidak clear, maka proses penentuan sampel harus diulang seperti pada poin 2 dan poin 3 hingga jumlah sampel optimal.
    5. Pada tahapan di poin 4, sampel pengganti yang tidak digunakan yang merupakan hasil proses poin 2 dan poin 3, tidak dimasukkan dalam proses pemilihan sampel pengganti secara sistematik berikutnya.
    6. Metode penentuan posisi sampel pengganti yang merupakan hasil dari poin 2 dilakukan dengan prosedur seperti pada metode pergeseran sampel.

Langkah selanjutnya adalah melakukan penghitungan akurasi dan uncertainty setiap kelas perubahan penutupan lahan berdasarkan sampel yang sudah dianalisa. Apabila nilai uncertainty masih tinggi, ada kemungkinan jumlah sampel yang digunakan belum mencukupi, untuk itu perlu dilakukan penambahan sampel setiap 10% hingga mencapai 100% atau jumlah sampel optimal atau tidak ada penurunan nilai uncertainty. Metode penambahan sampel ini tetap mengacu pada decision tree yang sudah digunakan pada proses pergeseran dan penggantian sampel.

Penambahan sampel hanya dilakukan pada kelas perubahan penutupan lahan yang mempunyai nilai uncertainty tinggi (>15%), sebagai contoh kelas deforestation dan forest degradation. Berdasarkan banyak penelitian, untuk kelas penutupan lahan yang tidak berubah, seperti stable forest atau stable non-forest biasanya mempunyai nilai uncertainty kecil, sehingga tidak perlu dilakukan penambahan sampel. Tahapan untuk penambahan sampel adalah sebagai berikut:
    1. Penambahan sampel dilakukan sesuai dengan jumlah sampel clear, hingga sampel mencapai jumlah optimum (tidak dapat ditambah lagi).
    2. Penambahan sampel ditentukan secara sistematik berdasarkan sampel clear.
    3. Penambahan sampel tetap dilakukan pada poligon kelas perubahan yang sama dengan sampel yang dijadikan dasar penambahan sampel.
    4. Sampel yang ditambahkan harus clear sesuai dengan decision tree yang sudah ditetapkan sebelumnya.
    5. Penomoran ID sampel tidak boleh sama dengan No_ID sampel yang sudah ada, sehingga tidak membingungkan. No_ID sampel tambahan juga dapat melanjutkan No_ID sampel yang sudah ada sebelumnya.
    6. Prosedur penempatan posisi sampel yang ditambahkan sama dengan prosedur pergeseran dan penggantian sampel.
    7. Namun demikian ada beberapa sampel yang tidak dapat ditambah karena tidak memenuhi prosedur untuk menjadi sampel clear seperti yang ditetapkan dalam decision tree, sebagai contoh karena luas poligon kelas perubahan penutupan lahan yang terbatas (kecil).

Seluruh hasil uji akurasi dihitung dan dianalisa dengan confusion matrix (matriks error), yang merupakan sebuah matriks untuk memvisualisasikan kinerja suatu algoritma klasifikasi. Setiap kolom dari matriks tersebut mewakili kelas data referensi yang berasal dari data citra (Landsat dan citra resolusi tinggi dan/atau data lapangan). Sementara, setiap baris mewakili kelas hasil klasifikasi data (peta) perubahan penutupan lahan yang dibuat. Matriks error dihitung berdasarkan jumlah sampel (𝑝ij) yang mempunyai kesesuaian antara data atau peta referensi dengan hasil klasifikasi 7. Kolom diagonal menunjukkan jumlah sampel yang sesuai antara data hasil klasifikasi perubahan penutupan lahan dan data referensi.

![[Pasted image 20240517112101.png]]
Matriks error hasil interpretasi titik sampel

Untuk menganalisis proporsi luas peta yang telah diklasifikasikan dengan benar, jumlah sampel (𝑛ij) dikonversi menjadi area (ha) dengan menggunakan persamaan:

![[Pasted image 20240517112121.png]]

Dimana:
Pij : estimasi proporsi luas setiap kelas
𝑊i : proporsi area yang diklasifikasikan di dalam kelas i (persamaan 2)
𝑛ij : Jumlah sampel pada strata i yang sesuai dengan data referensi
𝑛i : Jumlah total sampel pada strata i

Berdasarkan matriks error hasil interpretasi pada semua sampel kelas perubahan penutupan lahan dibuat matriks error estimasi proporsi area masing-masing kelas perubahan penutupan lahan sesuai sesuai dengan sampel. Contoh perhitungan estimasi proporsi untuk kelas deforestation: