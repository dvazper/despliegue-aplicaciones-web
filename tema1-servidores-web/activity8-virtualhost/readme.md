# 📘 Activity #8 — VirtualHost (Apache)
Actividad #6

Esta actividad trabaja con **hosting virtual en Apache**, permitiendo que un mismo servidor responda a múltiples dominios o sitios web.

---

# 📚 Documentación recomendada

- https://httpd.apache.org/docs/2.4/es/vhosts/
- https://www.digitalocean.com/community/tutorials/como-configurar-virtual-host-de-apache-en-ubuntu-14-04-lts-es
- http://geekland.eu/integrar-maquina-virtual-en-una-red-local/
- https://httpd.apache.org/docs/2.0/es/vhosts/
- http://linuxconfig.org/configuring-virtual-network-interfaces-in-linux
- https://www.oclc.org/support/services/ezproxy/documentation/technote/2w.en.html

---

# 🏗️ 1. Crear la estructura de directorios

Creamos dos sitios web de ejemplo: **site1** y **site2**.

```bash
sudo mkdir -p /var/www/site1
sudo mkdir -p /var/www/site2
```

Asignamos permisos:

```bash
sudo chown -R $USER:$USER /var/www/site1
sudo chown -R $USER:$USER /var/www/site2
```

Creamos páginas index simples:

```bash
echo "<h1>Bienvenido a Site1</h1>" > /var/www/site1/index.html
echo "<h1>Bienvenido a Site2</h1>" > /var/www/site2/index.html
```

---

# 🌐 2. Crear archivos VirtualHost

Apache guarda los hosts virtuales en:

```
/etc/apache2/sites-available/
```

Creamos el primer VirtualHost:

```bash
sudo nano /etc/apache2/sites-available/site1.conf
```

Contenido:

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@site1.test
    ServerName site1.test
    ServerAlias www.site1.test
    DocumentRoot /var/www/site1
    ErrorLog ${APACHE_LOG_DIR}/site1-error.log
    CustomLog ${APACHE_LOG_DIR}/site1-access.log combined
</VirtualHost>
```

Creamos el segundo VirtualHost:

```bash
sudo nano /etc/apache2/sites-available/site2.conf
```

Contenido:

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@site2.test
    ServerName site2.test
    ServerAlias www.site2.test
    DocumentRoot /var/www/site2
    ErrorLog ${APACHE_LOG_DIR}/site2-error.log
    CustomLog ${APACHE_LOG_DIR}/site2-access.log combined
</VirtualHost>
```

---

# 📌 3. Activar los VirtualHost

```bash
sudo a2ensite site1.conf
sudo a2ensite site2.conf
sudo systemctl reload apache2
```

---

# 🧱 4. Desactivar el VirtualHost por defecto (opcional)

```bash
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
```

---

# 🛠️ 5. Editar el archivo /etc/hosts

Se deben simular los dominios en la máquina local:

```bash
sudo nano /etc/hosts
```

Añadir:

```
127.0.0.1    site1.test
127.0.0.1    site2.test
```

---

# 🌐 6. Probar en el navegador

Abrir:

- http://site1.test  
- http://site2.test  

Cada uno debe mostrar su respectiva página.

---

# 🔥 7. Comprobar conflictos de puertos

Apache solo puede escuchar una vez en el puerto 80.  
Verificar puertos activos:

```bash
sudo ss -tulnp | grep apache
```

---

# 🧩 8. Crear VirtualHosts con IPs diferentes (opcional avanzado)

Si una máquina tiene varias IPs:

```apache
<VirtualHost 192.168.1.50:80>
<VirtualHost 192.168.1.51:80>
```

Ver IPs configuradas:

```bash
ip addr show
```

---

# 📡 9. Añadir una IP virtual en Linux (opcional)

```bash
sudo ip addr add 192.168.1.200/24 dev eth0
```

Persistencia (Ubuntu):

```bash
sudo nano /etc/netplan/*.yaml
```

---

# ✔️ Activity #8 completada

Este README proporciona la configuración completa de **VirtualHosts**, desde sitios básicos hasta escenarios avanzados.
