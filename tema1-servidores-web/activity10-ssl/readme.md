# 📘 Activity #10 — SSL y HTTPS en Apache  
Actividad #10 — Cifrado, certificados y Let’s Encrypt

Esta actividad trabaja con **cifrado asimétrico**, certificados SSL autofirmados y la instalación de certificados válidos usando **Let’s Encrypt (Certbot)**.

---

# 🔐 0. Documentación recomendada

### ▶️ Cifrado asimétrico  
http://www.criptored.upm.es/intypedia/video.php?id=criptografia-asimetrica&lang=es

### ▶️ Certificados SSL con OpenSSL  
https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-20-04-es

### ▶️ Instalación de certificados autofirmados  
https://josejuansanchez.org/iaw/practica-01-04/index.html

### ▶️ HTTPS con Let’s Encrypt + Certbot  
https://josejuansanchez.org/iaw/practica-https/index.html

---

# ☁️ Requisitos previos

- Instancia **AWS EC2** con IP pública  
- Puerto **80 (HTTP)** y **443 (HTTPS)** abiertos en el **Security Group**  
- Apache instalado  
- Dominio o subdominio creado en **no-ip.com** apuntando a la IP pública  

---

# 🧩 1. Crear un certificado SSL autofirmado (OpenSSL)

### Habilitar módulo SSL y módulo headers:

```bash
sudo a2enmod ssl
sudo a2enmod headers
sudo systemctl restart apache2
```

---

## 📁 Crear directorio para certificados

```bash
sudo mkdir /etc/apache2/ssl
```

---

## 🔑 Generar clave privada y certificado autofirmado

```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/servidor.key -out /etc/apache2/ssl/servidor.crt
```

Se solicitará:

- Country  
- State  
- City  
- Organization  
- Common Name (poner dominio o IP pública)  

---

# 🏗️ 2. Crear el VirtualHost SSL

Archivo:

```bash
sudo nano /etc/apache2/sites-available/default-ssl.conf
```

Contenido:

```apache
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
    ServerAdmin admin@example.com
    ServerName tu-dominio.com

    DocumentRoot /var/www/html

    SSLEngine on
    SSLCertificateFile /etc/apache2/ssl/servidor.crt
    SSLCertificateKeyFile /etc/apache2/ssl/servidor.key

    <Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride All
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/ssl-error.log
    CustomLog ${APACHE_LOG_DIR}/ssl-access.log combined
</VirtualHost>
</IfModule>
```

---

## ✔️ Activar el sitio SSL

```bash
sudo a2ensite default-ssl.conf
sudo systemctl reload apache2
```

---

### 🔍 Comprobar funcionamiento:

```
https://IP_PUBLICA
```

Debe aparecer un aviso de certificado no confiable (por ser autofirmado), pero funcionar correctamente.

---

# 🧩 3. Configurar dominio dinámico con **no-ip.com**

### Crear una cuenta en no-ip.com

- Crear host: `midominio.ddns.net`  
- Apuntar a la IP pública de AWS  

---

### Instalar cliente no-ip (opcional)

```bash
sudo apt install noip2 -y
sudo noip2 -C
sudo systemctl enable noip2
```

---

# 🧩 4. Instalar **Certbot** (Let’s Encrypt)

```bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y
```

---

# 🔐 5. Emitir un certificado válido para tu dominio

Ejecutar:

```bash
sudo certbot --apache -d midominio.ddns.net
```

Si se desea incluir `www`:

```bash
sudo certbot --apache -d midominio.ddns.net -d www.midominio.ddns.net
```

Certbot configurará:

- Redirección HTTP → HTTPS  
- Nuevo VirtualHost seguro  
- Renovación automática  

---

# 🔄 6. Comprobar renovación automática

Simular renovación:

```bash
sudo certbot renew --dry-run
```

---

# 🌐 7. Comprobar funcionamiento final

Acceder en navegador:

```
https://midominio.ddns.net
```

Debe mostrar un **candado verde** (conexión segura válida).

---

# 📝 8. Elementos a documentar en GitHub

- Pasos de instalación  
- Capturas de AWS EC2: IP pública, security groups  
- Captura del certificado autofirmado  
- Contenido del VirtualHost SSL  
- Certbot ejecutándose  
- Resultado final en navegador  
- Renovación automática  

---

# ✔️ Activity #10 completada

Incluye: certificado autofirmado, SSL configurado, dominio dinámico y certificado Let’s Encrypt válido.
