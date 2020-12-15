# Deploy Moodle into ubuntu server

```bash
sudo su
apt-get update
```
## Install Web Server
```bash
apt-get install apache2 -y
```
# Install LAMP (Linux Apache MySQL PHP)
Install Mysql untuk Database
```bash
apt-get install mysql-server -y
```

Menjalankan MySQL Buat user MySQL untuk moodle, dan berikan hak akses. 
```bash
mysql -u root -p

CREATE DATABASE moodle DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'adaptive'@'localhost' IDENTIFIED BY 'network';
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,CREATE TEMPORARY TABLES,DROP,INDEX,ALTER ON moodle.* TO adaptive@localhost;
FLUSH PRIVILEGES;
exit
```
## Install ekstensi dan library php yang dibutuhkan oleh moodle
```bash
apt install php php-common php-pspell php-curl php-gd php-intl php-mysql php-xml php-xmlrpc php-ldap php-zip php-soap php-mbstring libapache2-mod-php -y
```

## Restart web server
```bash 
service apache2 restart
```

# Install Moodle
## Download Moodle
```bash
wget https://download.moodle.org/download.php/direct/stable310/moodle-latest-310.tgz
```
## Pindahkan File
```bash 
mv moodle-latest-310.tgz /var/www/html
```

## Ekstrak File
```bash
cd /var/www/html
tar -xvzf moodle-latest-310.tgz
cd /moodle
mv -r ./* /var/www/html
rm -r moodle
```
## Ganti kepemilikan folder Berikan izin Hak akses dan Buat folder moodledata
```bash
chown -R www-data:www-data /var/www/html/
chmod 755 /var/www/html/
mkdir /var/www/moodledata
chmod 755 /var/www/moodledata/
chown -R www-data:www-data /var/www/moodledata
```
## Akses web instalasi moodle
 http://$IP_Address_ubuntu/moodle
 
## Bagian Cofirm Path
Pastikan data direktori /var/www/moodledata

## Bagian Database Driver
Pilih mysql

## Bagian Database Setting
```bash
Database host : localhost
Masukkan database user : moodleuser
Masukkan password dari moodleuser
```

## Bagian Confirm
Pilih Continue

## Bagian Server Checks
Pastikan module-module yang penting statusnya ok dan terdapat keterangan "Your server environment meets all minimum requirements.”

## Tunggu proses instalasi

## Configure Administrator Account
Isikan konfigurasi akun admin sesuai yang diperlukan saja

## New settings - Front page settings
Beri nama website e-learning moodlenya.

Instalasi Selesai…







