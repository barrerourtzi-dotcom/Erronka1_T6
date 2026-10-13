# Supermerkatuko Datu Estrategia eta Arkitektura

Dokumentu honek supermerkatu katearen kudeaketa operatiborako datuen egitura, bi datu-basetan (MySQL eta MongoDB) oinarritutako arkitektura eta segurtasun neurriak zehazten ditu.

## 1. Datu Motak eta Sailkapena

Supermerkatuan sortzen den informazioa bere egitura mailaren eta eremu funtzionalaren arabera sailkatzen da:

### a) Datu Egituratuak (Guztizkoaren %80a)

Errenkada eta zutabeko taula formatuan guztiz antolatuta dagoen informazioa. Eguneroko kudeaketa operatibo zein transakzioetarako erabiltzen da.

- **Inbentarioa eta Produktuak:** EAN/barra kodeak, artikuluen izenak, kategoriak, salmenta prezioak, dendako kokapenak eta stock mailak.
- **Salmentak eta Salmenta Puntutako Terminalak (POS/TPV):** Txartelen erregistroak, salmenta ordua, esleitutako kutxa, ordainketa modua eta zenbateko osoa.
- **Langileak eta Hornitzaileak:** Identifikazio datuak, lan txandak, soldatak, hornitzaileen kontaktua eta bete gabeko eskaerak.

### b) Datu Egituragabeak (Guztizkoaren %20a)

Malgutasuna behar duen eta taula egitura zurrunik ez duen informazioa.

- **Bezeroak eta App Profilak:** Nabigazio historia, erosketa lehentasunak, kupoi pertsonalizatuak eta promozio elkarreragiteak.
- **Dokumentuak eta Irisgarritasuna/Iritziak:** Erabiltzaileen iritziak, App-eko iruzkinak, eskaneatutako PDF albaranak eta jakinarazitako intzidentziak.

## 2. Gomendatutako Datu-Base Arkitektura (2 Sistema)

Mantenua errazteko eta segurtasuna nahiz errendimendua bermatzeko, bi datu-base osagarritan oinarritutako eredua inplementatuko da:

| Datu-Basea | Motor Mota | Gordetzen duen Informazioa | Arrazoitzea eta Abantailak |
|---|---|---|---|
| **MySQL** | Erlazionala (SQL) | <ul><li>Produktuen katalogoa eta prezioak</li><li>Inbentarioaren eta stockaren kontrola</li><li>Salmentak eta kutxa-txartelak</li><li>Langileen eta hornitzaileen datuak</li></ul> | Sendotasun eta integritate transakzional handia eskaintzen du. Kutxan desbideratzerik ez dela egongo eta stock zenbaketan akatsik ez dela gertatuko bermatzen du. |
| **MongoDB** | Ez-Erlazionala (NoSQL) | <ul><li>Kupoiak eta promozio pertsonalizatuak</li><li>Erosketa historia malgua</li><li>Iruzkinak, intzidentziak eta erregistroak</li></ul> | App-eko erabiltzaile kopurua erraz eskalatzea ahalbidetzen du, bezeroen edo promozioen datuen egitura aldatuz datu-base nagusia desorekatu gabe. |

## 3. Segurtasun Eskemak eta Datu Babesa

Negozioaren jarraitutasuna bermatzeko eta legezko araudia betetzeko, ondorengo segurtasun geruzak ezarriko dira:

- **Informazioaren Zifratzea:** Datu sentsible guztiak (pasahitzak, datu pertsonalak eta ordainketa xehetasunak) zifratze algoritmo seguruen bidez (AES-256 eta TLS/SSL protokoloak) gordetzen eta transmititzen dira.
- **Roletan Oinarritutako Sarbide Kontrola (RBAC):**
  - *Kutxariak:* Kutxa ordainketa sistemara soilik sarbidea (MySQL).
  - *Denda Arduradunak:* Stocka eta inbentarioa ikusteko zein aldatzeko sarbidea (MySQL).
  - *Marketin/Fidelizazio Taldea:* Bezeroen datuetara eta promozio kanpainetara sarbidea (MongoDB).
- **Segurtasun Kopia Automatikoak (Backups):** Eguneroko babes-kopia automatizatuak instalazio nagusietatik kanpo gordeak, akats teknikoen aurrean berreskuratze azkarra bermatzeko.
- **Sare eta Zerbitzarien Babesa:** Suhesia (Firewall), birus-aurkako korporatiboak eta bi urratseko autentifikazioa (2FA) inplementatzea kudeaketa sarbideetarako.

## 4. Erabiltzaileak eta Baimenak

![Erabiltzaileak sortzeko komandoa](irudiak/25-Erabiltzailea-sortu.png)

Erabiltzaileak sortzeko komando hau erabili dugu.

![IT erabiltzailearekin datu-basera sartzea](irudiak/26-Erabiltzailea-sortuta.png)

Hemen ikus dezakezue nola sartzen den IT erabiltzailetik gure datu-basera.

![Datu-basearen barruan sortutako erabiltzaileak](irudiak/27-Core-Erab.png)

Erabiltzaile desberdinak sortu ditugu datu-basearen barruan. Erabiltzaile bakoitzak baimen desberdinak izango ditu. Adibidez, IT-k datu-basea aldatzeko aukera izango du, giza baliabideak eta erosketakoek aldiz ikusteko soilik.

![IT erabiltzaileari emandako baimenak](irudiak/22-IT-baimenak.png)

Hemen ikus dezakezun bezala, baimen guztiak eman dizkiogu IT-ko erabiltzaileari.

![Giza baliabideen erabiltzailearen baimenak](irudiak/23-GB-baimenak.png)

![Erosketen erabiltzailearen baimenak](irudiak/24-Erosketak-baimenak.png)

Hemen aldiz, giza baliabideetakoei eta erosketakoei datu-basea ikusteko baimena soilik eman diegu.

## 5. Konfigurazio fitxategia

### MySQL

**Kokalekua:**

XAMPP erabili dugunez, XAMPP-eko karpetan egongo da. Kokalekua hau da:

`C:\xampp\mysql\bin\my.ini`

**Zer aldatu dezakegu?**

Adibidez, portua hortik aldatu dezakegu. Gu defektuzkoa utziko dugu, beste zerbitzurik ez dagoelako portu horretan.

![my.ini fitxategiaren konfigurazioa (portua)](./image9.png)

Hemen hainbat konfigurazio aldatu ditzakegu:

- Bind-address bat gehitu, hau da, datu-basera sartzeko beste IPak baimendu. Gure kasuan ez ditugu gehituko, localhost-etik sartuko garelako.

![my.ini fitxategiaren konfigurazio gehiago](./image8.png)

### MongoDB

**Kokalekua:**

MongoDB erabili dugunez, MongoDBren instalazio-karpetan egongo da konfigurazio fitxategia. Kokalekua hau da:

`C:\Program Files\MongoDB\Server\8.3\bin\mongod.cfg`

![mongod.cfg fitxategiaren edukia](./image2.png)

**Zer aldatu dezakegu?**

- **Portua** hortik aldatu dezakegu (`port: 27017`). Guk lehenetsitakoa (27017) utziko dugu, beste zerbitzurik ez duelako portu hori erabiltzen.
- **systemLog (erregistroak):** Log edo erregistroen fitxategia non eta nola gorde zehazten du (`C:\Program Files\MongoDB\Server\8.3\log\mongod.log`).
- **bindIp (sare-interfazea):** Datu-basera sartzeko IP helbideak baimentzeko balio du. Gure kasuan `127.0.0.1` utziko dugu (localhost), lokaletik bakarrik sartuko garelako.
