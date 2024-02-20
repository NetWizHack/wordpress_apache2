## Pas 1: Instal·lar Apache2
### Actualitzar el sistema:

```sh
sudo apt update
sudo apt upgrade
```
### Instal·lar Apache2:


```sh
sudo apt install apache2
```
### Habilitar i engegar el servei d'Apache2:

```sh
sudo systemctl enable apache2
sudo systemctl start apache2
```
## Pas 2: Instal·lar MySQL

### Instal·lar MySQL:

```sh
sudo apt install mysql-server
```
### Assegurar MySQL:

```sh
sudo mysql_secure_installation
```
## Crear una base de dades i un usuari per a WordPress:

### Entrar a MySQL:
```sh
sudo mysql -u root -p
```
### Crear la base de dades:
```sql
CREATE DATABASE wordpress_db;
```
### Crear l'usuari i concedir permisos:
```sql
CREATE USER 'wordpress_user'@'localhost' IDENTIFIED BY 'tu_contraseña';
GRANT ALL PRIVILEGES ON wordpress_db.* TO 'wordpress_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
## Pas 3: Instal·lar PHP

Instal·lar PHP i les seves extensions:
```sh
sudo apt install php libapache2-mod-php php-mysql
```
## Pas 4: Instal·lar WordPress

Descarregar l'última versió de WordPress:

```sh
cd /tmp
wget https://es.wordpress.org/latest-es_ES.zip
```  
Extraure l'arxiu:

```sh
sudo apt install unzip
unzip latest-es_ES.zip -d /var/www/html
```
Assignar els permisos correctes:

```sh
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```
## Pas 5: Configurar WordPress
### Crear l'arxiu de configuració de WordPress:

Copiar l'arxiu de configuració:
```sh
cd /var/www/html/wordpress
sudo cp wp-config-sample.php wp-config.php
```
Editar l'arxiu wp-config.php amb les teves dades de base de dades:
```sh
sudo nano wp-config.php
```
Canviar database_name_here, username_here i password_here per les teves dades.

```php
define('DB_NAME', 'wordpress_db');
define('DB_USER', 'wordpress_user');
define('DB_PASSWORD', 'tu_contraseña');
define('DB_HOST', 'localhost');
```
```
http://localhost/wordpress
```
