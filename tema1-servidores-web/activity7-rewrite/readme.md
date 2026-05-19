# 📘 Activity #7 — Reescritura (mod_rewrite)

Esta actividad trabaja con **URL rewriting** mediante el módulo `mod_rewrite` de Apache.  
Se aplican reglas en `.htaccess` o dentro de `<Directory>`.

---

# 📚 Documentación recomendada

- http://httpd.apache.org/docs/current/urlmapping.html  
- http://httpd.apache.org/docs/current/mod/mod_rewrite.html  
- https://www.elarraydejota.com/ejemplos-de-redirecciones-utiles-y-comunes-con-mod_rewrite-para-apache/  
- Ejercicios del módulo rewrite:  
  http://www.josedomingo.org/pledin/2011/10/ejemplos-del-modulo-rewrite-en-apache-2-2/

---

# ⚙️ Habilitar mod_rewrite

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

---

# 🗂️ Configuración recomendada (sin usar .htaccess)

Editar el VirtualHost:

```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

Agregar dentro del `<Directory /var/www/html>`:

```apache
<Directory /var/www/html>
    Options FollowSymLinks
    AllowOverride None
    RewriteEngine On
    RewriteBase /
</Directory>
```

---

# 🧮 Script operacion.php (dado en el enunciado)

```php
<?php
if (isset($_GET['op']) && isset($_GET['op1']) && isset($_GET['op2'])) {
   $op = $_GET["op"];
   $op1 = $_GET["op1"];
   $op2 = $_GET["op2"];
   $r = 0;

   if ($op == "suma")
      $r = $op1 + $op2;
   else if ($op == "resta")
      $r = $op1 - $op2;
   else if ($op == "multiplica")
      $r = $op1 * $op2;
   else if ($op == "divide")
      $r = $op1 / $op2;

   echo "op = " . $op . "<br>";
   echo "op1 = " . $op1 . " ";
   echo "op2 = " . $op2 . " ";
   echo "Resultado  = " . $r;
}
?>
```

---

# 🧪 Reglas de reescritura según los ejercicios

A continuación se listan las reglas típicas del ejercicio del blog de Pledín y otros ejemplos equivalentes.

---

## ✔️ 1. Transformar una URL de la forma:

```
http://localhost/suma/5/3
```

En una llamada PHP:

```
operacion.php?op=suma&op1=5&op2=3
```

Regla:

```apache
RewriteRule ^([a-z]+)/([0-9]+)/([0-9]+)$ operacion.php?op=$1&op1=$2&op2=$3 [L]
```

---

## ✔️ 2. Redirigir URLs sin “www” hacia “www”

```apache
RewriteCond %{HTTP_HOST} !^www\. [NC]
RewriteRule ^(.*)$ http://www.%{HTTP_HOST}/$1 [L,R=301]
```

---

## ✔️ 3. Quitar “www” de la URL (al contrario del ejercicio anterior)

```apache
RewriteCond %{HTTP_HOST} ^www\.(.+)$ [NC]
RewriteRule ^(.*)$ http://%1/$1 [L,R=301]
```

---

## ✔️ 4. Forzar HTTPS

```apache
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [L,R=301]
```

---

## ✔️ 5. Redirigir todos los .php a la versión sin extensión

Ejemplo: `/archivo.php` → `/archivo`

```apache
RewriteRule ^(.+)\.php$ /$1 [R=301,L]
```

---

## ✔️ 6. Crear URL amigable para un artículo

```
/articulo/35
```

Debe llamar a:

```
articulo.php?id=35
```

Regla:

```apache
RewriteRule ^articulo/([0-9]+)$ articulo.php?id=$1 [L]
```

---

# 🔄 Recargar Apache

```bash
sudo systemctl reload apache2
```

---

# ✔️ Activity #7 completada

Incluye todas las reglas necesarias y base para mod_rewrite.
