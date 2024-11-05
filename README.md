# not-indomaret-mobile
=======
# not-indomaret-mobile

## ---TUGAS 7---

### Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
Stateless Widget adalah widget di Flutter yang tidak mengalami perubahan keadaan setelah dibuat; widget ini hanya menampilkan UI berdasarkan data yang diberikan dan harus dibuat ulang jika data berubah. Contohnya adalah widget seperti `Text` dan `Icon`, yang tetap konstan kecuali di-render ulang dengan data baru. Sementara itu, Stateful Widget dapat berubah sesuai interaksi pengguna atau peristiwa lainnya tanpa harus membangun ulang seluruh widget, karena memiliki objek `State` terpisah yang menyimpan dan memperbarui data widget secara dinamis. Stateful widget sangat berguna untuk elemen interaktif seperti formulir, tombol, dan animasi.

### Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.
1. `main.dart`

| Nama                        | Fungsi |
|-----------------------------|--------|
| `runApp`                    | Memulai aplikasi dengan menampilkan widget root (`MyApp`) pada layar penuh. |
| `MaterialApp`               | Memberikan konfigurasi utama untuk aplikasi, termasuk `title`, `theme`, dan `home`. Mengatur navigasi dan tema dasar aplikasi. |
| `MyApp`                     | Sebagai widget utama (`StatelessWidget`) dari aplikasi yang mengatur tema dan widget utama (`home`). |
| `ThemeData`                 | Mengonfigurasi tema aplikasi, memungkinkan penyesuaian warna, font, dan gaya visual lainnya. |
| `ColorScheme.fromSwatch`    | Membuat skema warna berdasarkan warna utama (`primarySwatch`) dan warna pelengkap (`secondary`). |

2. `menu.dart`

| Nama Widget   | Fungsi |
|---------------|--------|
| `Scaffold`    | Memberikan struktur dasar halaman Flutter, termasuk `AppBar` dan `body`. Biasanya digunakan untuk tata letak dasar aplikasi yang mendukung elemen-elemen seperti `AppBar`, `body`, dan lainnya. |
| `AppBar`      | Menampilkan judul aplikasi “Not Indomaret” di bagian atas halaman dengan teks berwarna dan berformat khusus. Bagian dari `Scaffold` dan biasanya menampilkan judul atau aksi seperti tombol kembali atau menu. |
| `Padding`     | Menambahkan jarak di sekitar widget untuk tata letak yang lebih rapi. Di sini digunakan untuk mengatur jarak di sekitar `Column` utama dan komponen lainnya. |
| `Column`      | Menyusun widget secara vertikal, digunakan untuk menempatkan komponen seperti `Row`, `Text`, dan `GridView` dalam satu kolom dari atas ke bawah. |
| `Row`         | Menyusun widget secara horizontal, digunakan untuk menampilkan beberapa `InfoCard` secara berdampingan dalam satu baris. |
| `Text`        | Menampilkan teks di layar dengan gaya tertentu. Digunakan, misalnya, untuk menampilkan nama aplikasi dan pesan selamat datang. |
| `GridView`    | Menampilkan widget dalam format grid. Digunakan untuk menampilkan `ItemCard` dalam susunan tiga kolom agar tampilan lebih rapi dan terstruktur. |
| `Card`        | Menyediakan kotak dengan efek bayangan yang sering digunakan untuk menyusun informasi. `InfoCard`, misalnya, digunakan untuk menampilkan detail seperti NPM, nama, dan kelas. |
| `Icon`        | Menampilkan ikon yang telah ditentukan, seperti ikon keranjang, tambah, dan logout di dalam `ItemCard` untuk memperjelas fungsi dari setiap item. |
| `InkWell`     | Menambahkan efek klik pada widget dan menjalankan fungsi tertentu saat widget ditekan, misalnya menampilkan pesan `SnackBar` ketika `ItemCard` diklik. |
| `SnackBar`    | Menampilkan pesan singkat di bagian bawah layar sebagai respons dari aksi pengguna, misalnya ketika tombol ditekan untuk menunjukkan aksi yang berhasil. |


### Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
Fungsi `setState()` dalam widget stateful Flutter digunakan untuk memberi tahu framework bahwa ada perubahan pada state widget yang memerlukan pembaruan tampilan. Ketika `setState()` dipanggil, Flutter akan memicu proses render ulang hanya pada bagian yang terdampak, memungkinkan perubahan pada UI terlihat segera tanpa perlu merender ulang seluruh halaman. Variabel yang dapat terdampak oleh fungsi ini adalah variabel yang dideklarasikan dalam kelas `State`, yang biasanya menyimpan data dinamis atau status aplikasi yang berubah seiring interaksi pengguna, seperti nilai counter, data input pengguna, atau elemen daftar yang diperbarui.

### Jelaskan perbedaan antara const dengan final.
Perbedaan antara `const` dan `final` dalam Dart terletak pada cara dan kapan nilai variabel diinisialisasi. `final` digunakan untuk mendeklarasikan variabel yang hanya dapat diatur sekali dan nilainya tidak dapat diubah setelah diinisialisasi, serta dapat diinisialisasi dengan nilai yang dihasilkan secara dinamis pada saat runtime. Sebaliknya, `const` digunakan untuk mendeklarasikan konstanta yang nilainya sudah ditentukan pada saat kompilasi, sehingga harus memiliki nilai yang tetap dan diketahui saat kompilasi. Objek yang dibuat dengan `const` adalah singleton, artinya jika ada dua objek `const` dengan nilai yang sama, Dart akan menggunakan instans yang sama di memori.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.