# 📘 Activity #1 — Puesta en marcha de Apache

## 🔧 1. Arrancar el servicio Apache

```bash
sudo systemctl status apache2
```

Instalar si no está:

```bash
sudo apt update
sudo apt install apache2 -y
```

Iniciar:

```bash
sudo systemctl start apache2
```

Habilitar inicio automático:

```bash
sudo systemctl enable apache2
```

---

## 🔍 2. Comprobar que Apache funciona

```bash
hostname -I
```

Acceder desde navegador:

```
http://localhost
```

o

```
http://TU_IP
```

---

## 🌍 3. Comprobar puertos de escucha

```bash
sudo ss -tulnp | grep apache
```

---

## 📁 4. Directorio raíz

```
/var/www/html/
```

Ver contenido:

```bash
ls -l /var/www/html/
```

Editar index:

```bash
sudo nano /var/www/html/index.html
```

---

## ⚙️ 5. Archivo de configuración principal

```
/etc/apache2/apache2.conf
```

Editar:

```bash
sudo nano /etc/apache2/apache2.conf
```

---

## 🔥 6. Comandos de gestión

```bash
sudo systemctl restart apache2
sudo systemctl reload apache2
sudo systemctl stop apache2
```

---

## 🔒 7. Firewall UFW

```bash
sudo ufw allow 'Apache'
sudo ufw status
```

---

## ✔️ Ejercicio 1 completado
