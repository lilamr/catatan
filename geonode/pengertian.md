GeoNode adalah sebuah sistem manajemen konten geospasial, sebuah platform untuk pengelolaan dan publikasi data geospasial. Ini merupakan proyek bersama software open-source yang lebih matang dan stabil di bawah antarmuka yang konsisten dan mudah digunakan yang memungkinkan pengguna untuk berbagi data dan membuat peta interaktif.

GeoNode merupakan project open source yang dikembangkan untuk medukung pengembangan platform sistem informasi geografis berbasis web dan infrastruktur data spasial. GeoNode didesain untuk dapat dikembangkan lebih lanjut dan dapat diintegrasikan pada platform yang telah ada dan dapat menjadi salah satu aplikasi simpul (node) dari infrastruktur data spasial nasional(IDSN).

Fitur utama GeoNode yang dapat dijadikan dasar sebagai aplikasi simpul IDSN yang handal, antara lain:
1. Open Source Geospasial. GeoNode dibangun dari komponen project open source yaitu: Django, PostGIS, GeoServer, Pycsw, Geospasial Python libraries, OpenLayers, dan GeoExt. 
2. Infrastruktur Data Spasial (IDS). GeoNode mengimplementasikan dan mendukung institusi yang mengembangkan diri sebagai bagian dari infrastruktur data spasial. Infrastruktur data spasial harus mengimplementasi standar OGC untuk dapat mendukung interoperabilitas antar sistem. GeoNode mengaplikasikan GeoServer sebagai aplikasi yang berfungsi sebagai layanan web GIS. GeoServer mengaplikasikan kita dapat mempublikasikan data dari berbagai sumber menggunakan protokol dan standar dari OGC juga didukung oleh GeoNode dengan mengaplikasikan pycsw sebagai katalog dan penyedia layanan metadata. Berikut ini standar OGC yang didukung oleh GeoNode:
- Web Map Service (WMS)
- Web Feature Service (WFS)
- Web Coverage Service (WCS)
- Catalog Service for Web (CSW)
- Web Map Context (WMC)
- Tile Map Service (TMS)