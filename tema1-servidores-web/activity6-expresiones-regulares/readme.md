# 📘 Activity #6 — Expresiones Regulares  
Actividad #4 — Regex

---

## 📚 Prerrequisitos

Se recomienda leer:

- http://www.rexegg.com/regex-quickstart.html  
- http://www.regexr.com/  
- http://iie.fing.edu.uy/~vagonbar/unixbas/expreg.htm  

Además, realizar los ejercicios de:  
👉 http://regexone.com  

---

# 🧩 Expresiones Regulares Solicitadas

---

## ✔️ Directorios en /www/ cuyo nombre consista en tres dígitos

```regex
^\/www\/(.+\/)?[0-9]{3}
```

---

## ✔️ Ficheros *.gif, *.jpeg, *.jpg, *.png

```regex
.+\.(gif|jpe?g|png)$
```

---

## ✔️ Directiva para redireccionar todos los GIF a JPEG en otro servidor

```apache
RedirectMatch "(.+)\.gif$" "http://other.example.com/$1.jpg"
```

---

## ✔️ Números enteros y decimales

```regex
\d*\.?\d+
```

---

## ✔️ Número de teléfono Americano: 123-123-1234

```regex
\d{3}-?\d{3}-?\d{4}
```

---

## ✔️ Palabras

```regex
[a-zA-Z]+
```

---

## ✔️ Códigos hexadecimales de color (24 o 32 bits)

```regex
(#|0x)?(?:[0-9A-F]{2}){3,4}
```

---

## ✔️ Palabras de 4 letras

```regex
\w{4}
```

---

## ✔️ Número entero sin signo

```regex
\d+
```

---

## ✔️ Número entero con signo

```regex
[-+]?\d+
```

---

## ✔️ Números reales

```regex
[-+]?(([0-9]*\.[0-9]+)|([0-9]+))
```

---

## ✔️ Números reales con exponente

```regex
[-+]?[0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?
```

---

## ✔️ Email

```regex
[a-zA-Z0-9\._%\+\-]+@[a-zA-Z0-9\.\-]+\.[a-zA-Z]{2,}
```

---

## ✔️ Números del 0 al 255

```regex
^([01][0-9][0-9]|2[0-4][0-9]|25[0-5])$
```

---

# ✔️ Activity #6 Completada

