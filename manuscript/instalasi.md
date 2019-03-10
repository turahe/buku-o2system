## Kebutuhan Server

Untuk mulai bekerja dengan O2System Framework anda harus memastikan server anda telah memenuhi persyaratan minimum berikut:

### HTTP Server
- Apache
    - Module Rewrite (mod_rewrite)
    - Module Header (mod_header)
- NGINX
    - PHP FPM
- Microsoft IIS
    - PHP Fast-CGI
    - Rewrite Rule

Supported PHP Versions

PHP v5.6.0+ (Nearly Deprecated)
PHP v7.1+ (Strongly Recommended - Why v7.1?)

> Untuk performa lebih baik, disarankan menggunakan PHP v7.1+

### PHP Extensions
- Fileinfo
- Mcrypt
- OpenSSL
- Mbstring
- Tokenizer
- XML
- APCu & Zend OPCache

## Membuat Project

O2System Framework telah menggunakan Composer sebagai Dependency Management, jadi langkah termudah untuk melakukan instalasi adalah dengan menggunakan perintah `composer create-project` pada terminal:

```
composer create-project o2system/o2system [project-name]
```

Perizinan Direktori
Setelah selesai melakukan instalasi O2System Framework anda wajib memastikan bahwa direktori cache dan storage dapat ditulis oleh aplikasi anda.

Mengubah permission pada direktori cache

```sh
$ chmod -R 777 /path/to/your/project/cache
```

Mengubah permission pada direktori storage

```sh
$ chmod -R 777 /path/to/your/project/storage
```

## Konfigurasi server

### Apache
Bagi anda yang menggunakan apache sebagai web-server anda, buatlah file .htaccess pada direktori root dokumen aplikasi anda lalu isikan dengan kode htaccess seperti contoh dibawah ini.

```
<IfModule mod_rewrite.c>
<IfModule mod_negotiation.c>
Options -MultiViews
</IfModule>

Options +FollowSymlinks -Indexes
RewriteEngine On

# If you installed O2System in a subfolder, you will need to
# change the following line to match the subfolder you need.
# http://httpd.apache.org/docs/current/mod/mod_rewrite.html#rewritebase
# RewriteBase /

# Rewrite "www.example.com -> example.com"
RewriteCond %{HTTPS} !=on
RewriteCond %{HTTP_HOST} ^www\.(.+)$ [NC]
RewriteRule ^ http://%1%{REQUEST_URI} [R=301,L]

# Handle Front Controller...
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [QSA,L]

# Handle Authorization Header
RewriteCond %{HTTP:Authorization} .
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
</IfModule>
```

### NGINX

Bagi anda yang menggunakan NGINX sebagai web-server, buatlah vhost untuk proyek aplikasi anda lalu isi file vhost tersebut dengan konfigurasi seperti contoh di bawah ini.

```
server {
        listen *:80;
        server_name example.com *.example.com;

        root  /path/to/your/project/public;
        index  index.html index.htm index.php;

        charset utf-8;

        location / {
                try_files $uri $uri/ /index.php$is_args$args;
        }

        location = /favicon.ico { access_log off; log_not_found off; }
        location = /robots.txt  { access_log off; log_not_found off; }

        access_log off;
        error_log  /path/to/your/nginx/logs/example.com.error.log;

        location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                
                # fastcgi_pass unix:/var/run/php-fpm.sock;
                fastcgi_pass 127.0.0.1:9000;
                
                fastcgi_index index.php;
                include fastcgi_params;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                fastcgi_intercept_errors off;
                fastcgi_buffer_size 16k;
                fastcgi_buffers 4 16k;

                include fastcgi_params;
        }

        location ~ /\.ht {
                deny all;
        }
}
```

Microsoft IIS
Setelah anda memastikan IIS anda sudah memiliki plugin Rewrite Rule, buatlah file web.config di root direktori project anda dan isikan seperti contoh dibawah ini.

```
<configuration>
        <system.webServer>
                <rewrite>
                        <rules>
                                <clear />
                                <rule name="REQUEST_URI" stopProcessing="true">
                                        <match url="^" ignoreCase="false" />
                                        <conditions logicalGrouping="MatchAll" trackAllCaptures="false">
                                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" ignoreCase="false" negate="true" />
                                        <add input="{REQUEST_FILENAME}" matchType="IsFile" ignoreCase="false" negate="true" />
                                        </conditions>
                                        <action type="Rewrite" url="index.php" />
                                </rule>
                        </rules>
                </rewrite>
        </system.webServer>
</configuration>
```