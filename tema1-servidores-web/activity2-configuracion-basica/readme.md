# 📘 Activity #2 — Configuración básica de Apache

## 🔧 2.1 Configuración básica de Apache

---

### 1. Añadir el puerto 81 además del 80

Editar archivo:

```bash
sudo nano /etc/apache2/ports.conf
```

Añadir:

```bash
Listen 81
```

Reiniciar:

```bash
sudo systemctl restart apache2
```

Comprobar:

```bash
sudo ss -tulnp | grep apache
```

---

### 2. Añadir dominio marisma.intranet

```bash
sudo nano /etc/hosts
```

```txt
127.0.0.1   marisma.intranet
```

---

### 3. Cambiar ServerTokens

```bash
sudo nano /etc/apache2/conf-available/security.conf
```

```apache
ServerTokens ProductOnly
```

---

### 4. Cambiar ServerSignature

```apache
ServerSignature Off
```

```bash
sudo systemctl reload apache2
```

---

### 5. Crear directorios

```bash
sudo mkdir /var/www/prueba
sudo mkdir /var/www/prueba2
```

```bash
echo "<h1>Prueba 1</h1>" | sudo tee /var/www/prueba/index.html
echo "<h1>Prueba 2</h1>" | sudo tee /var/www/prueba2/index.html
```

---

### 6. Redirigir carpeta

```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

```apache
Redirect /prueba /prueba2
```

---

### 7. Redirigir una sola página

```apache
Redirect /prueba/pagina.html /prueba2/pagina2.html
```

---

### 8. Usar UserDir

```bash
sudo a2enmod userdir
sudo systemctl restart apache2
```

```bash
mkdir ~/public_html
echo "<h1>Página UserDir</h1>" > ~/public_html/index.html
```

---

### 9. Usar Alias

```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

```apache
Alias /docs /home/usuario/public_html
```

---

### 10. Desactivar indexación

```apache
<Directory /var/www/>
    Options -Indexes
</Directory>
```

```bash
sudo systemctl restart apache2
```

---

# 🐚 Activity 2.2 — Scripts Bash

---

## Script 1 — add_port.sh

```bash
#!/bin/bash

if [ "$#" -ne 1 ]; then
    echo "Error: debe especificar el puerto."
    echo "Uso: $0 <puerto>"
    exit 1
fi

PUERTO=$1
ARCHIVO="/etc/apache2/ports.conf"

grep -q "Listen $PUERTO" $ARCHIVO

if [ $? -eq 0 ]; then
    echo "El puerto $PUERTO ya existe."
else
    echo "Añadiendo puerto $PUERTO..."
    sudo cp $ARCHIVO $ARCHIVO.bak
    echo "Listen $PUERTO" | sudo tee -a $ARCHIVO
    sudo systemctl restart apache2
    echo "Puerto añadido y Apache reiniciado."
fi
```

---

## Script 2 — add_domain.sh

```bash
#!/bin/bash

if [ "$#" -ne 2 ]; then
    echo "Error: parámetros insuficientes."
    echo "Uso: $0 <ip> <dominio>"
    exit 1
fi

IP=$1
DOM=$2
ARCHIVO="/etc/hosts"

grep -q "$DOM" $ARCHIVO

if [ $? -eq 0 ]; then
    echo "El dominio '$DOM' ya existe."
else
    echo "$IP $DOM" | sudo tee -a $ARCHIVO
    echo "Dominio añadido."
fi
```

---

## Script 3 — create_page.sh

```bash
#!/bin/bash

if [ "$#" -ne 3 ]; then
    echo "Error: parámetros incorrectos."
    echo "Uso: $0 <archivo> <titulo> <mensaje>"
    exit 1
fi

ARCHIVO=$1
TITULO=$2
MENSAJE=$3

cat <<EOF | sudo tee $ARCHIVO
<html>
<head>
<title>$TITULO</title>
</head>
<body>
<h1>$TITULO</h1>
<p>$MENSAJE</p>
</body>
</html>
EOF

echo "Página creada correctamente."
```

