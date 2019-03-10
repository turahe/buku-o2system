O2System Framework merupakan sebuah php framework generasi masa depan yang dirancang untuk dapat dengan mudah beradaptasi dengan mudah dalam pengembangan aplikasi berskala kecil hingga besar. Oleh karena itu mengetahui dasar-dasar yang terdapat dalam O2System Framework menjadi sangat penting agar kita mengerti apa yang menjadi perbedaan-perbedaan dengan framework php lainnya.

## Berstandar Rekomendasi PHP dari PHP-FIG

Penulisan kode-kode programming php sangatlah beraneka ragam. Hal ini sangat berdampak pada para programmer-programmer php, khususnya ketika harus bekerja dalam satu tim. Sekelompok proyek PHP yang menamakan dirinya PHP Framework Interop Group (PHP-FIG) mulai membangun sebuah kolaborasi melalui standar-standar penulisan kode-kode programming php dan menjadi sebuah standar baru dalam penulisan kode-kode programming php.
O2System PSR adalah salah satu fondasi penting dalam O2System Framework dibuat berdasarkan PHP Standard Recommendations (PSR) yang telah diluncurkan oleh PHP-FIG. Seluruh penulisan kode-kode php dalam O2System Framework dan library-librarynya dibuat sesuai dengan dasar standar koding PSR-1 dan PSR-2. Berikut ini adalah daftar dari PSR yang diterapkan pada O2System Framework:


|Based |Title|
|--|---|
PSR-3|[Logger Interface](http://www.php-fig.org/psr/psr-3/)
PSR-4|[Autoloading Standard](http://www.php-fig.org/psr/psr-4/)
PSR-6|[Caching Interface](http://www.php-fig.org/psr/psr-6/)
PSR-7|[HTTP Message Interface](http://www.php-fig.org/psr/psr-7/)
PSR-11|[Container Interface](http://www.php-fig.org/psr/psr-11/)
PSR-15|[HTTP Server Request Handlers](http://www.php-fig.org/psr/psr-15/)
PSR-16|[Common Interface for Caching Libraries](http://www.php-fig.org/psr/psr-16/)

O2System PSR juga dilengkapi dengan PHP Pattern Classes yang merupakan sekumpulan dari abstract class php yang bertujuan untuk menjadi rancangan standar dari struktur kode-kode pada O2System Framework serta aplikasi yang akan dibuat. Berikut daftar dari PHP Pattern Classes yang ada pada O2System Framework:

- Parent-Child Pattern Class
- Data Storage Pattern Class
- Factory-Prototype Pattern Class
- Handler Pattern Class
- Item Storage Pattern Class
- Object Container Pattern Class
- Object Registry Pattern Class
-  Observer Pattern Class
- Singleton Pattern Class
- Subject Pattern Class
- Variable Storage Pattern Class

## Bergantung Pada Standard PHP Library (SPL)

O2System SPL yang juga menjadi salah satu fondasi penting dari O2System Framework dibuat bergantung kepada Standard PHP Library (SPL) serta dibuat dengan mengimplementasikan interface-interface dari SPL.

Beberapa programmer php mungkin belum pernah mendengar tentang keberadaan Standard PHP Library (SPL). SPL adalah koleksi dari dari interface-interface dan class-class php yang dibuat untuk memecahkan masalah umum . SPL menyediakan seperangkat standar datastructure, satu set iterator untuk melintasi objek, satu set interface, seperangkat standar Exception, sejumlah kelas untuk bekerja dengan file dan menyediakan seperangkat fungsi seperti spl_autoload_register yang dipergunakan oleh Composer dan O2System Framework Autoloader.

SPL mulai diperkenalkan sejak versi php 5.0 diluncurkan dan menjadi paket default dari php sejak saat itu. SPL bukanlah library external ataupun extension external melainkan tersedia dan dikompilasi didalam paket php.

## Dilengkapi dengan Fasilitas Developer

Beberapa kesulitan dari para php programmer adalah ketika harus melakukan proses testing, debugging dan profilling. Namun di O2System Framework sudah terdapat O2System Gear yang menyediakan seperangkat fungsi dan seperangkat library class untuk melakukan unit testing, debugging dan profilling. Berikut ini adalah daftar dari beberapa fitur yang sudah tersedia:

- Browser Debugging Toolbar
- Debugging Class with Helper
- Profiler Class
- Unit Testing Class
- Browser and Command Line Interface (CLI) Print-Out

## Kernel Sebagai Core Framework

Didalam dunia programming komputer, kernel dikenal sebagai inti dari sebuah sistem operasi pada komputer. Kernel adalah program pertama yang dimuat saat start-up yang menangani start-up service-service yang diperlukan oleh sistem serta tempat dimana permintaan input / output (I/O) ke aplikasi diproses untuk pertama kali.

Salah satu perbedaaan O2System Framework dengan php framework lainnya adalah karena memiliki kernel sebagai inti dari sistem frameworknya. Kernel yang dimiliki oleh O2System Framework dimuat saat start-up dan menjalankan secara otomatis service-service yang dibutuhkan oleh framework atau yang dibutuhkan oleh library-library yang dibuat untuk O2System Framework.

Tipe kernel dari O2System Framework bisa dimasukkan dalam kategori Hybrid (atau modular) karena menjalankan beberapa service pada saat start-up. Service-service yang berjalan pada saat start-up tersebut adalah:

- Profiler Service
- Language Service
- Logger Service
- Shutdown Service

## Pola Desain Singleton

Didalam dunia software engineering singleton pattern adalah sebuah rancangan kode program dimana instantiasi kelas dibatasi hanya dalam satu objek. Didalam O2System Framework hanya diperbolehkan satu instance sistem core oleh karena itu desain singleton pattern inilah yang diterapkan.

Fungsi dari instance sistem tersebut adalah untuk mengkoordinasikan seluruh tindakan-tindakan dan service-service yang terjadi di dalam sistem dan aplikasi menjadi satu kesatuan sistem. Hal ini menjadikan sistem dapat beroperasi dengan sangat effisien dalam penggunaan memori yang juga menyediakan status global didalamnya. Instance ini sering disebut juga dengan istilah Super Global Instance.

## Sistem Registry

Dirancang menyerupai sebuah sistem operasi, keberadaan sistem registry menambah satu lagi perbedaan O2System Framework dengan php framework lainnya. Sistem registry pada O2System Framework menyimpan data-data dari sistem modular pada O2System Framework, terutama data mengenai namespace alias dari module-module yang digunakan oleh sistem autoloader untuk memperoleh lokasi directory dari namespace module yang dipanggil.

## Halaman Statis

Secara default O2System Framework telah mendukung halaman-statis, Hal ini menambahkan perbedaan lagi dari O2System Framework dengan php framework lainnya. Istilah untuk halaman-statis pada lingkup O2System Framework disebut dengan istilah Page atau Pages untuk istilah dalam bentuk jamak.