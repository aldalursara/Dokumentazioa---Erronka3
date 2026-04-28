---
layout: page
title: Markatze lengoaiak
---


# Turismo Analitika: Proiektuaren Egitura eta Garapen Teknikoa

Proiektu honek **turismo-fluxuak aztertzeko plataforma digital bat** aurkezten du. Dokumentazio honek sistemaren arkitektura teknikoa, fitxategien antolaketa eta datuen tratamendua azaltzen ditu.

---

## 1. Arkitektura Teknikoa

Aplikazioa bezeroaren aldeko (*client-side*) arkitektura baten gainean eraiki da, teknologia hauek erabiliz:

* **Datu-egitura (XML):** Informazio guztia formatu hierarkikoan gordetzen da, beste sistema batzuekin interoperabilitatea bermatzeko.
* **Logika Dinamikoa (jQuery & AJAX):** Datuak modu asinkronoan kargatzen dira, webgunea freskatu beharrik gabe erabiltzailearen esperientzia hobetzeko.
* **Bistaratze Grafikoa (Chart.js):** Datu estatistikoak (maximoak, minimoak eta batez bestekoak) modu bisualean interpretatzeko liburutegia.
* **Diseinu Arduratsua (CSS3):** *Flexbox* eta *Sticky* posizionamendua erabili dira interfaze garbi eta moldagarri bat lortzeko.

---

## 2. Fitxategien Egitura eta Eginkizunak

Proiektua modulu hauetan banatuta dago:

### HTML (Egitura)
* **`sarrera.html`**: Hasiera orria. Proiektuaren helburu estrategikoak eta testuingurua aurkezten ditu.
* **`3erronka.html`**: Dashboard nagusia. Hemen kokatzen dira iragazkiak, grafiko interaktiboak eta eguneko datuen fitxak.
* **`txostena.html`**: Open Data atala. Datuak JSON formatuan deskargatzeko gunea.

### CSS (Diseinua)
* **`3erronka.css`**: Estilo fitxategi bateratua. Kolore paleta berdea erabili da jasangarritasunaren irudia indartzeko eta osagaien (kaxak, botoiak, menuak) itxura definitzen du.

### JavaScript (Logika)
* **`3erronka.js`**: Fitxategi nagusia. XML datuen karga (**AJAX**), datuen parseatzea eta grafikoaren eguneraketa kudeatzen ditu.
* **`opendata.js`**: Deskarga sistemaren logika gehigarria kudeatzeko erabilgarria.

### Data (Iturria)
* **`datuak.xml`**: Proiektuaren "datu-basea". Ofizina, data, bisitari kopurua eta jatorria biltzen dituen fitxategi egituratua.

---

## 3. Datuen Fluxua (Data Workflow)

Aplikazioak prozesu hau jarraitzen du datuak erakusteko:

1.  **Eskaera (Request):** Orrialdea kargatzean, JavaScript-ak AJAX eskaera bat egiten du `datuak.xml` fitxategia lortzeko.
2.  **Prozesatzea (Parsing):** XML testua DOM objektu bihurtzen da. Algoritmoak datuak *array*-etan antolatzen ditu (dataren eta herrialdearen arabera).
3.  **Iragaztea (Filtering):** Erabiltzaileak hautatzaileak (*select*) aldatzean, logika honek datu espezifikoak erauzten ditu.
4.  **Eguneratzea (Rendering):** *Chart.js* liburutegiak grafikoa berriz marrazten du eta orrialdeak informazio-fitxa berriak sortzen ditu dinamikoki.

---

## 4. Funtzio Nagusiak

* **Datuen Bistaratzea:** Panel nagusian (`3erronka.html`), erabiltzaileak bisitari kopuruen grafikoak ikus ditzake. Grafiko hauek dinamikoak dira eta aukeratutako iragazkien arabera eguneratzen dira.
* **Iragazki Sistema:** Datuak bi modutara iragazi daitezke:
    * *Egunaren arabera:* Egun zehatz bateko datuak edo denbora-lerro osoa ikusteko.
    * *Jatorriaren arabera:* Herrialde bakoitzeko bulegoaren datu espezifikoak aztertzeko.
* **Open Data eta Deskargak:** Proiektuak gardentasuna sustatzen du. `txostena.html` orrialdean, erabiltzaileak egun bakoitzeko datu gordinak **JSON formatuan** deskarga ditzake.
