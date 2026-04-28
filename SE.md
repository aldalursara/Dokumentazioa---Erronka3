# Erronka OS: Zerbitzarien Administrazio Osoa (Debian 12)

Debian 12 zerbitzariaren inplementazio integrala ingurune mistoan. Dokumentazio honek konfigurazio tekniko guztiak, erabilitako komandoak eta ebatzitako gertakariak jasotzen ditu.

---

## 1. Administrazio Grafikoa: Cockpit
Zerbitzaria modu profesionalean eta urrutitik kudeatzeko panela.

* **Instalazioa:**
    ```bash
    sudo apt update
    sudo apt install cockpit -y
    sudo systemctl enable --now cockpit.socket
    ```
* **Sarbidea:** `https://192.168.70.147:9090` helbidean.
* **Erabilera:** CPU/RAM monitorizazioa, log-ak aztertzea eta erabiltzaileen kudeaketa grafikoa.

---

## 2. Biltegiratzea: RAID eta LVM Konfigurazioa
Datuen segurtasuna eta partizioen kudeaketa dinamikoa bermatzeko.

1.  **RAID 1 sortu (Ispilua):**
    ```bash
    sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
    ```
2.  **LVM bolumenak kudeatu:**
    ```bash
    sudo pvcreate /dev/md0
    sudo vgcreate vg_datos /dev/md0
    sudo lvcreate -L 10G -n lv_empresa vg_datos
    ```
3.  **Fitxategi-sistema eta muntatze automatikoa:**
    ```bash
    sudo mkfs.ext4 /dev/vg_datos/lv_empresa
    sudo mkdir -p /mnt/datos_empresa
    # Gehitu lerro hau /etc/fstab fitxategian:
    /dev/vg_datos/lv_empresa  /mnt/datos_empresa  ext4  defaults  0  2
    ```

---

##  3. Baliabideen Kontrola: Disko Kuotak
Erabiltzaileek diskoan betetzen duten espazioa mugatzeko sistema.

1.  **Instalazioa eta aktibazioa:**
    ```bash
    sudo apt install quota quotatool -y
    # Editatu /etc/fstab eta gehitu: 'usrjquota=aquota.user,jqfmt=vfsv0'
    sudo mount -o remount /mnt/datos_empresa
    sudo quotacheck -cum /mnt/datos_empresa
    sudo quotaon -v /mnt/datos_empresa
    ```
2.  **Muga ezartzea (Adibidez, 'alex' erabiltzaileari):**
    ```bash
    sudo edquota -u alex
    # Aldatu 'soft' (400M) eta 'hard' (500M) zutabeak.
    ```
3.  **Egiaztapena:** `sudo repquota -as`
<img width="753" height="493" alt="Captura de pantalla 2026-04-28 083322" src="https://github.com/user-attachments/assets/be719969-823f-42a2-bd66-fa3afd7bac66" />

---

##  4. Zerbitzuak: Samba eta RDP Integrazioa

### Samba (Fitxategiak Windows-ekin partekatzeko)
1.  **Konfigurazioa (`/etc/samba/smb.conf`):**
    ```ini
    [Empresa]
    path = /mnt/datos_empresa
    valid users = alex
    read only = no
    browseable = yes
    ```
2.  **Samba pasahitza ezarri:** `sudo smbpasswd -a alex`

### Urrutiko Mahaigaina (xrdp + XFCE)
RDP saioak egonkorrak izateko, GNOME ordez XFCE ingurunea konfiguratu da.
1.  **Instalazioa:**
    ```bash
    sudo apt install xfce4 xfce4-goodies xrdp -y
    ```
2.  **XFCE behartu saio guztietan:**
    `/etc/xrdp/startwm.sh` fitxategia editatu eta amaierako lerroak komentatu (#). Ondoren, gehitu:
    ```bash
    startxfce4
    ```
