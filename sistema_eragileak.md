---
Almacenamiento y Gestión de Cuotas
---
Enpresa baten biltegiratzea simulatzeko, /mnt/datos_empresan muntatutako disko dedikatu bat konfiguratu da, eta erabiltzaileentzako espazioa murrizteko politikak (kuotak) ezarri dira.
Kuoten konfigurazioa

Disko-kuotak aplikatu ditu erabiltzaile espezifikoek kontsumitu dezaketen gehieneko espazioa mugatzeko (adibidez, Alex erabiltzailea). Horri esker, langile bakar batek ez du zerbitzaria asetzen.

Administratzaile gisa kuoten egoera orokorra egiaztatzeko, honako komando hau erabiliko dugu: 

$\color{green}{\text{sudo repquota -as}}$

<img width="753" height="493" alt="Captura de pantalla 2026-04-28 083322" src="https://github.com/user-attachments/assets/be719969-823f-42a2-bd66-fa3afd7bac66" />

---
Sarean partekatutako karpetak (Samba/SMB)
---

Samba zerbitzua konfiguratu da, Windowseko erabiltzaileak Debian zerbitzarian dauden fitxategietara modu gardenean sar daitezen.

Zerbitzaria fitxategi-arakatzailearen "Sarea" atalean ikus daiteke, ERRONKADEBIAN3 izenarekin, smb:// protokoloa erabiliz.

Windows bezero batetik sartzeko, UNC:\\192.168.70.147 ibilbidea erabiltzen da.

Erabiltzaileak Samban dituen kredentzialen ($\color{green}{\text{smbpasswd}}$) arabera konfiguratu ditu baimen pikortarrak (irakurketa eta idazketa). 

<img width="888" height="542" alt="imagen" src="https://github.com/user-attachments/assets/c089d3ad-19f8-4e32-b967-4e41f9a4f3e2" />
