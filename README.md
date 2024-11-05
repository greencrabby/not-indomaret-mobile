# not-indomaret-mobile

# ---TUGAS 7---

## Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
Stateless Widget adalah widget di Flutter yang tidak mengalami perubahan keadaan setelah dibuat; widget ini hanya menampilkan UI berdasarkan data yang diberikan dan harus dibuat ulang jika data berubah. Contohnya adalah widget seperti `Text` dan `Icon`, yang tetap konstan kecuali di-render ulang dengan data baru. Sementara itu, Stateful Widget dapat berubah sesuai interaksi pengguna atau peristiwa lainnya tanpa harus membangun ulang seluruh widget, karena memiliki objek `State` terpisah yang menyimpan dan memperbarui data widget secara dinamis. Stateful widget sangat berguna untuk elemen interaktif seperti formulir, tombol, dan animasi.

## Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.
1. `main.dart`

| Nama                        | Fungsi |
|-----------------------------|--------|
| `runApp`                    | Memulai aplikasi dengan menampilkan widget root (`MyApp`) pada layar penuh. |
| `MaterialApp`               | Memberikan konfigurasi utama untuk aplikasi, termasuk `title`, `theme`, dan `home`. Mengatur navigasi dan tema dasar aplikasi. |
| `MyApp`                     | Sebagai widget utama (`StatelessWidget`) dari aplikasi yang mengatur tema dan widget utama (`home`). |
| `ThemeData`                 | Mengonfigurasi tema aplikasi, memungkinkan penyesuaian warna, font, dan gaya visual lainnya. |
| `ColorScheme.fromSwatch`    | Membuat skema warna berdasarkan warna utama (`primarySwatch`) dan warna pelengkap (`secondary`). |

2. `menu.dart`

| Nama          | Fungsi |
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


## Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
Fungsi `setState()` dalam widget stateful Flutter digunakan untuk memberi tahu framework bahwa ada perubahan pada state widget yang memerlukan pembaruan tampilan. Ketika `setState()` dipanggil, Flutter akan memicu proses render ulang hanya pada bagian yang terdampak, memungkinkan perubahan pada UI terlihat segera tanpa perlu merender ulang seluruh halaman. Variabel yang dapat terdampak oleh fungsi ini adalah variabel yang dideklarasikan dalam kelas `State`, yang biasanya menyimpan data dinamis atau status aplikasi yang berubah seiring interaksi pengguna, seperti nilai counter, data input pengguna, atau elemen daftar yang diperbarui.

## Jelaskan perbedaan antara const dengan final.
Perbedaan antara `const` dan `final` dalam Dart terletak pada cara dan kapan nilai variabel diinisialisasi. `final` digunakan untuk mendeklarasikan variabel yang hanya dapat diatur sekali dan nilainya tidak dapat diubah setelah diinisialisasi, serta dapat diinisialisasi dengan nilai yang dihasilkan secara dinamis pada saat runtime. Sebaliknya, `const` digunakan untuk mendeklarasikan konstanta yang nilainya sudah ditentukan pada saat kompilasi, sehingga harus memiliki nilai yang tetap dan diketahui saat kompilasi. Objek yang dibuat dengan `const` adalah singleton, artinya jika ada dua objek `const` dengan nilai yang sama, Dart akan menggunakan instans yang sama di memori.

## Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.
### Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.
1. Membuka terminal dan lakukan `flutter create not_indomaret`
2. Modifikasi isi `main.dart` dalam direktori `lib` dan diubah menjadi:
```dart
import 'package:flutter/material.dart';
import 'package:not_indomaret/menu.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        // Invoke "hot reload" (save your changes or press the "hot
        // reload" button in a Flutter-supported IDE, or press "r" if you used
        // the command line to start the app).
        //
        // The application state is not lost during the reload. 
        // To reset the state, use hot restart instead.
        //
        // This works for code too, not just values: Most code changes can be
        // tested with just a hot reload.
         colorScheme: ColorScheme.fromSwatch(
              primarySwatch: Colors.deepPurple,
        ).copyWith(secondary: Colors.deepPurple[400]),
        useMaterial3: true,
      ),
      home: MyHomePage(),
    );
  }
}
```

### Membuat tiga tombol sederhana dengan ikon dan teks untuk: Melihat daftar produk (Lihat Daftar Produk), Menambah produk (Tambah Produk), dan Logout (Logout)
Buka file `menu.dart` dalam direktori `lib` dan tambahkan kode berikut:
```dart
class MyHomePage extends StatelessWidget {
    ...

    // Button list
    final List<ItemHomepage> items = [
        ItemHomepage("Lihat Daftar Produk", Icons.shopping_basket),
        ItemHomepage("Tambah Produk", Icons.add),
        ItemHomepage("Logout", Icons.logout),
    ];
    ...
}
...

class ItemHomepage {
  final String name;
  final IconData icon;

  ItemHomepage(this.name, this.icon);
}
...

class ItemCard extends StatelessWidget {
  // Display the card with an icon and name.

  final ItemHomepage item;
  final Color color;

  const ItemCard({super.key, required this.item, required this.color});

  @override
  Widget build(BuildContext context) {
    return Material(
      // Specify the color passed in as the background color.
      color: Theme.of(context).colorScheme.secondary,
      // Round the card border.
      borderRadius: BorderRadius.circular(12),

      child: InkWell(
        // Action when the card is pressed.
        onTap: () {
          // Display the SnackBar message when the card is pressed.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}"))
            );
        },
        // Container to store the Icon and Text
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              // Place the Icon and Text in the center of the card.
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

### Mengimplementasikan warna-warna yang berbeda untuk setiap tombol (Lihat Daftar Produk, Tambah Produk, dan Logout).
Buka file `main.dart` dalam direktori `lib` dan tambahkan kode berikut:
```dart
class MyHomePage extends StatelessWidget {
    ...

    // List of colors for the ItemCards
    final List<Color> itemColors = [
        Colors.blue,
        Colors.green,
        Colors.red,
    ];
    ...

    @override
    Widget build(BuildContext context) {
    // Scaffold provides the basic structure of the page with the AppBar and body.
    return Scaffold(
      ...
                  // Grid to display ItemCard in a 3 column grid.
                  GridView.count(
                    ...

                    // Display ItemCard for each item in the items list.
                    children: [
                      ItemCard(item: items[0], color: itemColors[0]),
                      ItemCard(item: items[1], color: itemColors[1]),
                      ItemCard(item: items[2], color: itemColors[2]),
                    ],
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
``` 
Kemudian modifikasi bagian kode berikut:
```dart
class ItemCard extends StatelessWidget {
  ...

  @override
  Widget build(BuildContext context) {
    return Material(
      // Specify the color passed in as the background color.
      color: color, // Modifikasi bagian ini
      ...
    );
  }
}
```

### Memunculkan Snackbar dengan tulisan: "Kamu telah menekan tombol Lihat Daftar Produk" ketika tombol Lihat Daftar Produk ditekan, "Kamu telah menekan tombol Tambah Produk" ketika tombol Tambah Produk ditekan, dan "Kamu telah menekan tombol Logout" ketika tombol Logout ditekan.
Sudah ada di kode sebelumnya, tidak perlu modifikasi, dalam file `menu.dart` dalam direktori `lib` ada kode berikut:
```dart
class ItemCard extends StatelessWidget {
  ...
  @override
  Widget build(BuildContext context) {
    return Material(
      ...
      child: InkWell(
        // Action when the card is pressed.
        onTap: () {
          // Display the SnackBar message when the card is pressed.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}"))
            );
        },
        ...
      ),
    );
  }
}
```