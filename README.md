# myportofolio_mobile

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Learn Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Flutter learning resources](https://docs.flutter.dev/reference/learning-resources)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

### Tugas 7

## Pertanyaan Reflektif
1. Widget tree pada Flutter dan hubungan induk-anak (parent-child) bekerja antar-widget:
- **Widget tree** adalah struktur hierarkis berbentuk pohon yang merepresentasikan susunan seluruh elemen antarmuka pengguna (User Interface) dalam sebuah aplikasi Flutter. Sebuah widget di flutter adalah semua komponen seperti tatak letak, warna, padding, teks, hingga aplikasi itu sendiri.
- Hubungan induk-anak bekerja dengan prinsip komposisi:
* **Parent Widget (induk):** Bertanggung jawab menentukan batasan ukuran, posisi, gaya, atau konteks bagi widget di bawahnya. (Contoh: `Scaffold`, `Column`, `Row`, `Center`, dan `Padding`).
* **Child / Children Widget (Anak):** Menerima batasan dari induknya, lalu menentukan ukurannya sendiri sesuai batasan tersebut sebelum melaporkan kembali posisinya ke induk untuk dirender di layar.
* Widget induk yang hanya menampung satu komponen menggunakan properti `child` (seperti `Padding` atau `Center`), sedangkan widget induk yang menampung banyak komponen secara berurutan menggunakan properti `children` berupa `List<Widget>` (seperti `Column`, `Row`, dan `GridView`).


2. Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya masing-masing!
* **`MyApp` (`StatelessWidget`):** Widget akar (*root widget*) khusus aplikasi yang menginisialisasi konfigurasi global aplikasi melalui `MaterialApp`.
* **`MaterialApp`:** Membungkus keseluruhan aplikasi dengan standar desain *Material Design*, mengatur tema warna (`ThemeData`), judul aplikasi, dan menentukan halaman utama (`home`).
* **`MyHomePage` (`StatelessWidget`):** Halaman utama aplikasi portofolio yang menampilkan informasi pemilik portofolio serta daftar menu aksi.
* **`Scaffold`:** Menyediakan kerangka tata letak visual dasar halaman *Material Design*, seperti bagian kepala halaman (`appBar`) dan area konten utama (`body`).
* **`AppBar`:** Menampilkan bilah judul (*header bar*) di bagian atas layar aplikasi.
* **`Text`:** Menampilkan rangkaian karakter atau teks di layar dengan gaya tertentu (`TextStyle`), seperti judul aplikasi, identitas mahasiswa, pesan sambutan, dan label tombol.
* **`Padding`:** Memberikan jarak ruang kosong (*padding*) di sekeliling widget anaknya agar elemen tidak menempel langsung ke tepi layar atau widget lain.
* **`Column`:** Menyusun daftar widget anak (`children`) secara vertikal dari atas ke bawah.
* **`Row`:** Menyusun daftar widget anak (`children`) secara horizontal dari kiri ke kanan (digunakan untuk menampilkan 3 `InfoCard` secara sejajar).
* **`InfoCard` (`StatelessWidget`):** Widget kustom untuk menampilkan kartu informasi identitas pemilik portofolio (`NPM`, `Name`, dan `Class`).
* **`Card`:** Menampilkan panel berbingkai dengan sudut membulat dan efek bayangan untuk memisahkan kelompok informasi secara visual.
* **`Container`:** Widget pembungkus serbaguna untuk mengatur dimensi ukuran (`width`), jarak dalam (`padding`), dan tata letak anak di dalamnya.
* **`SizedBox`:** Memberikan jarak kosong berukuran tetap (baik secara vertikal maupun horizontal) di antara dua widget.
* **`Center`:** Memosisikan widget anaknya tepat di tengah-tengah ruang yang tersedia dari induknya.
* **`GridView.count`:** Menampilkan sekumpulan widget dalam tata letak kisi (*grid*) dua dimensi dengan jumlah kolom tetap (`crossAxisCount: 3`).
* **`ItemCard` (`StatelessWidget`):** Widget kustom untuk merepresentasikan setiap kartu tombol aksi menu portofolio.
* **`Material`:** Menyediakan kanvas elemen *Material Design* yang mendukung warna latar (`color`), bentuk sudut membulat (`borderRadius`), serta efek visual sentuhan (*ink splash*).
* **`InkWell`:** Menjadikan area widget anak dapat merespons sentuhan atau klik pengguna (`onTap`) sekaligus menampilkan animasi berupa ripple effect.
* **`SnackBar`:** Menampilkan pesan notifikasi sementara di bagian bawah layar ketika pengguna menekan salah satu tombol `ItemCard`.
* **`Icon`:** Menampilkan ikon grafis vektor bawaan Material Icons (seperti `Icons.folder`, `Icons.add_circle`, dan `Icons.logout`).


3. Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini umumnya digunakan sebagai root widget pada aplikasi Flutter!
**`MaterialApp`** adalah widget pembungkus tingkat atas yang menyediakan berbagai konfigurasi dan layanan inti untuk membangun aplikasi berstandar *Material Design*. Fungsinya meliputi:
* Mengatur tema visual global (`ThemeData` dan `ColorScheme`) yang diwariskan ke seluruh halaman.
* Mengelola sistem navigasi dan perpindahan antarhalaman (*routing* dan `Navigator`).
* Menyediakan dukungan lokalisasi bahasa, arah teks (*text directionality*), serta manajemen `ScaffoldMessenger` untuk menampilkan `SnackBar` atau dialog.

**Alasan digunakan sebagai *root widget*:**
Banyak widget turunan Material di dalam Flutter—seperti `Scaffold`, `AppBar`, `Text`, dan `Theme.of(context)`—membutuhkan konteks lingkungan (*inherited widgets*) seperti informasi arah teks (`Directionality`), tema (`Theme`), dan navigator agar dapat dirender tanpa error. Dengan menempatkan `MaterialApp` sebagai *root widget* di puncak *widget tree*, seluruh widget di bawahnya otomatis mewarisi fondasi konfigurasi dan layanan tersebut secara konsisten.

4. Jelaskan perbedaan antara StatelessWidget dan StatefulWidget! Kapan kita sebaiknya memilih StatelessWidget dan kapan harus menggunakan StatefulWidget?
* **`StatelessWidget`:** Bersifat statis (*immutable*) dan tidak memiliki objek `State` internal, sehingga hanya dirender ulang jika widget induknya (*parent*) dibangun ulang atau mengirimkan parameter baru.
* **`StatefulWidget`:** Bersifat dinamis (*mutable*) dan memiliki objek `State` terpisah yang dapat diperbarui secara mandiri kapan saja menggunakan `setState()` ketika data berubah.

Kita memilih **`StatelessWidget`** untuk tampilan statis yang tidak berubah akibat interaksi internal pengguna (seperti `InfoCard`, `ItemCard`, dan `MyHomePage` pada proyek ini), sedangkan **`StatefulWidget`** digunakan ketika UI perlu berubah secara interaktif atau memuat data dinamis (seperti `TextField`, *checkbox*, *counter*, atau data asinkron dari API).


5. Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di dalam metode build?
**`BuildContext`** adalah objek penunjuk (*handle*) yang merepresentasikan lokasi spesifik sebuah widget di dalam hierarki *widget tree*. Objek ini penting karena memungkinkan sebuah widget menelusuri hierarki ke atas (*ancestor lookup*) untuk mengambil konfigurasi tema, informasi perangkat, maupun layanan aplikasi dari widget induknya.

Di dalam metode `build(BuildContext context)`, objek `context` ini digunakan sebagai parameter pemanggilan berbagai layanan induk, seperti `Theme.of(context)` untuk mengambil warna tema aplikasi pada `AppBar`, `MediaQuery.of(context)` untuk membaca lebar layar perangkat pada `InfoCard`, serta `ScaffoldMessenger.of(context)` untuk memunculkan `SnackBar` saat kartu tombol ditekan.

6. Jelaskan konsep hot reload di Flutter dan apa perbedaannya dengan hot restart! Kapan kita tidak bisa hanya mengandalkan hot reload dan harus melakukan hot restart atau full restart?
* **Hot Reload (`r`):** Menyuntikkan perubahan kode Dart ke *Dart VM* yang sedang berjalan dan membangun ulang (*rebuild*) *widget tree* dalam hitungan detik **tanpa menghilangkan *state* aplikasi** yang sedang aktif.
* **Hot Restart (`R`):** Memuat ulang seluruh kode Dart dan **mengatur ulang seluruh *state* aplikasi** kembali ke kondisi awal (dimulai ulang dari fungsi `main()`), namun tanpa mengompilasi ulang kode *native* dari awal.

Kita perlu melakukan ***Hot Restart*** saat mengubah struktur widget akar (seperti mengubah `StatefulWidget` menjadi `StatelessWidget`), nilai `initState`, atau variabel global. Sementara itu, ***Full Restart*** (menghentikan aplikasi dan menjalankan ulang `flutter run`) wajib dilakukan saat menambah dependensi di `pubspec.yaml`, mendaftarkan aset baru, atau mengubah konfigurasi kode *native* platform (Android/iOS/Web).

## AI Declaration
Saya menggunakan Gemini sebagai alat bantu untuk memahami konsep terkait kode yang telah saya kerjakan.

**AI Tool**: Gemini

**Prompting Strategy**: Prompt yang saya berikan bertujuan untuk memahami konsep dan juga kode yang belum cukup jelas bagi saya.

Contoh penggunaan AI: 
- Menanyakan konsep serta perbedaan antara `Theme.of(context).colorScheme.secondary` dan `item.color` pada widget.

**AI Chatlog**: https://share.gemini.google/OvRfdTfHEKC8



### Tugas 8

## Pertanyaan Reflektif
1. Perbedaan antara Navigator.push(), Navigator.pushReplacement(), dan Navigator.pop(). Metode apa yang digunakan untuk membuka formulir dari kartu aksi? Jelaskan juga bagaimana opsi Home di drawer membawa pengguna kembali ke halaman utama.
**Perbedaan metode navigasi flutter**:
- `Navigator.push()` : Menambahkan halaman baru ke posisi paling atas tumpukan tanpa menghapus halaman sebelumnya.
- `Navigator.pushReplacement()` : Mengganti halaman aktif saat ini dengan halaman baru (halaman lama dihapus dari tumpukan).
- `Navigator.pop()` : Menghapus halaman paling atas dari tumpukan untuk menutupnya.

**Metode untuk membuka formulir dari kartu aksi**:
Untuk membuka formulir saat pengguna menekan kartu aksi, metode yang digunakan adalah `Navigator.push()`. Karena halaman formulir ditumpuk di atas halaman utama tanpa menghapusnya.

**Cara opsi Home di Drawer membawa pengguna ke halaman utama**:
[1] Tutup Drawer: Sistem memanggil `Navigator.pop(context)` untuk menutup panel drawer yang sedang terbuka.
[2] Arahkan ke Halaman Utama: 
    - Jika sudah di halaman utama, proses berhenti sampai disini.
    - Jika dari halaman lain, sistem mengganti halaman saat ini menggunakan `Navigator.pushReplacement()` menuju HomePage agar pengguna tidak menumpuk riwatat navigasi.

2. Bagaimana susunan Scaffold, AppBar, dan Drawer membantu menjaga struktur halaman tetap konsisten? Berikan satu contoh penggunaan warna tema portofolio di lebih dari satu halaman.
- Susunan Scaffold, AppBar, dan Drawer berperan sebagai kerangka tata letak standar Material Design yang memisahkan antara navigasi global dan konten spesifik halaman, sehingga pengalaman pengguna tetap konsisten saat berpindah layar.
    [1] **Scaffold sebagai Kerangka Utama**: Menyediakan slot terstruktur untuk komponen layar (appBar, drawer, body). Dengan membungkus setiap halaman menggunakan Scaffold, posisi elemen-elemen antarmuka serta penanganan area aman otomatis seragam di seluruh halaman.
    [2] **AppBar sebagai Penanda Identitas & Konteks Halaman**: Selalu berada di bagian atas layar dengan gaya tipografi, tinggi, dan ikon navigasi yang seragam. Hal ini memberi pengguna orientasi yang jelas mengenai halaman yang sedang aktif tanpa mengubah pola interaksi.
    [3] **Drawer sebagai Navigasi Terpusat yang Dapat Digunakan Ulang (Reusable Widget)**:
    Dengan memisahkan komponen LeftDrawer ke dalam berkas widget tersendiri dan memasangnya pada properti drawer di setiap halaman, daftar menu navigasi dan logika perpindahan halaman tetap identik di mana pun pengguna berada.

- **Contoh penggunaan warna tema portofolio di lebih dari satu halaman**
[1] Halaman Utama (lib/screens/menu.dart):
   Digunakan untuk mewarnai latar belakang AppBar agar menjadi identitas visual utama aplikasi:
    appBar: AppBar(
        title: const Text('MyPortfolio'),
        backgroundColor: Theme.of(context).colorScheme.primary, 
        foregroundColor: Colors.white,
    ),
[2] Halaman Experience Form (lib/screens/experience_form.dart):
    Digunakan kembali baik pada AppBar maupun tombol aksi utama (Save), sehingga tampilan halaman formulir selaras dengan halaman utama tanpa perlu menulis ulang kode warna secara hardcoded.
    appBar: AppBar(
        title: const Text('Add Experience Form'),
        backgroundColor: Theme.of(context).colorScheme.primary,
        foregroundColor: Colors.white,
    ),
    // ...
    ElevatedButton(
        style: ButtonStyle(
            backgroundColor: WidgetStateProperty.all(
            Theme.of(context).colorScheme.primary,
            ),
        ),
        // ...
    )

3. Mengapa tata letak tersebut dipilih untuk formulir? Jelaskan peran widget pengatur jarak dan widget penggulir ketika ruang layar terbatas.
- Tata letak vertikal berbasis SingleChildScrollView + Column + Padding dipilih karena alur pengisian formulir bersifat linear dari atas ke bawah dan memberi lebar maksimal bagi label maupun pesan validasi.
Saat ruang layar terbatas muncul:
    - **Widget Pengulir (SingleChildScrollView)**: Mencegah error RenderFlex overflow akibat layar terpotong papan ketik, sekaligus memastikan seluruh kolom dan tombol Save tetap dapat digulir dan dijangkau.
    - **Widget Pengatur Jarak (Padding/SizedBox)**:
    Memberi celah konsisten antar-kolom agar kotak masukan, label, dan pesan kesalahan tidak saling tertumpuk, serta menjaga area sentuh tetap nyaman pada layar sempit.

4. Apa peran GlobalKey<FormState>, validator, dan validate() saat tombol Simpan ditekan? Berikan satu contoh nilai yang ditolak oleh validasi dan jelaskan mengapa memilih jenis input atau papan ketik saja belum cukup.
    [1] **GlobalKey<FormState> (_formKey)**: Berfungsi sebagai pengenal unik dan penghubung antara tombol Save dengan state internal widget Form (FormState). Melalui _formKey.currentState, tombol di luar maupun di bagian bawah tree widget dapat mengontrol serta memeriksa status seluruh field di dalam Form secara serentak.
    [2] **validate()**: Method milik FormState yang dipanggil melalui _formKey.currentState!.validate(). Saat dipanggil, Flutter menelusuri setiap field turunan di dalam Form, mengeksekusi fungsi validator masing-masing, lalu mengembalikan true jika semuanya mengembalikan null, atau false jika minimal ada satu field yang tidak valid.
    [3] **validator**: Fungsi pengecekan logika di setiap FormField (seperti TextFormField) yang menerima nilai masukan saat ini. Jika nilai melanggar aturan, validator mengembalikan String pesan kesalahan untuk langsung ditampilkan di bawah field terkait; jika lolos, ia mengembalikan null

    **Contoh nilai yang ditolak oleh validasi**
    - Input berupa string berisi spasi saja (" ") pada kolom Nama Pengalaman atau Nama Organisasi, maupun tanggal selesai (2025-05-01) yang lebih awal daripada tanggal mulai (2026-01-10).

    **Mengapa memilih jenis input atau papan ketik saja belum cukup**:
    - Jenis widget input atau keyboardType (TextInputType.url, TextInputType.number, atau showDatePicker) hanya mengatur tampilan papan ketik dan mekanisme pemilihan dasar, bukan aturan bisnis data. Widget tsb tidak dapat mencegah pengguna mengosongkan kolom wajib, mengisi spasi kosong, atau memasukkan URL dengan format yang salah. Oleh karena itu, validator tetap wajib ada sebagai penjaga aturan domain sebelum data disimpan atau dikirim ke server.

## AI Declaration
Pada pengerjaan tugas ini, Saya menggunakan bantuan Gemini sebagai alat bantu dan asisten untuk memahami konsep terkait kode yang telah saya kerjakan, dengan berdiskusi dan meminta code review untuk memastikan ketepatan kode.

**AI Tool**: Gemini

**Prompting Strategy**: Prompt yang saya berikan bertujuan untuk memahami konsep dan juga kode yang belum cukup jelas bagi saya.

**Contoh penggunaan AI**: 
- *Penentuan Tipe Data State (`DateTime?` vs `int`)*: Berdiskusi mengenai perbedaan `GlobalKey<FormState>` dengan tipe data variabel state untuk kolom `start_at` dan `end_at` pada `ExperienceFormPage`, serta penggunaannya bersama `showDatePicker`.
- Tata Letak & Padding Input Tanggal*: Memastikan cara membungkus `TextFormField` pemicu `showDatePicker` dengan `Padding` agar jarak dan tampilannya seragam dengan kolom masukan lainnya.
- *Code Review `ExperienceFormPage`*: Meminta peninjauan terhadap keseluruhan kode `ExperienceFormPage` terkait validasi input (spasi kosong, format URL, urutan tanggal).

**Analisis kritis keterbatasan AI & Perbaikan manual yang dilakukan**:
- Ketidaksesuaian properti `DropdownButtonFormField`:
Dalam ulasan kodenya, AI menyarankan untuk mengganti `initialValue: _category` menjadi `value: _category`. Namun, ketika saran tersebut diterapkan pada lingkungan Flutter SDK yang saya gunakan, `value` justru memicu peringatan/error. Akhirnya, saya memperbaikinya secara manual dengan mempertahankan `initialValue: _category` yang sesuai standar SDK Flutter yang terpasang.

**AI Chatlog**:
https://share.gemini.google/NH7NZyUSgYhD

### Peningkatan UX & Fitur Tambahan (Bonus)
Selain memenuhi seluruh spesifikasi wajib tugas, saya menambahkan beberapa peningkatan pengalaman pengguna (UX) pada `ExperienceFormPage`:
1. **Tombol Hapus Tanggal Selesai (*Clear End Date*):** Menyediakan tombol ikon `×` (`Icons.clear`) pada kolom **Tanggal Selesai** yang muncul secara dinamis ketika tanggal telah dipilih, sehingga pengguna dapat mengosongkannya kembali dengan mudah apabila pengalaman tersebut masih berlangsung (*ongoing*).
2. **Penghitung Karakter Langsung (`maxLength: 255`):** Menampilkan indikator jumlah karakter secara *real-time* pada kolom **Nama Pengalaman** agar pengguna mengetahui batas maksimal karakter sejak awal mengetik.
