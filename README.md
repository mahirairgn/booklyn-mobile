# Tugas 9
### Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?
Bisa. Menurut saya, lebih baik untuk membuat model dulu sebelum melakukan pengambilan data JSON agar struktur datanya lebih mudah untuk dipahami sehingga datanya mudah untuk divalidasi. Selain itu, pembuatan model terlebih dahulu juga memudahkan proses identifikasi bug yang ada di program.

### Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
`CookieRequest` digunakan untuk mengirim HTTP request ke server yang membutuhkan cookie untuk autentikasi. Instance tersebut harus dibagikan ke semua komponen agar pengiriman HTTP request bisa dilakukan dari semua bagian di aplikasi sehingga tidak perlu untuk membuat instance baru untuk setiap bagian.

### Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.
1. Pastikan sudah memiliki data JSON dari sumber yang diinginkan
2. Membuat instance yang digunakan untuk mengirim HTTP request ke server
3. Mengirim HTTP request menggunakan fungsi `Future` yang mengambil data JSON dari server
4. Parsing data JSON yang diterima menggunakan `json.decode()`
5. Menampilkan data JSON menggunakan model

### Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
1. Pastikan terdapat form autentikasi di flutter untuk user memasukkan datanya
2. Implementasikan autentikasi pada server Django
3. Mengirim HTTP request ke endpoint autentikasi Django
4. Jika autentikasi berhasil, Django akan memberikan token akses secara lokal di Flutter yang harus disimpan
5. Gunakan token tersebut untuk autentikasi request ke endpoint
6. Jika request berhasil, tampilkan aplikasi menu pada interface user

### Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.
Widget yang digunakan pada tugas ini tidak jauh berbeda dengan widget yang digunakan pada tugas-tugas sebelumnya. Untuk penjelasannya dapat dilihat di readme tugas 6.
Beberapa widget baru yang digunakan di tugas ini adalah:
1. `Provider` mengelola dan menyediakan data ke seluruh aplikasi
2. `TextField` digunakan sebagai tempat pengguna memasukkan teks
3. `SizedBox` memberi ruang yang bersifat tetap di antara elemen-elemen pada widget 
4. `ElevatedButton` adalah tombol untuk memanggil suatu aksi dan dilengkapi dengan efek elevasi
5. `FutureBuilder` membangun widget sesuai hasil dari operasi asynchronous Future
6. `ListView.builder` membuat daftar item dalam bentuk list sehingga dapat di-scroll
7. `TextButton` digunakan sebagai tombol dengan gaya teks
8. `Form` untuk mengelola state formulir dan memvalidasi input pengguna.
9. `GlobalKey` digunakan untuk mengidentifikasi state dari formulir atau widget lainnya.
10. `TextEditingController` untuk mengontrol teks yang ditampilkan dan diubah dalam TextField.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).
1. Membuat app baru bernama `authentication` pada folder `booklyn` yang berbasis Django. Tambahkan kode ke `views.py` kemudian buat file `urls.py` baru dan lakukan routing dengan endpoint `login/`. Lalu, tambahkan `path('auth/', include('authentication.urls')),` ke file `urls.py` yang ada di folder `booklyn`
2. Jalankan perintah `pip install django-cors-headers` kemudian tambahkan `corsheaders` di bagian `INSTALLED_APPS` dan `corsheaders.middleware.CorsMiddleware` di bagian `MIDDLEWARE` pada file `settings.py`
3. Tambahkan `django-cors-headers` di file `requirements.txt` kemudian jalankan perintah `pip install -r requirements.txt`
4. Tambahkan beberapa variabel baru ke `settings.py`
5. Jalankan perintah `flutter pub add provider` dan `flutter pub add pbp_django_auth` untuk meng-*install* package yang sudah disediakan, serta perintah `flutter pub add http`
6. Modifikasi root widget agar `CookieRequest` library tersedia untuk semua child widgets menggunakan `Provider`
7. Buat file baru bernama `login.dart` dan `list_product.dart` pada folder `screens` kemudian isi kode yang sesuai dengan tampilannya
8. Ubah `home: MyHomePage()` menjadi `home: LoginPage()` pada widget `MaterialApp(...)` di file `main.dart`
9. Buka endpoint `JSON` pada web dengan Django sebelumnya, kemudian *copy* datanya dan masukkan ke web Quicktype. Lalu *copy* kode yang muncul dan *paste* ke dalam file baru bernama `product.dart` pada folder `lib/models`
10. Tambahkan kode di `android/app/src/main/AndroidManifest.xml` untuk mengizinkan akses internet pada aplikasi Flutter 
11. Tambahkan `ListTile` baru pada `left_drawer.dart` untuk menambahkan halaman `list_product.dart`
12. Arahkan tombol `Lihat Item` ke halaman `ProductPage` ketika diklik dengan menambahkan kode `else if` yang sesuai di bagian `onTap` pada file `shop_card.dart`
13. Buat file baru bernama `detail_product.dart` pada `lib/screens` dan masukkan kode untuk menampilkan detail dari setiap produk. Kemudian, tambahkan kode `onTap(...)` pada bagian `itemBuilder` di `list_product.dart` agar setiap produk dapat mengarah ke halaman `detail_product.dart` ketika diklik
14. Buat fungsi baru bernama `create_product_flutter` di `main/views.py` dan tambahkan kode yang sesuai. Lalu, tambahkan path baru di `main/urls.py`
15. Tambahkan kode untuk menghubungkan `CookieRequest` dengan `shoplist_form.dart` dan `shop_card.dart`. Kemudian, ubah kode di bagian `onPressed()` dan `onTap()` sehingga sekarang bersifat async
16. Buat fungsi baru bernama `logout` pada `authentication/views.py` dan tambahkan kode yang sesuai. Lalu, tambahkan pathnya ke `urls.py` di folder yang sama

