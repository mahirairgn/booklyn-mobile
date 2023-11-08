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