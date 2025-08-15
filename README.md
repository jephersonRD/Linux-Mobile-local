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

## 🚀 Ejemplo rápido
```bash
pkg update -y && pkg upgrade -y
pkg install proot-distro -y
proot-distro install ubuntu
proot-distro login ubuntu
apt update && apt upgrade -y
---

## 3️⃣ Listar distribuciones disponibles
Para ver qué distribuciones puedes instalar:
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

## 6️⃣ Actualizar paquetes dentro de la distribución
Una vez dentro del entorno Linux:
```bash
apt update && apt upgrade -y
```

---

## 7️⃣ Salir de la distribución
```bash
exit
```

---

## 📌 Notas útiles
- **Reinstalar una distribución**:
```bash
proot-distro remove <nombre> && proot-distro install <nombre>
```
- **Solución de errores de claves GPG**:
```bash
apt install ca-certificates -y && apt update
```
- Distribuciones disponibles incluyen: `ubuntu`, `debian`, `fedora`, `archlinux`, entre otras.

---


```

---

> ⚡ Con esto podrás tener un entorno Linux completo dentro de tu Android usando Termux.


# 📚 Índice

## PROOT-DISTRO (🟠 UBUNTU)
```bash
pkg update
pkg install x11-repo
pkg install termux-x11-nightly
pkg install pulseaudio
pkg install proot-distro
```

Luego instala Ubuntu e inicia sesión una vez finalice: 
```bash
proot-distro install ubuntu
proot-distro login ubuntu
```

Actualiza los repositorios e instala cualquier paquete que necesites: 
```bash
apt update 
apt upgrade

apt install sudo nano adduser -y
```

---  
<br>

## ⬇️ Descarga scripts fácilmente: <a name=easy-download-ubuntu-proot></a> 
* startgnome_ubuntu.sh
```bash
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/scripts/proot_ubuntu/startgnome_ubuntu.sh
```
* startxfce4_ubuntu.sh
```bash
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/scripts/proot_ubuntu/startxfce4_ubuntu.sh
```

---  
<br>

# ⚙️ Instalando entornos de escritorio <a name=installing-desktops-ubuntu-proot></a> 

Usé como referencia este [artículo](https://ivonblog.com/en-us/posts/termux-proot-distro-ubuntu/) del blog de Ivon para algunos pasos. 

<br>

<details>
<summary><strong> GNOME </strong></summary>

<br>

> [!NOTE]  
> Todo el proceso está explicado en más detalle en este [video](https://www.youtube.com/watch?v=_vxhzSG2zVQ).

<br>

```bash
# Comandos: 
proot-distro login ubuntu --user droidmaster
```
```bash
sudo apt install dbus-x11 ubuntu-desktop -y
```
Ejecuta este comando después de que termine: 
```bash
for file in $(find /usr -type f -iname "*login1*"); do rm -rf $file
done
```
Desactiva snapd ya que no funciona en Termux:
```bash
cat <<EOF | sudo tee /etc/apt/preferences.d/nosnap.pref
# To prevent repository packages from triggering the installation of Snap,
# this file forbids snapd from being installed by APT.
# For more information: https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html
Package: snapd
Pin: release a=*
Pin-Priority: -10
EOF
```

Instala Firefox: 
```bash
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt-get update
sudo apt-get install firefox-esr
```

Ahora puedes ejecutar Ubuntu con interfaz GNOME usando el script de la sección `Descarga scripts fácilmente`: 
```bash
chmod +x startgnome_ubuntu.sh
./startgnome_ubuntu.sh
```
</details>  

<br>

<details>
<summary><strong> Otros escritorios (XFCE4, Mate, LXDE, etc) </strong></summary>
<br>

Sigue los mismos [pasos de instalación](https://github.com/LinuxDroidMaster/Termux-Desktops/blob/main/Documentation/proot/debian_proot.md#installing-desktops) que para Debian.

</details>  
