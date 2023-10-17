# Jarkom-Modul-2-A18-2023

- [Jarkom-Modul-2-A18-2023](#jarkom-modul-2-a18-2023)
  - [Anggota](#anggota)
  - [Pembagian Topologi](#pembagian-topologi)
    - [IP node](#ip-node)
  - [Pembahasan Soal](#pembahasan-soal)
    - [Soal 1](#soal-1)
    - [Soal 2](#soal-2)
      - [Yudhistira](#yudhistira)
    - [Soal 3](#soal-3)
      - [Yudhistira](#yudhistira-1)
    - [Soal 4](#soal-4)
      - [Yudhistira](#yudhistira-2)
    - [Soal 5](#soal-5)
      - [Yudhistira](#yudhistira-3)
    - [Soal 6](#soal-6)
      - [Yudhistira](#yudhistira-4)
      - [Werkudara](#werkudara)
    - [Soal 7](#soal-7)
      - [Yudhistira](#yudhistira-5)
      - [Werkudara](#werkudara-1)
    - [Soal 8](#soal-8)
      - [Werkudara](#werkudara-2)
    - [Soal 9](#soal-9)
      - [Arjuna](#arjuna)
      - [Prabukusuma, Abimanyu, Wisanggeni](#prabukusuma-abimanyu-wisanggeni)
    - [Soal 10](#soal-10)
      - [Prabukusuma, Abimanyu, Wisanggeni](#prabukusuma-abimanyu-wisanggeni-1)
      - [Arjuna](#arjuna-1)
    - [Soal 11](#soal-11)
      - [Abimanyu](#abimanyu)
    - [Soal 12](#soal-12)
      - [Abimanyu](#abimanyu-1)
    - [Soal 13](#soal-13)
      - [Abimanyu](#abimanyu-2)
    - [Soal 14](#soal-14)
      - [Abimanyu](#abimanyu-3)
    - [Soal 15](#soal-15)
      - [Abimanyu](#abimanyu-4)
    - [Soal 16](#soal-16)
      - [Abimanyu](#abimanyu-5)
    - [Soal 17](#soal-17)
      - [Abimanyu](#abimanyu-6)
    - [Soal 18](#soal-18)
      - [Abimanyu](#abimanyu-7)
    - [Soal 19](#soal-19)
      - [Abimanyu](#abimanyu-8)
    - [Soal 20](#soal-20)
      - [Abimanyu](#abimanyu-9)

## Anggota

|     | Nama                      | NRP        |
| --- | ------------------------- | ---------- |
| 1   | SATRIA SULTHAN SABILILLAH | 5025201267 |
| 2   | Urdhanaka Aptanagi        | 5025211123 |

## Pembagian Topologi

Topologi 1

![topologi](https://user-images.githubusercontent.com/46347836/275704154-d33ae6b3-33ea-460b-a5c3-431ed6147fcc.png)

### IP node

- Yudhistira: 10.8.1.2
- Nakula: 10.8.1.3
- Prabukusuma: 10.8.2.2
- Abimanyu: 10.8.2.3
- Wisanggeni: 10.8.2.4
- Arjuna: 10.8.2.5
- Werkudara: 10.8.3.2
- Sadewa: 10.8.3.3

## Pembahasan Soal

### Soal 1

Sesuai dengan topologi di atas

### Soal 2

#### Yudhistira

terminal command

```text
apt-get update && apt install bind9
```

/etc/bind/named.conf.local

```text
zone "arjuna.a18.com" {
    type master;
    file "/etc/bind/jarkom/arjuna.a18.com";
};
```

/etc/bind/jarkom/arjuna.a18.com

```bind
;
; BIND data file for local loopback interface
;
$TTL    604800
@   IN  SOA arjuna.a18.com. root.arjuna.a18.com. (
                  2     ; Serial
             604800     ; Refresh
              86400     ; Retry
            2419200     ; Expire
             604800  )  ; Negative Cache TTL
;
@   IN  NS      arjuna.a18.com.
@   IN  A       10.8.2.5
www IN  CNAME   arjuna.a18.com.
```

### Soal 3

#### Yudhistira

/etc/bind/named.conf.local

```text
zone "arjuna.a18.com" {
    type master;
    file "/etc/bind/jarkom/arjuna.a18.com";
};

zone "abimanyu.a18.com" {
    type master;
    file "/etc/bind/jarkom/abimanyu.a18.com";
};
```

/etc/bind/jarkom/abimanyu.a18.com

```text
;
; BIND data file for local loopback interface
;
$TTL    604800
@   IN  SOA abimanyu.a18.com. root.abimanyu.a18.com. (
                  2     ; Serial
             604800     ; Refresh
              86400     ; Retry
            2419200     ; Expire
             604800  )  ; Negative Cache TTL
;
@   IN  NS      abimanyu.a18.com.
@   IN  A       10.8.2.3
www IN  CNAME   abimanyu.a18.com.
```

### Soal 4

#### Yudhistira

/etc/bind/jarkom/abimanyu.a18.com

```bind
;
; BIND data file for local loopback interface
;
$TTL    604800
@   IN  SOA abimanyu.a18.com. root.abimanyu.a18.com. (
                  2     ; Serial
             604800     ; Refresh
              86400     ; Retry
            2419200     ; Expire
             604800  )  ; Negative Cache TTL
;
@           IN  NS      abimanyu.a18.com.
@           IN  A       10.8.2.3
www         IN  CNAME   abimanyu.a18.com.
parikesit   IN  A       10.8.2.3
```

### Soal 5

#### Yudhistira

/etc/bind/named.conf.local

```text
zone "arjuna.a18.com" {
    type master;
    file "/etc/bind/jarkom/arjuna.a18.com";
};

zone "abimanyu.a18.com" {
    type master;
    file "/etc/bind/jarkom/abimanyu.a18.com";
};

zone "2.8.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.8.10.in-addr.arpa";
};
```

/etc/bind/jarkom/2.8.10.in-addr.arpa

```bind
;
; BIND data file for local loopback interface
;
$TTL    604800
@   IN  SOA abimanyu.a18.com.   root.abimanyu.a18.com. (
                  2     ; Serial
             604800     ; Refresh
              86400     ; Retry
            2419200     ; Expire
             604800  )  ; Negative Cache TTL
;
2.8.10.in-addr.arpa IN  NS  abimanyu.a18.com.
3                   IN  PTR abimanyu.a18.com.

```

### Soal 6

#### Yudhistira

/etc/bind/named.conf.local

```text
zone "arjuna.a18.com" {
    type master;
    notify yes;
    also-notify { 10.8.3.2; };
    allow-transfer { 10.8.3.2; };
    file "/etc/bind/jarkom/arjuna.a18.com";
};

zone "abimanyu.a18.com" {
    type master;
    notify yes;
    also-notify { 10.8.3.2; };
    allow-transfer { 10.8.3.2; };
    file "/etc/bind/jarkom/abimanyu.a18.com";
};

zone "3.8.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/3.8.10.in-addr.arpa";
};
```

#### Werkudara

/etc/bind/named.conf.local

```text
zone "arjuna.a18.com" {
    type slave;
    masters { 10.8.1.2; };
    file "/var/lib/bind/arjuna.a18.com";
};

zone "abimanyu.a18.com" {
    type slave;
    masters { 10.8.1.2; };
    file "/var/lib/bind/abimanyu.a18.com";
};
```

### Soal 7

#### Yudhistira

/etc/bind/jarkom/abimanyu.a18.com

```bind
;
; BIND data file for local loopback interface
;
$TTL    604800
@   IN  SOA abimanyu.a18.com. root.abimanyu.a18.com. (
                  2     ; Serial
             604800     ; Refresh
              86400     ; Retry
            2419200     ; Expire
             604800  )  ; Negative Cache TTL
;
@           IN  NS      abimanyu.a18.com.
@           IN  A       10.8.2.3
www         IN  CNAME   abimanyu.a18.com.
parikesit   IN  A       10.8.2.3
ns1         IN  A       10.8.3.2
baratayuda  IN  NS      ns1
```

/etc/bind/named.conf.options

```text
options {
    directory "/var/cache/bind";
    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
};
```

#### Werkudara

/etc/bind/named.conf.options

```text
options {
    directory "/var/cache/bind";
    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
};
```

/etc/bind/named.conf.local

```text
zone "arjuna.a18.com" {
    type slave;
    masters { 10.8.1.2; };
    file "/var/lib/bind/arjuna.a18.com";
};

zone "abimanyu.a18.com" {
    type slave;
    masters { 10.8.1.2; };
    file "/var/lib/bind/abimanyu.a18.com";
};

zone "baratayuda.abimanyu.a18.com" {
    type master;
    file "/etc/bind/baratayuda/baratayuda.abimanyu.a18.com";
};
```

/etc/bind/baratayuda/baratayuda.abimanyu.a18.com

```bind
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     baratayuda.abimanyu.a18.com. root.baratayuda.abimanyu.a18.com. (
                     2023101103         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      baratayuda.abimanyu.a18.com.
@               IN      A       10.6.2.2
www             IN      CNAME   baratayuda.abimanyu.a18.com.
```

### Soal 8

#### Werkudara

/etc/bind/baratayuda/baratayuda.abimanyu.a18.com

```bind
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     baratayuda.abimanyu.a18.com. root.baratayuda.abimanyu.a18.com. (
                     2023101103         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      baratayuda.abimanyu.a18.com.
@               IN      A       10.6.2.2
www             IN      CNAME   baratayuda.abimanyu.a18.com.
rjp             IN      A       10.6.2.2
www.rjp         IN      CNAME   rjp
```

### Soal 9

#### Arjuna

terminal command

```text
apt-get update && apt install nginx
```

#### Prabukusuma, Abimanyu, Wisanggeni

terminal command

```text
apt-get update && apt install nginx wget unzip php php-fpm
```

### Soal 10

#### Prabukusuma, Abimanyu, Wisanggeni

terminal command

```text
wget -O arjunafile “https://drive.google.com/uc?export=download&id=17tAM_XDKYWDvF-JJix1x7txvTBEax7vX && unzip arjunafile && mv arjuna.yyy.com /var/www/arjuna.a18
```

/etc/nginx/sites-available/arjuna.a18

> P.S. Untuk
>
> ```nginx
> listen 8001
> ```
>
> disesuaikan dengan PORT masing-masing node. Untuk konfigurasi kelompok kami adalah
>
> - Prabukusuma:8001
> - Abimanyu:8002
> - Wisanggeni:8003

```nginx
server {
    listen 8001;
    root /var/www/arjuna.a18;
    index index.php index.html index.htm;
    server_name arjuna;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }

    error_log /var/log/nginx/arjuna_error.log;
    access_log /var/log/nginx/arjuna_access.log;
}
```

terminal command

```text
ln -s /etc/nginx/sites-available/arjuna.a18 /etc/nginx/sites-enabled && rm -rf /etc/nginx/sites-enable/default
```

#### Arjuna

/etc/nginx/sites-available/lb-arjuna

```nginx
upstream myweb {
    server 10.8.2.2:8001;
    server 10.8.2.3:8002;
    server 10.8.2.4:8003;
}

server {
    listen 80;
    server_name arjuna;

    location / {
        proxy_pass http://myweb;
    }
}
```

terminal command

```text
ln -s /etc/nginx/sites-available/lb-arjuna /etc/nginx/sites-enabled && rm -rf /etc/nginx/sites-enable/default
```

### Soal 11

#### Abimanyu

terminal command

```text
wget -O abimanyufile “https://drive.google.com/uc?export=download&id=1a4V23hwK9S7hQEDEcv9FL14UkkrHc-Zc” && unzip abimanyufile && mv abimanyu.yyy.com /var/www/abimanyu.a18
```

```text
apt install apache2 php libapache2-mod-php7.0
```

/etc/apache2/sites-available/abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/abimanyu.a18
    ServerName abimanyu.a18.com
    ServerAlias www.abimanyu.a18.com
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

terminal command

```text
a2ensite abimanyu.a18.com && service apache2 reload
```

### Soal 12

#### Abimanyu

/etc/apache2/sites-available/abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/abimanyu.a18
    ServerName abimanyu.a18.com
    ServerAlias www.abimanyu.a18.com

    Alias "/home" "/var/www/abimanyu.a18/index.php/home"

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### Soal 13

#### Abimanyu

terminal command

```text
wget -O parikesitfile “https://drive.google.com/uc?export=download&id=1LdbYntiYVF_NVNgJis1GLCLPEGyIOreS && unzip parikesit && mv parikesit.abimanyu.a18.com /var/www/parikesit.abimanyu.a18
```

/etc/apache2/sites-available/parikesit.abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.a18
        ServerName parikesit.abimanyu.a18.com
        ServerAlias www.parikesit.abimanyu.a18.com

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</Virtualhost>
```

terminal command

```text
a2ensite parikesit.abimanyu.a18.com
```

### Soal 14

#### Abimanyu

terminal command

```text
mkdir /var/www/parikesit.abimanyu.a18/secret
```

/etc/apache2/sites-available/parikesit.abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.a18
        ServerName parikesit.abimanyu.a18.com
        ServerAlias www.parikesit.abimanyu.a18.com

        <Directory /var/www/parikesit.abimanyu.a18/public>
                Options +Indexes
        </Directory>
        <Directory /var/www/parikesit.abimanyu.a18/secret>
                Options -Indexes +FollowSymLinks
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</Virtualhost>
```

### Soal 15

#### Abimanyu

/etc/apache2/sites-available/parikesit.abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.a18
        ServerName parikesit.abimanyu.a18.com
        ServerAlias www.parikesit.abimanyu.a18.com

        <Directory /var/www/parikesit.abimanyu.a18/public>
                Options +Indexes
        </Directory>
        <Directory /var/www/parikesit.abimanyu.a18/secret>
                Options -Indexes +FollowSymLinks
        </Directory>

        ErrorDocument 403 /error/403.html
        ErrorDocument 404 /error/404.html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</Virtualhost>
```

### Soal 16

#### Abimanyu

/etc/apache2/sites-available/parikesit.abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parikesit.abimanyu.a18
        ServerName parikesit.abimanyu.a18.com
        ServerAlias www.parikesit.abimanyu.a18.com

        <Directory /var/www/parikesit.abimanyu.a18/public>
                Options +Indexes
        </Directory>
        <Directory /var/www/parikesit.abimanyu.a18/secret>
                Options -Indexes +FollowSymLinks
        </Directory>

        ErrorDocument 403 /error/403.html
        ErrorDocument 404 /error/404.html

        Alias "/js" "/var/www/parikesit.abimanyu.a18/public/js"

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</Virtualhost>
```

### Soal 17

#### Abimanyu

terminal command

```text
wget -O rjpfile “https://drive.google.com/uc?export=download&id=1pPSP7yIR05JhSFG67RVzgkb-VcW9vQO6” && unzip rjpfile && mv rjp.baratayuda.abimanyu.yyy.com /var/www/rjp.baratayuda.abimanyu.a18
```

/etc/apache2/sites-available/rjp.baratayuda.abimanyu.a18.com.conf

```apache
<VirtualHost *:14000 *:14400>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/rjp.baratayuda.abimanyu.a18.com
    ServerName rjp.baratayuda.abimanyu.a18.com
    ServerAlias www.rjp.baratayuda.abimanyu.a18.com

    <Directory /var/www/rjp.baratayuda.abimanyu.a18>
        Options +Indexes
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

/etc/apache2/ports.conf

```apache
Listen 14000
Listen 14400
Listen 80

<IfModule ssl_module>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

terminal command

```text
a2ensite rjp.baratayuda.abimanyu.a18.com
```

### Soal 18

#### Abimanyu

/etc/apache2/sites-available/rjp.baratayuda.abimanyu.a18.com.conf

```apache
<VirtualHost *:14000 *:14400>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/rjp.baratayuda.abimanyu.a18.com
    ServerName rjp.baratayuda.abimanyu.a18.com
    ServerAlias www.rjp.baratayuda.abimanyu.a18.com

    <Directory /var/www/rjp.baratayuda.abimanyu.a18>
        Options +Indexes
    </Directory>

    <Location />
        AuthType Basic
        AuthName “Restricted Area”
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
    </Location>


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

terminal command

```text
htpasswd -c -B -b /etc/apache2/.htpasswd Wayang baratayudaa18 && a2enmod authn_core auth_basic authn_file && service apache2 restart
```

### Soal 19

#### Abimanyu

/etc/apache/sites-available/abimanyu.a18.com.conf

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/abimanyu.a18
    ServerName abimanyu.a18.com
    ServerAlias www.abimanyu.a18.com

    Alias "/home" "/var/www/abimanyu.a18/index.php/home"

    Redirect permanent /10.8.2.3/ http://www.abimanyu.a18.com

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### Soal 20

#### Abimanyu

/var/www/parikesit.abimanyu.a18/.htaccess

```apacheconf
RewriteCond %{REQUEST_URI} /public/images
RewriteCond %{REQUEST_URI} abimanyu
RewriteRule ^(.*)$ public/images/abimanyu.png [L,R=301]
```
