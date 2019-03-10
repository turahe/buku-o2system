Setiap project yang menggunakan O2System Framework memiliki 5 struktur direktori dasar pada root-nya, yang terdiri dari:

1. Direktori App 
2. Direktori Cache
3. Direktori Public
4. Direktori Storage
5. Direktori Vendor

Masing-masing direktori tersebut memiliki peruntukannya masing-masing.

## Direktori App
Direktori aplikasi berisi semua source-code aplikasi anda yang tersusun rapi sesuai dengan peruntukkannya masing-masing. Secara default, direktori ini berada dalam namespace App dan di-autoload oleh Composer dan O2System Framework autoloader menggunakan standar autoloading PSR-4.

> Hampir seluruh file class-class php pada folder app dapat digenerate menggunakan O2System Console Commands. Untuk mempelajari perintah-perintahnya, jalankan perintah:

```sh
php o2system make --help
```

Seperti yang terlihat pada gambar diatas, struktur pada direktori app memiliki beberapa sub-direktori. Beberapa diantaranya merupakan sub-direktori yang memiliki fungsi penting dan tidak dapat anda gantikan nama sub-direktori tersebut dengan nama lain. Walaupun demikian anda tetap dapat menambahkan sub-direktori baru dengan nama lain sesuai dengan preferensi masing-masing namun harus tetap mematuhi standar penulisan nama direktori PSR-4.

## Direktori Config

Tempat menyimpan semua file-file konfigurasi aplikasi anda. File Config diharuskan ber-format file PHP, yang berisikan variable bertipe array atau bertipe object dari class O2System\Kernel\Datastructures\Config, berlaku untuk turunannya. Penamaan nama variable harus ber-format camelcase dari nama filename Config tersebut, sedangkan untuk penulisan nama filename harus berstandar PSR-4 yaitu dengan format penulisan StudlyCase.

```php
<?php
/**
 * $yourConfig
 *
 * Configuration example.
 *
 * @var array
 */
$yourConfig = [
    'key' => 'value'
];
// ------------------------------------------------------------------------

/**
 * $yourConfig
 *
 * Configuration example.
 *
 * @var \O2System\Kernel\Datastructures\Config
 */
$yourConfig = new \O2System\Kernel\Datastructures\Config([
    'key' => 'value'
]);
```

> Script diatas harus disimpan dengan filename 
`app/Config/YourConfig.php`

## Direktori Controllers/Commanders

Tempat menyimpan semua file-file Controller/Commander class aplikasi anda. File Controller/Commander class diharuskan ber-format file PHP, yang berisikan script PHP class Controller. Penamaan class dan filename harus berstandar PSR-4 yaitu dengan format penulisan StudlyCase dan harus disertai dengan namespace.

```php
<?php
namespace App\Controllers;

use O2System\Framework\Http\Controller;

/**
 * Class HelloWorld
 *
 * HelloWorld controller class example.
 *
 * @package App\Controllers
 */
class HelloWorld extends Controller
{
    /**
     * HelloWorld::index
     *
     * HelloWorld index.
     */
    public function index()
    {
        // write your business-logic here.
    }
}
```

> Script diatas harus disimpan dengan filename `app/Controllers/HelloWorld.php`

## Direktori Helpers 

Tempat menyimpan semua file-file Helper aplikasi anda. File Helper diharuskan ber-format file PHP, yang berisikan script fungsi-fungsi yang anda tulis khusus untuk aplikasi anda. Setiap penulisan fungsi disarankan seperti sample dibawah ini dan harus berstandar PSR-1 dan PSR-2. Sedangkan untuk penulisan nama filename harus berstandar PSR-4 yaitu dengan format penulisan StudlyCase.

```<?php
/**
 * Your Helper Collection
 *
 * Example helper collection.
 */
// ------------------------------------------------------------------------

if ( ! function_exists('my_function')) {
    /**
     * my_function
     *
     * Example helper function.
     *
     * @param array $parameter_1 First parameter of my function.
     *
     * @return mixed
     */
    function my_function(array $parameter_1 = [])
    {
// write your function-logic here.
    }
}

// ------------------------------------------------------------------------
```

> Script diatas harus disimpan dengan nama filename `app/Helpers/YourHelper.php`

## Direktori Languages 

Tempat menyimpan semua file-file Language (bahasa) aplikasi anda. File-file tersebut diharuskan ber-format file INI. Dalam direktori Languages anda dapat mengelompokkan kembali setiap file-file bahasa ke dalam sub-direktori yang diberi nama sesuai dengan standar kode bahasa atau apabila anda merasa tidak perlu mengelompokkannya ke dalam sub-direktori anda dapat menamakan file Language dengan filename yang ditambahkan suffix (akhiran) kode bahasa.

