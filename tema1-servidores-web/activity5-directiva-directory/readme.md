# 📘 Activity #5 — Directiva Directory (Apache)

## 📂 1. Crear directorios dir1 y dir2

```bash
sudo mkdir /var/www/dir1
sudo mkdir /var/www/dir2
```

---

# 📘 2. Diferencias entre sintaxis antigua y nueva (`Require`)

### Sintaxis antigua (Apache 2.2)

```apache
<Directory /var/www/example1>
    Order Deny,Allow
    Deny from All
    Allow from 192.168.1.100
</Directory>
```

### Sintaxis nueva equivalente (Apache 2.4)

```apache
<Directory /var/www/example1>
    Require ip 192.168.1.100
</Directory>
```

---

### Segundo ejemplo (el orden cambia pero el resultado es igual)

```apache
<Directory /var/www/example1>
    Order Allow,Deny
    Deny from All
    Allow from 192.168.1.100
</Directory>
```

Equivalente:

```apache
<Directory /var/www/example1>
    Require ip 192.168.1.100
</Directory>
```

---

# 📁 3. Configuración para dir1

## ✔️ A) Permitir acceso desde 10.3.0.100

```apache
<Directory /var/www/dir1>
    Require ip 10.3.0.100
</Directory>
```

---

## ✔️ B) Permitir acceso desde marisma.intranet

```apache
<Directory /var/www/dir1>
    Require host marisma.intranet
</Directory>
```

---

## ✔️ C) Permitir acceso desde cualquier subdominio de marisma.intranet

```apache
<Directory /var/www/dir1>
    Require host .marisma.intranet
</Directory>
```

---

## ✔️ D) Permitir acceso desde 10.3.0.0/16 (máscara 255.255.0.0)

```apache
<Directory /var/www/dir1>
    Require ip 10.3.0.0/16
</Directory>
```

---

## ✔️ E) Permitir acceso a marisma.intranet y denegar 10.3.0.101

```apache
<Directory /var/www/dir1>
    Require host marisma.intranet
    Require not ip 10.3.0.101
</Directory>
```

---

# 📁 4. Configuración para dir2

## ✔️ A) Permitir acceso a 10.0.0.0/8

```apache
<Directory /var/www/dir2>
    Require ip 10.0.0.0/8
</Directory>
```

---

## ✔️ B) Permitir 10.0.0.0/8 y denegar marisma.intranet

```apache
<Directory /var/www/dir2>
    Require ip 10.0.0.0/8
    Require not host marisma.intranet
</Directory>
```

---

# 🔄 Recargar Apache

```bash
sudo systemctl reload apache2
```

O reiniciar:

```bash
sudo systemctl restart apache2
```

---

# ✔️ Activity #5 completada
