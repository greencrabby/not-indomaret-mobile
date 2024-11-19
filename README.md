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
              ),
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

# ---TUGAS 8---

## Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?
Di Flutter, `const` digunakan untuk membuat objek yang bersifat immutable dan hanya dibuat sekali saat compile-time, sehingga menghemat penggunaan memori dan meningkatkan performa aplikasi karena tidak perlu membuat objek yang sama berulang kali. Keuntungan menggunakan `const` adalah aplikasi menjadi lebih efisien dan responsif karena elemen statis tidak perlu di-render ulang setiap kali widget dibangun kembali. Sebaiknya gunakan `const` ketika membuat widget atau objek yang nilainya tidak akan berubah selama runtime, seperti teks statis, ikon, atau gaya. Namun, `const` tidak perlu digunakan jika nilai dari objek bisa berubah berdasarkan kondisi tertentu atau input pengguna, karena dalam kasus ini objek perlu di-rebuild agar sesuai dengan kondisi terbaru.

## Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
Pada Flutter, `Column` dan `Row` adalah widget layout yang digunakan untuk menyusun elemen secara vertikal dan horizontal. `Column` menyusun widget dari atas ke bawah, sedangkan `Row` menyusun widget dari kiri ke kanan. Keduanya menerima daftar widget sebagai anak, sehingga bisa digunakan untuk mengatur tata letak beberapa elemen sekaligus. `Column` dan `Row` memiliki properti alignment seperti `mainAxisAlignment` dan `crossAxisAlignment` untuk mengatur posisi anak-anak widget di sepanjang sumbu utama dan sumbu silang.
```dart
// Contoh implementasi column
child: const Column(
  children: [
    Text(
      'Not Indomaret',
      textAlign: TextAlign.center,
      style: TextStyle(
        fontSize: 24,
        fontWeight: FontWeight.bold,
        color: Colors.white,
      ),
    ),
    Padding(padding: EdgeInsets.all(8)),
    Text(
      "Menjual Semuanya Kecuali yang Dijual Indomaret",
      textAlign: TextAlign.center,
      style: TextStyle(
        fontSize: 15,
        color: Colors.white,
        fontWeight: FontWeight.normal,
      ),
    ),
  ],
),
```
```dart
// Contoh implementasi row
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    InfoCard(title: 'NPM', content: npm),
    InfoCard(title: 'Name', content: name),
    InfoCard(title: 'Class', content: className),
  ],
),
```

##  Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!
Pada halaman form `ProductEntryFormPage`, terdapat tiga elemen input utama yang digunakan: `TextFormField` untuk menerima input `_name`, `_amount`, dan `_description`. Ketiga elemen `TextFormField` ini masing-masing memiliki validasi agar tidak kosong dan, khusus untuk jumlah produk, validasi tambahan untuk memastikan bahwa input berupa angka. Selain `TextFormField`, terdapat beberapa elemen input Flutter lain yang tidak digunakan dalam tugas ini, seperti `DropdownButton` (untuk pilihan bertingkat), `Checkbox` (untuk input boolean), `Radio` (untuk memilih satu opsi dari beberapa opsi), `Switch` (untuk input on/off), dan `Slider` (untuk nilai rentang).

## Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
Tema aplikasi flutter saya diatur melalui Material App. Tema utama saya berisi di `colorScheme`. Isi dari skema warna tersebut adalah warna deep purple sebagai warna utama dan deep purple 400 sebagai warna sekunder. Sehingga tema aplikasi konsisten dengan implementasi melalui penggunaan potongan code `color: Theme.of(context).colorScheme.primary,` di beberapa screen.

## Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?
Dalam konteks aplikasi ini, navigasi antarhalaman diatur melalui `LeftDrawer`. Setiap item `ListTile` di dalam `Drawer` digunakan untuk mengarahkan pengguna ke halaman yang berbeda, seperti `MyHomePage` dan `ProductEntryFormPage`. Navigasi ini dilakukan dengan menggunakan `Navigator.pushReplacement`, yang menggantikan halaman saat ini dengan halaman tujuan tanpa menambahkannya ke tumpukan, sehingga pengguna tidak dapat kembali ke halaman sebelumnya dengan tombol kembali. Hal ini cocok untuk navigasi utama dalam aplikasi, seperti pindah antarhalaman inti dari menu.

# ---TUGAS 9---

## Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?
Kita perlu membuat model untuk pengambilan atau pengiriman data JSON karena model berfungsi sebagai kerangka kerja yang mendefinisikan struktur data secara sistematis, seperti tipe data dan relasi antar atribut. Model memastikan data yang diterima atau dikirim sesuai dengan format yang diharapkan, sehingga meminimalkan risiko kesalahan seperti tipe data yang tidak cocok atau data yang tidak lengkap. Tanpa model, proses manipulasi data menjadi lebih rentan terhadap error karena tidak ada validasi atau kontrol yang terstruktur. Meskipun mungkin tidak langsung terjadi error jika model tidak dibuat, aplikasi dapat mengalami masalah seperti data yang tidak konsisten, sulit dikelola, atau sulit diintegrasikan dengan sistem lain. Dengan model, pengelolaan data menjadi lebih mudah, efisien, dan terjamin keakuratannya.

## Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini
Library http pada tugas ini digunakan untuk melakukan komunikasi antara aplikasi Flutter dengan server backend, seperti pengambilan (GET) atau pengiriman (POST) data melalui protokol HTTP. Library ini memungkinkan aplikasi untuk mengirim permintaan HTTP ke server, menerima respons, dan memproses data yang dikirim dalam format seperti JSON. Dalam tugas ini, library http digunakan untuk:
1. Mengambil Data (GET): Misalnya, saat mengambil daftar produk atau detail tertentu dari server dalam format JSON.
2. Mengirim Data (POST): Untuk mengirimkan data baru, seperti informasi produk yang diinputkan pengguna, ke backend untuk disimpan di database.
3. Mengelola Respons: Library ini membantu membaca respons server, seperti status keberhasilan atau pesan error, sehingga dapat ditampilkan atau diolah lebih lanjut di aplikasi.
Dengan library http, aplikasi Flutter dapat berfungsi secara dinamis dengan backend, mendukung integrasi data secara real-time.

## Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
Fungsi dari `CookieRequest` adalah untuk mengelola permintaan HTTP yang memerlukan pengelolaan cookies, seperti autentikasi pengguna atau sesi yang berkelanjutan antara aplikasi Flutter dan server backend. `CookieRequest` memungkinkan aplikasi untuk secara otomatis menangani cookies yang disertakan dalam respons dari server, seperti token otentikasi, dan mengirimkannya kembali dalam permintaan berikutnya. Hal ini sangat penting untuk menjaga status pengguna antara sesi aplikasi. Instance `CookieRequest` perlu dibagikan ke semua komponen aplikasi karena cookies perlu dipertahankan dan digunakan di berbagai bagian aplikasi, dan dengan membagikan instance ini menggunakan provider, memastikan konsistensi dan akses mudah ke objek `CookieRequest` di seluruh aplikasi tanpa perlu membuat instance baru di setiap permintaan, yang mengurangi kompleksitas dan potensi kesalahan.

## Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
Mekanisme pengiriman data dimulai ketika pengguna memasukkan data melalui antarmuka aplikasi Flutter, seperti formulir input. Data yang diinput akan diproses dan dikemas dalam format yang sesuai (misalnya JSON), kemudian dikirim ke server menggunakan metode HTTP POST. Server akan menerima data, memprosesnya, dan menyimpannya di database. Setelah itu, server mengirimkan respons kembali, yang biasanya berupa status atau data yang baru diproses. Aplikasi Flutter menerima respons tersebut, mendekode data (misalnya dalam format JSON), dan menampilkannya pada antarmuka pengguna sesuai dengan kebutuhan, seperti memperbarui daftar produk atau menampilkan pesan konfirmasi.

## Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
Mekanisme autentikasi dimulai ketika pengguna memasukkan data akun (username dan password) melalui formulir login di aplikasi Flutter. Data tersebut dikirim ke server Django menggunakan metode HTTP POST, dimana Django memverifikasi kredensial pengguna dengan membandingkannya dengan data yang ada di database. Jika autentikasi berhasil, Django membuat sesi atau token autentikasi dan mengirimkan respons yang menyatakan keberhasilan login, yang kemudian diterima oleh Flutter dan disimpan (misalnya, dalam cookie atau token). Setelah itu, pengguna diarahkan ke halaman utama (menu) di Flutter, yang hanya dapat diakses jika sudah login. Untuk logout, pengguna mengirimkan permintaan ke Django untuk mengakhiri sesi, dan server menghapus sesi atau token tersebut, kemudian Flutter mengarahkan kembali pengguna ke halaman login.

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).
TBA