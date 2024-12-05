A projection is described by a coordinate reference system (CRS), which consists of two elements: (a) The geodetic datum, which is a geodetic reference system placing reference locations on a geometrical body (e.g. a rotation ellipsoid), representing the Earth’s approximate spherical shape. (b) A coordinate system, which projects a coordinate grid (cylindrical, conic or planar) onto the geodetic reference system.

A **projection** in the context of geographic information systems (GIS) involves transforming the three-dimensional surface of the Earth (which is approximately an ellipsoid or spheroid) onto a two-dimensional plane (such as a map). To achieve this transformation, a **coordinate reference system (CRS)** is used, and it consists of two key elements:

### 1. **Geodetic Datum**

- A **geodetic datum** defines the shape of the Earth and establishes a reference framework for geographic coordinates. It provides a model of the Earth's shape (which is not perfectly spherical but more like an ellipsoid or spheroid).
- The datum is based on a specific ellipsoid or spheroid (such as WGS84, NAD83, or GRS80) that approximates the shape of the Earth. It also includes parameters like the Earth's center of mass, orientation in space, and the size of the ellipsoid.
- Common examples include:
    - **WGS84** (World Geodetic System 1984): The most widely used datum for global positioning systems (GPS).
    - **NAD83** (North American Datum 1983): Used primarily in North America.

### 2. **Coordinate System**

- The **coordinate system** is a grid that helps define how positions on the Earth's surface are represented using numerical values (e.g., latitude, longitude, and elevation).
- It involves defining the grid system that will map locations in 2D (on a flat surface) based on the chosen datum.
- The grid can be:
    - **Cylindrical**: For example, the **Mercator projection**, where the Earth is projected onto a cylinder.
    - **Conic**: For example, the **Albers Equal Area Conic** projection, which projects the Earth onto a cone.
    - **Planar** (or Azimuthal): For example, the **Lambert Conformal Conic** projection, which projects onto a flat plane.

Each coordinate system used in a projection is designed to preserve certain properties, like distances, areas, angles, or directions, depending on the purpose of the projection.

### Putting it together:

- The **datum** gives you the shape and position of the Earth.
- The **coordinate system** provides the mathematical framework to map locations from the Earth's surface (as defined by the datum) onto a 2D plane or surface for easier analysis or display.

By combining both of these elements, you can define a **Coordinate Reference System (CRS)**, which is essential for correctly interpreting and using geospatial data in applications like mapping, navigation, and geodesy.


Contoh: WGS84/UTM 50S
- Kalau menggunakan geographical coordinate system hanya butuh WGS85
- Kalau menggunakan projected coordinate system berarti selain ditampilkan WGS84 juga harus dilengkapi sistem proyeksinya yaitu UTM 50S

=================
### **1. Sistem Koordinat Geografis (Geographical Coordinate System)**

- **WGS84** (World Geodetic System 1984) adalah sistem koordinat geografis yang menggunakan **latitude** dan **longitude** untuk menentukan posisi suatu titik di permukaan bumi.
- Dalam hal ini, sistem referensinya adalah **WGS84** saja, yang mengacu pada koordinat berbasis bumi (seperti pada GPS).
- **Contoh**: Koordinat titik yang hanya menggunakan WGS84 adalah:
    - **Latitude**: 3.1390° S
    - **Longitude**: 106.8162° E

### **2. Sistem Koordinat Proyeksi (Projected Coordinate System)**

- Dalam **sistem koordinat proyeksi**, koordinat bumi yang melengkung diproyeksikan ke dalam bidang datar menggunakan suatu jenis proyeksi (seperti UTM).
- **UTM** (Universal Transverse Mercator) adalah jenis sistem proyeksi yang membagi bumi menjadi zona-zona yang lebih kecil (terdiri dari 60 zona), di mana setiap zona menggunakan sistem proyeksi **Transverse Mercator**.
- **UTM 50S** adalah salah satu zona UTM yang berlaku di belahan bumi selatan (dari **zone 50S**) dengan proyeksi Transverse Mercator untuk wilayah tersebut.
- Proyeksi ini akan menggantikan penggunaan **latitude** dan **longitude** dengan **koordinat X (easting)** dan **Y (northing)**, serta zona proyeksinya.
- **Contoh**: Koordinat di sistem UTM 50S bisa terlihat seperti:
    - **Easting**: 500000 m
    - **Northing**: 5000000 m
    - **Zone**: 50S

### **Contoh Perbandingan**:

- **Geographical (WGS84)**:
    - 3.1390° S, 106.8162° E (Latitude dan Longitude)
- **Projected (UTM 50S)**:
    - Easting: 500000 m, Northing: 5000000 m, Zone: 50S

### Ringkasan:

- **WGS84** hanya digunakan untuk sistem koordinat geografis.
- **WGS84/UTM 50S** adalah kombinasi antara sistem geografis (WGS84) dengan sistem proyeksi (UTM 50S), yang digunakan untuk mendapatkan lokasi dalam bentuk koordinat proyeksi.

Jadi, untuk aplikasi pemetaan dan pengolahan data geospasial, kita harus menyertakan proyeksi sistem jika menggunakan **UTM**, sementara hanya **WGS84** cukup untuk koordinat geografis.