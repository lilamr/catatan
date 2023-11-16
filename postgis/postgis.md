PostGIS adalah sebuah ekstensi untuk database PostgreSQL yang memungkinkan pengguna untuk menyimpan, memanipulasi, dan menganalisis data geografis di dalam database relasional. PostGIS menyediakan tipe data geometri dan geografi yang memungkinkan pengguna untuk menyimpan dan memanipulasi data spasial seperti titik, garis, poligon, dan banyak lagi.

Dengan menggunakan PostGIS, pengguna dapat melakukan operasi spasial seperti pengukuran jarak antara dua titik, menemukan area yang dikelilingi oleh suatu poligon, menemukan lokasi terdekat, dan banyak lagi. PostGIS juga dapat digunakan untuk membangun aplikasi GIS (Geographic Information System) yang kompleks dengan dukungan peta interaktif dan analisis spasial.

PostGIS adalah salah satu ekstensi paling populer untuk PostgreSQL dan digunakan oleh banyak organisasi di seluruh dunia untuk mengelola dan menganalisis data geospasial.

PostGIS adalah sistem manajemen basis data spasial (Spatial Database Management System) yang memiliki beberapa kelebihan dibandingkan dengan sistem file seperti SHP, di antaranya:

1.  Integrasi Data: PostGIS memungkinkan pengguna untuk mengintegrasikan data spasial dengan data non-spaial dalam satu database, sehingga memudahkan analisis data dan pengambilan keputusan. Hal ini sulit dicapai dengan sistem file SHP karena data yang berbeda biasanya disimpan dalam file terpisah.
    
2.  Scalability: PostGIS dapat menangani volume data spasial yang jauh lebih besar daripada sistem file seperti SHP. PostGIS dapat diinstal di server dan digunakan oleh banyak pengguna secara bersamaan dengan performa yang stabil dan cepat.
    
3.  Kecepatan: PostGIS dapat melakukan operasi analisis spasial dan query data yang kompleks dengan lebih cepat daripada sistem file SHP. Hal ini disebabkan oleh dukungan indeks spasial pada PostGIS dan optimasi query yang lebih baik.
    
4.  Fungsionalitas: PostGIS menyediakan fungsi analisis spasial yang lengkap dan mendukung banyak algoritma analisis data spasial yang umum digunakan. Hal ini menjadikan PostGIS menjadi pilihan ideal untuk proyek-proyek yang membutuhkan analisis spasial yang kompleks.
    
5.  Keamanan dan backup: PostGIS memiliki fitur keamanan yang baik dan dapat melakukan backup data secara otomatis. Hal ini memungkinkan pengguna untuk memulihkan data dengan cepat jika terjadi kegagalan sistem atau kehilangan data.
    
6.  Interoperabilitas: PostGIS dapat berintegrasi dengan sistem informasi geografis (GIS) dan aplikasi pengolahan data lainnya melalui berbagai protokol dan standar seperti OGC WMS dan WFS. Sebaliknya, file SHP cenderung memerlukan konversi atau impor ke dalam format lain sebelum dapat digunakan di berbagai aplikasi.
    

Dalam ringkasan, PostGIS memungkinkan pengguna untuk mengintegrasikan data spasial dengan data non-spatial dalam satu database, dengan performa yang cepat, fungsionalitas yang lengkap, dan dukungan multi-pengguna. Hal ini sulit dicapai dengan sistem file seperti SHP, yang lebih cocok digunakan untuk proyek-proyek skala kecil. Namun, penggunaan PostGIS juga memerlukan pengetahuan dan keterampilan yang lebih tinggi daripada penggunaan sistem file seperti SHP.



====================================

It has a lot, and I mean a lot, of useful spatial functions to search, analyze, convert, and manage spatial data. With a GIS database, we can handle geographic data more eff i ciently because it contains functions and algorithms that make it easier to manipulate and analyze it.

Newer versions of PostGIS have introduced newer spatial index types such as spgist, BRIN, and support for parallelizing queries:  
1. Geometry—The planar type. This is the very first model, and it’s still the most popular type that PostGIS supports. It’s the foundation of the other types. It uses the Cartesian math you learned about in high school geometry.  
2. Geography—The spheroidal geodetic type. Lines and polygons are drawn on the earth’s curved surface, so they’re curved rather than straight lines. PostGIS 2.2 introduced support for any geodetic spatial reference systems, which means you can use geography for other planets, such as Mars or your own made-up world.  
3. Raster—The multi-band cell type. Rasters model space as a grid of rectangular cells, each containing a numeric array of values.  
4. Topology—The relational model type. Topology models the world as a network of connected nodes, edges, and faces. Objects are composed of these elements and may share these with other objects. There are really two related concepts in topology—the network, which defines what elements each thing is composed of, and routing. PostGIS 2+ packages the network topology model, which is often just referred to as topology.

keuntungan postgis:  
1. user management (schema and role)  
2. trigger function (auto add new field to table)  
3. default styling (save style)  
4. form data input (create form for data input > maintain data integrity)  
5. saving qgis project to DB (acces role)

