# 📘 Activity #9 — Autenticación en Apache
Actividad #7

Esta actividad trabaja con **autenticación básica**, control de usuarios, grupos y la directiva `Satisfy`.

---

# 📚 Documentación recomendada

- https://httpd.apache.org/docs/2.4/es/howto/auth.html  
- https://httpd.apache.org/docs/2.0/es/howto/auth.html  

---

# 🧩 1. Crear usuarios para autenticación

Creamos 5 usuarios llamados usuario1…usuario5.

El primer usuario debe crearse sin `-c` (crea archivo nuevo):

```bash
sudo htpasswd -c /etc/apache2/.htpasswd usuario1
```

Los siguientes usuarios:

```bash
sudo htpasswd /etc/apache2/.htpasswd usuario2
sudo htpasswd /etc/apache2/.htpasswd usuario3
sudo htpasswd /etc/apache2/.htpasswd usuario4
sudo htpasswd /etc/apache2/.htpasswd usuario5
```

---

# 🧩 2. Crear grupos

Creamos archivo de grupos:

```bash
sudo nano /etc/apache2/.htgroup
```

Contenido:

```
grupo1: usuario1 usuario2
grupo2: usuario3 usuario4 usuario5
```

---

# 🗂️ 3. Crear directorio privado1 (acceso para todos los usuarios)

```bash
sudo mkdir /var/www/privado1
echo "<h1>Privado 1</h1>" | sudo tee /var/www/privado1/index.html
```

Configurar en el VirtualHost:

```apache
<Directory /var/www/privado1>
    AuthType Basic
    AuthName "Zona privada 1"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

✔️ *Todos los usuarios pueden acceder.*

---

# 🗂️ 4. Crear directorio privado2 (solo grupo1)

```bash
sudo mkdir /var/www/privado2
echo "<h1>Privado 2</h1>" | sudo tee /var/www/privado2/index.html
```

Configuración:

```apache
<Directory /var/www/privado2>
    AuthType Basic
    AuthName "Zona privada 2"
    AuthUserFile /etc/apache2/.htpasswd
    AuthGroupFile /etc/apache2/.htgroup
    Require group grupo1
</Directory>
```

✔️ *Solo usuario1 y usuario2 tienen acceso.*

---

# 🔒 5. Restricción adicional: acceso solo desde localhost

Añadimos control de acceso por IP:

```apache
<Directory /var/www/privado2>
    Require ip 127.0.0.1
    AuthType Basic
    AuthName "Privado 2"
    AuthUserFile /etc/apache2/.htpasswd
    AuthGroupFile /etc/apache2/.htgroup
    Require group grupo1
    Satisfy all
</Directory>
```

---

# 🧠 6. Analizar `Satisfy any` vs `Satisfy all`

### ✔️ `Satisfy all` (por defecto)
El usuario debe cumplir **todas** las condiciones:

- Ser del grupo1 **Y**
- Conectarse desde 127.0.0.1

Si no cumple ambas → ❌ acceso denegado.

---

### ✔️ `Satisfy any`
El usuario debe cumplir **una de las condiciones**:

- Que venga de `localhost` **O**
- Sea del grupo1

Efecto:

- Desde localhost → **entra cualquiera**, aunque no esté autenticado.  
- Desde otro sitio → solo usuarios de grupo1 pueden entrar.

---

# 🔄 Recargar Apache

```bash
sudo systemctl reload apache2
```

---

# ✔️ Activity #9 completada
Incluye usuarios, grupos, control de acceso por IP y uso de `Satisfy`.
