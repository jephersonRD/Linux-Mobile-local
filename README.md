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
```
---

## 7️⃣ Salir de la distribución
```bash
exit
```

---

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