```
;; Example INI Language file en-US
HELLO_WORLD = "Hello World"
```

> Disimpan didalam sub-direktori berdasarkan bahasa
`app/Languages/en-US/nama-file.ini`

> Disimpan dengan tambahan suffix bahasa
`app/Languages/nama-file_en-US.ini`

;; Example INI Language file id-ID
HELLO_WORLD = "Halo Dunia"
Disimpan didalam sub-direktori berdasarkan bahasa
app/Languages/id-ID/nama-file.ini
Disimpan dengan tambahan suffix bahasa
app/Languages/nama-file_id-ID.ini
Hal terpenting pertama dalam penulisan file Language adalah language key parameter harus dituliskan dengan format CAPSLOCK dan menggunakan underscore (_) sebagai pemisah kata. Hal terpenting kedua yaitu language key parameter pada setiap bahasa tidak boleh berubah seperti pada contoh diatas.

> Tips and Trick
Jika anda menuliskan nama filename sama dengan salah satu controller/commander class maka secara otomatis file language tersebut akan diload oleh O2System Framework ketika controller/commander tersebut diakses.

## Direktori Libraries 

Tempat menyimpan semua file-file Library class aplikasi anda. File Library class diharuskan ber-format file PHP yang berisikan script PHP class. Penamaan class dan filename harus berstandar PSR-4 yaitu dengan format penulisan StudlyCase dan harus disertai dengan namespace.

```php
<?php
namespace App\Libraries;

/**
 * Class MyClass
 *
 * Library class example.
 *
 * @package App\Libraries
 */
class MyClass
{
    /**
     * MyClass::__construct
     *
     * MyClass constructor.
     */
    public function __construct()
    {
        // write your logic here
    }
}
```

> Script diatas harus disimpan dengan nama filename `app/Libraries/MyClass.php`

Direktori Models 
Tempat menyimpan semua file-file Model class aplikasi anda. File Model class diharuskan ber-format file PHP yang berisikan script PHP class. Penamaan class dan filename harus berstandar PSR-4 yaitu dengan format penulisan StudlyCase dan harus disertai dengan namespace.

```
<?php
namespace App\Models;

use O2System\Framework\Models\Sql\Model;

/**
 * Class HelloWorld
 *
 * HelloWorld model class example.
 *
 * @package App\Models
 */
class HelloWorld extends Model
{
    /**
     * HelloWorld::$table
     *
     * HelloWorld database table name
     *
     * @var string
     */
    public $table = 'hello_world';
}
```

> Script diatas harus disimpan dengan nama filename `app/Models/HelloWorld.php`

Tips and Trick
Jika anda menuliskan nama filename sama dengan salah satu controller class maka secara otomatis file Model class tersebut akan diload oleh O2System Framework ketika controller tersebut diakses.

## Directory Pages

Tempat menyimpan file-file halaman statis aplikasi anda. File Page harus ber-format file PHTML yang berisikan gabungan HTML, PHP ataupun script yang sesuai dengan parser engine yang digunakan. Penulisan nama filename pada file Page diharuskan berformat StudlyCaps.

## Direktori Views

Tempat menyimpan file-file View aplikasi anda. File View harus ber-format file HTML atau PHTML yang berisikan script gabungan HTML, PHP ataupun script yang sesuai dengan parser engine yang digunakan. Penulisan nama filename pada file View sebaiknya ber-format dash.

## Direktori Cache

Direktori cache berfungsi sebagai tempat penyimpanan dari semua file cache dari template parser yang dikompilasi, sesi berbasis file, registri berbasis file, cache manipulasi gambar, file logging dan cache lainnya yang dihasilkan oleh aplikasi dan framework. Setiap file cache disimpan dalam folder yang dinamai sesuai dengan namanya.

## Direktori Public

Direktori publik berfungsi sebagai root document dari web server anda, di mana semua file yang dapat diakses oleh publik akan ditempatkan di direktori ini seperti file javascript, css, gambar dan asset lainnya. Index.php yang berfungsi sebagai front-controller dari permintaan http aplikasi anda terletak di direktori ini. Asset dan tema yang digunakan oleh aplikasi Anda juga terletak di dalam direktori ini.

## Direktori Storage

Direktori storage berfungsi sebagai tempat penyimpanan raw-files atau file-file yang di-upload dari aplikasi anda.

## Direktori Vendor

Direktori vendor berisi library-library dari Composer Dependencies yang diperlukan oleh project aplikasi anda, termasuk didalamnya library-library dari O2System Framework.