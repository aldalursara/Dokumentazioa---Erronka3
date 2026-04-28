## 📊 1. Administrazio Grafikoa: Cockpit
Zerbitzaria modu profesionalean eta urrutitik kudeatzeko, **Cockpit** panela instalatu eta konfiguratu da.

* **Sarbidea:** `https://192.168.70.147:9090`
* **Funtzionalitateak:** * Erabiltzaileen kudeaketa grafikoa.
    * Zerbitzuen egoeraren monitorizazioa (systemd).
    * Log-en azterketa eta sareko konexioen kudeaketa.

---

## 💾 2. Biltegiratzea: RAID eta Bolumenak
Datuen segurtasuna bermatzeko, diskoen kudeaketa aurreratua egin da.

* **RAID Konfigurazioa:** `mdadm` tresna erabiliz, RAID unitateak sortu dira datuen erredundantzia ziurtatzeko.
* **LVM (Logical Volume Management):** Partizioak modu dinamikoan kudeatzeko LVM erabili da, bolumenak beharren arabera handitu ahal izateko.
* **Muntatzea:** Unitateak `/mnt/datos_empresa` bidean automatikoki muntatzeko `/etc/fstab` fitxategia konfiguratu da.

---

## 📏 3. Erabiltzaileak eta Kuotak
Erabiltzaile bakoitzak diskoan betetzen duen espazioa mugatzeko sistema aktibatu da.

* **Kuotak:** `quota` eta `quotatool` erabili dira.
* **Muga teknikoak:** Alex bezalako erabiltzaileei muga gogorrak (*hard limits*) ezarri zaizkie.
* **Egiaztapena:** `repquota -as` komandoaren bidez kudeatzen da administrazio osotik.

---

## 📂 4. Zerbitzuak: Samba eta Windows Integrazioa
Windows bezeroak Linux zerbitzarira konektatzeko integrazioa.

* **Samba (SMB):** Karpeta partekatuak konfiguratu dira (`/etc/samba/smb.conf`).
* **Active Directory (AD) Integrazioa:** Zerbitzaria Windows domeinu batera gehitzeko prestatu da, baimen zentralizatuak kudeatzeko.
* **Sarbidea:** Windows-eko fitxategi esploratzailetik: `\\192.168.70.147\Empresa`.

---

## 🖥️ 5. Urrutiko Mahaigaina (RDP)
Konexio egonkorra bermatzeko, mahaigain ingurunea optimizatu da:

1. **XFCE Instalazioa:** GNOME baino arinagoa eta egonkorragoa RDPrako.
2. **Startwm.sh aldaketa:** Erabiltzaile guztiek XFCE saioa automatikoki hasteko:
   ```bash
   # /etc/xrdp/startwm.sh amaieran:
   startxfce4
