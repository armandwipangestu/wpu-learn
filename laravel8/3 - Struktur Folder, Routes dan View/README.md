## Daftar Isi

- [Sturktur Direktori atau Folder](#struktur-direktori-atau-folder)
- [Root Direktori](#root-direktori)
  - [App Direktori](#app-direktori)
  - [Bootstrap Direktori](#bootstrap-direktori)
  - [Config Direktori](#config-direktori)
  - [Database Direktori](#database-direktori)
  - [Public Direktori](#public-direktori)
  - [Resources Direktori](#resources-direktori)
  - [Routes Direktori](#routes-direktori)
  - [Storage Direktori](#storage-direktori)
  - [Tests Direktori](#tests-direktori)
  - [Vendor Direktori](#vendor-direktori)
- [App Direktori Main](#app-direktori-main)
  - [Broadcasting Direktori](#broadcasting-direktori)
  - [Console Direktori](#console-direktori)
  - [Events Direktori](#events-direktori)
  - [Exceptions Direktori](#exceptions-direktori)
  - [Http Direktori](#http-direktori)
  - [Jobs Direktori](#jobs-direktori)
  - [Listeners Direktori](#listeners-direktori)
  - [Mail Direktori](#mail-direktori)
  - [Models Direktori](#models-direktori)
  - [Notifications Direktori](#notifications-direktori)
  - [Policies Direktori](#policies-direktori)
  - [Providers Direktori](#providers-direktori)
  - [Rules Direktori](#rules-direktori)
- [Lokasi Folder atau File MVC dan Yang Perlu Di ingat pada Aplikasi Laravel](#lokasi-folder-atau-file-mvc-dan-yang-perlu-di-ingat-pada-aplikasi-laravel)

> **Catatan**:
>
> Kalian jangan khawatir dengan banyak nya folder di aplikasi Laravel, karena jika Anda baru pertama kali belajar, kita hanya akan memodifikasi di beberapa folder dan file saja (tidak perlu dibuka semua folder dan file).

## Struktur Direktori atau Folder

Struktur aplikasi Laravel default dimaksudkan untuk memberikan titik awal yang baik untuk aplikasi besar dan kecil. Namun Anda bebas mengatur aplikasi sesuka Anda. Laravel hampir tidak menerapkan batasan di mana class tertentu berada - selama composer dapat memuat class secara otomatis.

## Root Direktori

### App Direktori

Direktori `app` berisi kode inti aplikasi Anda. Kami akan segera menjelajahi direktori ini secara lebih rinci; namun, hampir semua class dalam aplikasi Anda akan berada di direktori ini.

### Bootstrap Direktori

Direktori `bootstrap` berisi file `app.php` yang mem-bootstrap framework. Direktori ini juga menampung direktori cache yang berisi file yang dihasilkan framework untuk optimalisasi kinerja seperti route dan service cache files. Biasanya Anda tidak perlu mengubah file apapun pada direktori ini.

### Config Direktori

Direktori `config` sesuai dengan namanya, berisi semua file konfigurasi aplikasi Anda. Merupakan ide bagus untuk membaca semua file ini dan membiasakan diri dengan semua opsi yang tersedia untuk Anda.

### Database Direktori

Direktori `database` berisi database migration Anda, model factories (pabrik model) dan seeds. Jika mau, Anda juga dapat menggunakan direktori ini untuk menyimpan database SQLite.

### Public Direktori

Direktori `public` berisi file `index.php` yang merupakan titik masuk untuk semua permintaan yang masuk ke aplikasi Anda dan mengonfigurasi autoloading (pemuatan otomatis). Direktori ini juga menampung aset Anda seperti gambar, javascript dan css.

### Resources Direktori

Direktori `resources` berisi views anda serta asset mentah yang belum di compile seperti CSS atau javascript. Direktori ini juga menampung semua file bahasa Anda.

### Routes Direktori

Direktori `routes` berisi semua definisi route untuk aplikasi Anda. Secara default, beberapa file route disertakan dengan Laravel: `web.php`, `api.php`, `console.php`, dan `channels.php`.

File `web.php` berisi route yang ditempatkan `RouteServiceProvider` di grup middleware web, yang menyediakan keadaan session, perlindungan CSRF, dan enkripsi cookie. Jika aplikasi Anda tidak menawarkan API RESTful dan tanpa keadaan (stateless), kemungkinan besar semua route Anda akan ditentukan di file `web.php`.

File `api.php` berisi route yang ditempatkan `RouteServiceProvider` di grup api middleware. Route-route ini dimaksudkan untuk menjadi tanpa keadaan (stateless), jadi permintaan yang masuk ke aplikasi melalui route-route ini dimaksudkan untuk diautentikasi melalui token dan tidak akan memiliki akses ke keadaan session (session state).

File `console.php` adalah tempat Anda dapat menentukan semua perintah console berbasis penutupan (closure based console commands). Setiap penutupan terikat pada instance perintah yang memungkinkan pendekatan sederhana untuk berinteraksi dengan metode IO setiap perintah. Meskipun file ini tidak menentukan route HTTP, file ini mendefinisikan titik masuk (route) berbasis console ke dalam aplikasi Anda.

File `channels.php` adalah tempat Anda dapat mendaftarkan semua saluran penyiaran acara (broadcasting channels) yang didukung aplikasi Anda.

### Storage Direktori

Direktori `storage` berisi log Anda, tempat template blade yang dikompilasi, session berbasis file (file based sessions), cache file, dan file lain yang dihasilkan oleh framework. Direktori ini dipisahkan menjadi direktori `app`, `framework`, dan `logs`. Direktori `app` dapat digunakan untuk menyimpan file apapun yang dihasilkan oleh aplikasi Anda. Direktori `framework` digunakan untuk menyimpan file dan cache yang dihasilkan framework. Terakhir, direktori `logs` berisi file log aplikasi Anda.

Direktori `storage/app/public` dapat digunakan untuk menyimpan file buatan pengguna, seperti avatar profile, yang harus dapat diakses secara publik. Anda harus membuat tautan simbolik (symbolic link) di `public/storage` yang menunjuk ke direktori ini. Anda dapat membuat tautan menggunakan perintah Artisan `php artisan storage:link`

### Tests Direktori

Direktori `tests` berisi test otomatis Anda. Contoh pengujian PHPUnit dan pengujian fitur disediakan secara langsung. Setiap class test harus diakhiri dengan kata `Test`. Anda dapat menjalankan pengujian menggunakan perintah `phpunit` atau `php verndor/bin/phpunit`. Atau, jika Anda menginginkan representasi hasil pengujian yang lebih detail dan indah, Anda dapat menjalankan pengujian menggunakan perintah Artisan `php artisan test`.

### Vendor Direktori

Direktori `vendor` berisi dependency package composer Anda.

## App Direktori Main

Mayoritas aplikasi Anda ditempatkan di direktori `app`. Secara default, direktori ini dibawah namespaced `App` dan dimuat secara otomatis oleh composer menggunakan standar pemuatan otomatis PSR-4 (PSR-4 autoloading standard).

Direktori `app` berisi berbagai direktori tambahan seperti `Console`, `Http`, dan `Providers`. Bayangkan direktori `Console` dan `Http` menyediakan API ke dalam inti aplikasi Anda. Protokol HTTP dan CLI keduanya merupakan mekanisme untuk berinterkasi dengan aplikasi Anda, namun sebenarnya tidak berisi logika aplikasi. Dengan kata lain, ini adalah dua cara mengeluarkan perintah ke aplikasi Anda. Direktori `Console` berisi semua perintah Artisan Anda, sedangkan direktori `Http` berisi Controllers, middleware, dan requests.

Berbagai direktori lain akan dihasilkan di dalam direktori `app` saat Anda menggunakan perintah Artisan `make` untuk menghasilkan class. Jadi, misalnya, direktori `app/Jobs` tidak akan ada sampai Anda menjalankan perintah Artisan `make:job` untuk menghasilkan Job Class.

> **Catatan**:
>
> Banyak class di direktori `app` dapat dihasilkan oleh perintah Artisan. Untuk meninjau perintah yang tersedia, jalankan perintah `php artisan list make` di terminal Anda.

### Broadcasting Direktori

Direktori `Broadcasting` berisi semua class broadcast channel untuk aplikasi Anda. Class-class ini dihasilkan menggunakan perintah `make:channel`. Direktori ini tidak ada secara default, tetapi akan dibuat untuk Anda saat Anda membuat saluran atau channel pertama. Untuk mempelajari tentang saluran atau channel, lihat dokumentasi di event broadcasting.

### Console Direktori

Direktori `Console` berisi semua perintah Artisan khusus atau custom Artisan untuk aplikasi Anda. Perintah-perintah ini dapat dihasilkan menggunakan perintah `make:command`. Direktori ini juga menampung kernel console Anda, yang merupakan tempat perintah Artisan khusus Anda didaftarkan dan tugas terjadwal Anda ditentukan.

### Events Direktori

Direktori `Events` ini tidak ada secara default, tetapi akan dibuat untuk Anda dengan perintah Artisan `event:generate` dan `make:event`. Direktori `Events` menampung Class Event. Event dapat digunakan untuk mengingatkan bagian lain aplikasi Anda bahwa tindakan tertentu telah terjadi, sehingga memberikan banyak fleksibilitas dan pemisahan.

### Exceptions Direktori

Direktori `Exceptions` berisi pengendali pengecualian aplikasi Anda dan juga merupakan tempat yang baik untuk menempatkan pengecualian apapaun yang diberikan oleh aplikasi Anda. Jika Anda ingin menyesuaikan cara pengecualian dicatat atau dirender, Anda harus memodifikasi Class `Handler` di direktori ini.

### Http Direktori

Direktori `Http` berisi pengontrol, middleware dan permintaan formulir (form request) Anda. Hampur semua logika untuk menangani permintaan yang masuk ke aplikasi Anda akan ditempatkan di direktori ini.

### Jobs Direktori

Direktori `Jobs` ini tidak ada secara default, namun akan dibuat untuk Anda jika Anda menjalankan perintah Artisan `make:job`. Direktori `Jobs` menampung pekerjaan yang dapat diantrekan untuk aplikasi Anda (queueable jobs for your application). Jobs mungkin dimasukkan ke dalam antrean oleh aplikasi Anda atau dijalankan secara sinkron dalam siklus hidup permintaan saat ini. Jobs yang dijalankan secara sinkron selama permintaan saat ini terkadang disebut sebagai "perintah" atau "commands" karena merupakan implementasi dari pola perintah (implementation of the command pattern).

### Listeners Direktori

Direktori `Listeners` ini tidak ada secara default, namun akan dibuat untuk Anda jika Anda menjalankan perintah Artisan `event:generate` atau `make:listener`. Direktori `Listeners` berisi Class-Class yang menangani Event Anda. Pemroses event menerima instance Event dan menjalankan logika setiap respons terhadap Event yang diaktifkan. Misalnya, Event `UserRegistered` mungkin ditangani oleh listener `SendWelcomeEmail`.

### Mail Direktori

Direktori `Mail` ini tidak ada secara default, namun akan dibuat untuk Anda jika Anda menjalankan perintah Artisan `make:mail`. Direktori `Mail` berisi semua Class Anda yang mewakili email yang dikirim oleh aplikasi Anda. Objek email memungkinkan Anda merangkum semua logika pembuatan email dalam satu Class sederhana yang dapat dikirim menggunakan metode `Mail::send`.

### Models Direktori

Direktori `Models` ini berisi semua Class model Eloquent Anda. ORM Eloquent yang disertakan dengan Laravel menyediakan implementasi `ActiveRecord` yang indah dan sederhana untuk bekerja dengan database Anda. Setiap tabel database memiliki "Model" terkait yang digunakan untuk berinteraksi dengan tabel tersebut. Model memungkinkan Anda membuat query data dalam tabel Anda, serta menyisipkan catatan baru ke dalam tabel.

### Notifications Direktori

Direktori `Notifications` ini tidak ada secara default, tetapi akan dibuat untuk Anda jika Anda menjalankan perintah Artisan `make:notification`. Direktori `Notifications` berisi semua notifikasi "transaksional" yang dikirimkan oleh aplikasi Anda, seperti notifikasi sederhana tentang Event yang terjadi dalam aplikasi Anda. Fitur notifikasi Laravel mengabstraksi pengiriman notifkasi melalui berbagai driver seperti email, Slack, SMS, atau disimpan dalam database.

### Policies Direktori

Direktori `Policies` ini tidak ada secara default, namun akan dibuat untuk Anda jika Anda menjalankan perintah Artisan `make:policy`. Direktori `Policies` berisi Class kebijakan otorisasi (authorization policy) untuk aplikasi Anda. Kebijkan atau Policies digunakan untuk menentukan apakah pengguna dapat melakukan tindakan tertentu terhadap sumber daya (resource).

### Providers Direktori

Direktori `Providers` ini berisi semua providers atau penyedia layanan untuk aplikasi Anda. Penyedia layanan (Service providers) mem-bootstrap aplikasi Anda dengan mengikat layanan (binding services) dalam wadah layanan, mendaftarkan event atau peristiwa, atau melakukan tugas lain apapun untuk mempersiapkan aplikasi Anda menghadapi permintaan masuk.

Dalam aplikasi Laravel yang baru, direktori ini sudah berisi beberapa provider atau penyedia. Anda bebas menambahkan provider atau penyedia Anda sendiri ke direktori ini sesuai dengan kebutuhan Anda.

### Rules Direktori

Direktori `Rules` ini tidak ada secara default, tetapi akan dibuat untuk Anda jika Anda menjalankan perintah Artisan `make:rule`. Direktori `Rules` berisi objek aturan validasi khusus untuk aplikasi Anda. Aturan digunakan untuk merangkum logika validasi yang rumit dalam objek sederhana. Untuk informasi lebih lanjut, lihat dokumentasi validasi.

## Lokasi Folder atau File MVC dan Yang Perlu Di ingat pada Aplikasi Laravel

| Nama                   | PATH atau Lokasi          | Penjelasan                                                                                                       |
| ---------------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Model                  | `app/Models`              | Semua yang berhubungan dengan Model                                                                              |
| View                   | `resources/views`         | Semua yang berhubungan dengan View                                                                               |
| Controller             | `app/Http/Controllers`    | Semua yang berhubungan dengan Controller                                                                         |
| Routes                 | `app/routes`              | Semua yang berhubungan dengan route                                                                              |
| Assets Statis          | `public`                  | Semua yang berhubungan dengan asset statis (css, javascript, gambar)                                             |
| Assets Sistem Bundling | `resources/{css,js,lang}` | Semua yang berhubungan dengan asset saat menggunakan sistem bundling                                             |
| Environment File       | `.env`                    | Semua yang berhubungan dengan environment aplikasi Laravel, seperti informasi Database, app url atau baseurl dsb |