-------------------------------------------------------------------------------------------------------------------------------

# Tugas 8
###  Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!
- `Navigator.push()` berfungsi untuk navigasi ke halaman baru dan menambahkannya ke stack. Sehingga user dapat kembali dari halaman baru ke halaman sebelumnya menggunakan tombol back. Contoh:
```
Navigator.push(
    context,
    MaterialPageRoute(
        builder: (context) => const ShopFormPage(),
    ));
```
- `Navigator.pushReplacement` juga berfungsi untuk navigasi ke halaman baru, tetapi halaman baru itu akan menggantikan halaman saat ini sehingga user tidak bisa kembali ke halaman sebelumnya. Contoh:
```
Navigator.pushReplacement(
    context,
    MaterialPageRoute(
        builder: (context) => const ShopFormPage(),
    ));
```

### Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!
1. `Container` digunakan untuk menambahkan padding, margin, border, warna latar, dan sebagainya sesuai keinginan
2. `GridView` adalah layout yang berbentuk grid. Biasanya digunakan untuk menampilkan konten dalam format grid
3. `ListView` menampilkan konten dalam bentuk daftar secara vertikal atau horizontal dan bisa di-*scroll* jika ukuran konten tidak pas dengan tampilan (misal: terlalu besar atau panjang)
4. `Stack` memungkinkan untuk meletakkan sebuah widget di atas widget lainnya. Misalnya menumpuk widget teks dan gambar
5. `Row dan Column` berfungsi untuk mengatur widget secara horizontal dalam baris (row) dan vertikal dalam kolom (Column)
6. `Align` mengatur penyesuaian posisi widget child dalam widget itu sendiri
7. `Expanded` dapat memperluas widget anak dari row dan column agar mengisi ruang yang ada

### Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!
Pada form di tugas ini, saya menggunakan elemen`TextFormField`. Elemen tersebut memiliki kegunaan yang sama dengan `TextField`, yaitu menerima input teks dari user. Namun, saya lebih memilih menggunakan `TextFormField` agar dapat memvalidasi input user dengan lebih mudah, karena elemen tersebut memiliki `validator` yang merupakan built-in untuk validasi

