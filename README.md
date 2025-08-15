# 🐧 Instalar `proot-distro` y actualizar paquetes en Termux

## 📌 Requisitos previos
- **Termux** instalado desde [F-Droid](https://f-droid.org/en/packages/com.termux/) (recomendado para evitar problemas de repositorios).
- Conexión a internet estable.

---

## 1️⃣ Actualizar Termux y sus paquetes
Antes de instalar cualquier cosa, actualiza el sistema:
```bash
pkg update -y && pkg upgrade -y
```

---

## 2️⃣ Instalar `proot-distro`
`proot-distro` nos permite instalar distribuciones Linux dentro de Termux:
```bash
pkg install proot-distro -y
```

---

## 3️⃣ Listar distribuciones disponibles
Para ver qué distros puedes instalar:
```bash
proot-distro list
```

---

## 4️⃣ Instalar una distribución (ejemplo: Ubuntu)
```bash
proot-distro install ubuntu
```

---

## 5️⃣ Iniciar la distribución
```bash
proot-distro login ubuntu
```

---

## 6️⃣ Actualizar paquetes dentro de la distro
Ya dentro del entorno Linux:
```bash
apt update && apt upgrade -y
```

---

## 7️⃣ Salir de la distro
```bash
exit
```

---

## 📌 Notas útiles
- **Reinstalar una distro**:
```bash
proot-distro remove <nombre> && proot-distro install <nombre>
```
- **Solución de errores de claves GPG**:
```bash
apt install ca-certificates -y && apt update
```
- Distros disponibles incluyen: `ubuntu`, `debian`, `fedora`, `archlinux`, entre otras.

---

## 🚀 Ejemplo rápido
```bash
pkg update -y && pkg upgrade -y
pkg install proot-distro -y
proot-distro install ubuntu
proot-distro login ubuntu
apt update && apt upgrade -y
```

---

> ⚡ Con esto podrás tener un entorno Linux completo dentro de tu Android usando Termux.
