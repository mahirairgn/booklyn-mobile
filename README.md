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