### Bagaimana penerapan clean architecture pada aplikasi Flutter?
Penerapan *clean architecture* pada Flutter berkaitan dengan pemisahan aplikasi menjadi beberapa *layer* berdasarkan suatu prinsip. Ada 3 *layer* utama dalam arsitektur ini:
1. **Data Layer** yang bertanggung jawab terhadap pengambilan data
2. **Domain Layer** yang berkaitan dengan logika aplikasi dan model data
3. **Feature Layer** yang berisi UI dan *event handler*-nya. Selain itu, ada juga dua *supporting layer*, yaitu **Resources** dan **Shared Library** yang dapat diakses oleh *layer* lainnya

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)
1. Membuat direktori baru bernama `widgets` dan `screens`. Kemudian pindahkan file `menu.dart` ke folder `screens`
2. Buat file baru bernama `left_drawer.dart` di folder `widgets` lalu tambahkan kode untuk membuat drawer dan lakukan routing ke halaman yang diinginkan
3. Impor drawer ke file `menu.dart`
4. Buat file baru bernama `shoplist_form.dart` di folder `screens` dan tambahkan kode untuk membuat form dengan elemen input yang sesuai, serta bisa divalidasi dan disimpan
5. Meakukan routing pada tombol "Tambah Item" agar dapat mengarah ke form ketika diklik
6. Membuat file baru bernama `shop_card.dart` di folder `widgets`. Selanjutnya, pindahkan isi widget `ShopItem` dari `menu.dart` dan impor `shoplist_form.dart` ke file tersebut

-------------------------------------------------------------------------------------------------------------------------------

# Tugas 7
### Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?
- **Stateless Widget** adalah widget yang tidak akan pernah berubah karena tidak memiliki internal state yang berubah. Lebih efisien karena tidak perlu memperbarui tampilan saat ada perubahan data. Contoh: Teks statis yang tidak punya fungsi untuk mengubah isi dari text tersebut.
- **Stateful Widget** adalah widget yang dapat berubah secara dinamis (memperbarui tampilannya saat data atau kondisi di dalamnya berubah). Contoh: Tombol yang bisa diklik dan memengaruhi perubahan data.

### Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.
- `MyHomePage` adalah kelas turunan dari `StatelessWidget` yang membangun halaman utama aplikasi.
- `Scaffold` adalah widget yang menampilkan struktur dasar aplikasi. Mencakup widget lainnya, yaitu `AppBar` dan `Body`
- `AppBar` adalah widget di bagian atas aplikasi yang menampilkan judul aplikasi.
- `Text` untuk menampilkan teks
- `SingleChildScrollView` adalah widget yang memungkinkan konten dapat di-*scroll* jika terlalu panjang
- `Padding` adalah widget untuk memberikan padding (jarak) dengan widget lain
- `Column` adalah widget untuk mengatur tampilan widget anak-anaknya secara vertikal
- `GridView` adalah widget untuk menampilkan grid berisi widget anak-anaknya dengan jumlah baris & kolom tertentu
- `ShopItem` adalah kelas yang menyimpan data item toko (nama, ikon, warna)
- `ShopCard` adalah kelas untuk menampilkan item toko sebagai card. Datanya diperoleh dari `ShopItem`
- `Icon` untuk menampilkan ikon
- `Material` untuk memberikan efek visual Material Design ke widget lain
- `InkWell` untuk memberikan efek sentuhan ke widget lain
- `Container` untuk menggabungkan beberapa widget ke satu kotak
- `Center` untuk memusatkan widget anaknya ke tengah

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
1. Membuat program flutter baru bernama `booklyn` melalui perintah `flutter create booklyn`. Kemudian, masuk ke direktorinya
2. Membuat file baru bernama `menu.dart` dan mengimpor package `material.dart`
3. Mengimpor package `menu.dart` ke file `main.dart`
4. Memindahkan class `MyHomePage` dan `_MyHomePageState` dari `main.dart` ke `menu.dart`
5. Menghapus argumen title pada `MyHomePage` di file `main.dart` dan mengubah sifatnya menjadi stateless dengan menambahkan kode `extends StatelessWidget` kemudian sesuaikan kode di dalamnya
6. Me-*define* tipe yang digunakan di list melalui class bernama `ShopItem`. Kemudian, menambahkan item yang akan ditampilkan ke dalam list items
7. Menambahkan kode untuk menampilkan halaman beranda aplikasi yang mencakup `AppBar` dan `Grid`
8. Membuat widget stateless baru untuk menampilkan card
9. Mengubah warna button sehingga setiap button memiliki warna yang berbeda