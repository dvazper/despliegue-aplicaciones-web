# Paso 2 – Instalación de PHP y MySQL

---

## 1. Pasos a seguir (comandos listos para copiar y pegar)

### 1.1 Instalar PHP y módulos necesarios
```bash
sudo apt install php libapache2-mod-php php-mysql
```
![instalación php](capturas/01-instalacion-php.png)

---

### 1.2 Comprobar versión de PHP
```bash
php -v
```
![version php](capturas/02-version-php.png)

---

### 1.3 Instalar MySQL Server
```bash
sudo apt install mysql-server
```
![instalación mysql](capturas/03-instalacion-mysql.png)

---

### 1.4 Comprobar estado de MySQL
```bash
sudo systemctl status mysql
```
![estado mysql](capturas/04-estado-mysql.png)

---

### 1.5 Crear archivo de prueba PHP
```bash
sudo nano /var/www/centro/info.php
```

Contenido:
```php
<?php
phpinfo();
?>
```

![info php](capturas/05-phpinfo.png)

---

### 1.6 Comprobación desde el navegador
Acceder a:
- http://centro.intranet/info.php

![navegador php](capturas/06-navegador-php.png)

---

## 2. Resultado
El servidor Apache queda preparado para ejecutar código PHP y conectarse a bases de datos MySQL, cumpliendo los requisitos para la instalación de WordPress.
