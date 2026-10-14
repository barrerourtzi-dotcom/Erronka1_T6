# 1. Erronka: WAE dokumentazioa

T6 taldea. Web aplikazioen ezarpena.

## 1. GLPI

GLPI enpresaren ekipoak eta intzidentziak kudeatzeko aplikazioa da. Hemen azaltzen dugu nola instalatu dugun eta zer erregistratu dugun.
### 1.1 Instalazioa

GLPI Ubuntu Server makina birtual batean instalatu dugu, Proxmox-en barruan (100 makina). Nabigatzailetik http://192.168.71.186 helbidean sartzen gara.

Instalazioan erabili ditugun parametroak hauek dira:

| Parametroa | Balioa |
|---|---|
| GLPI bertsioa | 10.0.18 |
| Instalazio modua | Tarball (deskargatutako paketea) |
| Karpeta | /var/www/glpi |
| Sistema eragilea | Ubuntu 24.04 |
| Web zerbitzaria | Apache 2.4.58, 80 portua |
| PHP | 8.3.6 |
| Datu-basea | MariaDB 10.11.14 |
| Datu-basearen izena | glpidb |
| Datu-baseko erabiltzailea | admin, localhost-etik |
| Hizkuntza | Gaztelania (es_ES) |

Datu-basea makina berean dago, GLPIk bakarrik erabiltzen duelako eta horrela ez delako sarean irekita egon behar. Datu-baseko erabiltzaileak localhost-etik bakarrik konekta daiteke.

### 1.2 Erregistratutako ekipoak

Enpresako ekipo guztiak GLPIn erregistratu ditugu. Kokapenak, motak eta egoerak euskaraz sortu ditugu, enpresan euskaraz lan egiten dugulako.

Kokapenak: Cloud, Zerbitzari-gela, Finantzak bulegoa, Giza Baliabideak bulegoa, Erosketak bulegoa eta IT bulegoa. Cloud kokapena IsardVDI-n dauden makinentzat da.

#### 1.2.1 Ordenagailuak

| Izena | Mota | Kokapena | Oharrak |
|---|---|---|---|
| WSCore | Zerbitzaria | Cloud | Windows Server, domeinu-kontrolatzailea |
| proxmox | Zerbitzaria | Zerbitzari-gela | Proxmox VE 8.4.0, 192.168.71.185 |
| GLPI | Makina birtuala | Zerbitzari-gela | Ubuntu Server, 192.168.71.186 |
| GLPIBackup | Makina birtuala | Zerbitzari-gela | GLPIren bigarren makina |
| WIN11BEZ1 | Mahaigaineko ordenagailua | Cloud | Windows 11 Pro, 192.168.10.40 |
| WIN11BEZ2 | Mahaigaineko ordenagailua | Cloud | Windows 11 Pro, 192.168.10.102 |

Ordenagailu bakoitzaren Iruzkinak eremuan ezaugarri nagusiak eta IPa idatzi ditugu.

![GLPIn erregistratutako ordenagailuak](Irudiak/glpi-01-ordenagailuak.jpg)

#### 1.2.2 Sareko gailuak

Bi suebaki ditugu eta biak Sareko gailuetan erregistratu ditugu, Suebakia motarekin. pfSense Proxmox-eko 103 makina da. PFSENSE (Cloud) IsardVDI-n dagoena da eta core.lan sarearen atebidea da (192.168.10.254).

![GLPIn erregistratutako sareko gailuak](Irudiak/glpi-02-sare-gailuak.jpg)

#### 1.2.3 Inprimagailuak

WS_T6 zerbitzarian partekatuta dauden bi inprimagailuak erregistratu ditugu, bakoitza bere saileko bulegoan.

![GLPIn erregistratutako inprimagailuak](Irudiak/glpi-03-inprimagailuak.jpg)

### 1.3 Lizentziak

Windows Server 2025 Standard softwarea sortu dugu, Microsoft editorearekin, eta bi lizentzia gehitu dizkiogu:

| Lizentzia | Mota | Kopurua | Esleituta |
|---|---|---|---|
| Windows Server 2025 Standard (16 nukleo) | Nukleo-lizentzia | 1 | WSCore |
| Windows Server 2025 erabiltzaile CAL | Erabiltzaile CAL | 10 | Erabiltzaileei |

Zerbitzariaren lizentzia WSCore ordenagailuari esleitu diogu. CALak ez dira ordenagailu bati esleitzen, erabiltzaile bakoitzeko direlako. Lizentzien kopurua aurrekostuan erosi ditugunekin bat dator.

![Windows Server-en lizentziak](Irudiak/glpi-04-lizentziak.jpg)

### 1.4 Erabiltzaileak

GLPIk dakartzan erabiltzaileez gain (glpi, tech, normal eta post-only), enpresako sei erabiltzaile sortu ditugu, domeinuan dituzten izen berarekin. Hiru profil desberdin erabili ditugu, bakoitzak GLPIn egin behar duenaren arabera:

| Erabiltzailea | Izena | Profila |
|---|---|---|
| obravo | Oier Bravo | Technician |
| pmalatsetxebarria | Peru Malatsetxebarria | Technician |
| lgarcia | Lierni Garcia | Technician |
| ubarrero | Urtzi Barrero | Supervisor |
| jlopez | Joseba Lopez | Self-Service |
| ltellabide | Luis Tellabide | Self-Service |

IT saileko langileek Technician profila dute, tiketak konpondu eta ekipoak kudeatu behar dituztelako. Urtzik Supervisor profila du, IT saileko arduraduna delako eta taldearen tiketak ikusi eta esleitu behar dituelako. Beste sailetako langileek Self-Service profila dute: tiketak ireki eta beren tiketen egoera ikusi besterik ez dute egin behar.

![GLPIko erabiltzaileak](Irudiak/glpi-07-erabiltzaileak.jpg)

![Technician profila duten erabiltzaileak](Irudiak/glpi-08-technician.jpg)

![Supervisor profila duen erabiltzailea](Irudiak/glpi-09-supervisor.jpg)

![Self-Service profila duten erabiltzaileak](Irudiak/glpi-10-self-service.jpg)

### 1.5 Tiketak

GLPI ondo dabilela egiaztatzeko hiru tiket sortu ditugu. post-only erabiltzaileak eskatzen ditu, langile batek bezala, eta tech erabiltzaileari esleitzen zaizkio, teknikariari bezala.

| ID | Izenburua | Mota | Lotutako elementua |
|---|---|---|---|
| 1 | Finantzak inprimagailuak ez du inprimatzen | Intzidentzia | Finantzak_Imprimagailua |
| 2 | P: unitatea ez da agertzen WIN11BEZ2 ordenagailuan | Intzidentzia | WIN11BEZ2 |
| 3 | Erabiltzaile berria Erosketak sailean | Eskaera | |

Tiketak ekipoekin lotu ditugu, horrela ekipo bakoitzaren fitxan bere arazoen historia ikusten delako.

![GLPIko tiketak](Irudiak/glpi-05-tiketak.jpg)

![1. tiketa](Irudiak/glpi-06-tiketa.jpg)

## 2. GitHub biltegia eta GitHub Pages

### 2.1 Biltegia

Erronkaren dokumentazio guztia GitHub-eko biltegi batean dago: https://github.com/barrerourtzi-dotcom/Erronka1_T6

Biltegi bakarra erabiltzen dugu taldekide guztiok, dokumentazio guztia leku batean egon dadin eta edozeinek aldaketen historia ikus dezan.

Modulu bakoitzak bere adarra du: SEA, SZI eta Hardware. Modulu bakoitzeko lana bere adarrean egiten dugu eta, bukatuta dagoenean, main adarrera batzen dugu. Horrela taldekide batek bere moduluan lan egin dezake besteen lana hautsi gabe, eta main adarrean zuzendutako bertsioa bakarrik dago.

### 2.2 Biltegiaren egitura

```
Erronka1_T6/
├── README.md                                  Hasierako orria eta aurkibidea
├── _config.yml                                GitHub Pages-en konfigurazioa
├── Dokumentazioa_SEA.md                       Sistema eragileen administrazioa
├── Dokumentazioa_SB.md                        Sistema banatuak (Proxmox)
├── Dokumentazioa_WAE.md                       Web aplikazioak (GLPI, GitHub eta plangintza)
├── Datu_Base_eta_Segurtasun_Estrategia.md     Datu-baseak eta segurtasuna
├── Dokumentazioa_HW.md                        Hardwarea: aurrekostua, osagaiak eta tailerra
└── Irudiak/                                   Dokumentuetako kaptura guztiak
```

Modulu bakoitzak bere .md fitxategia du, eta kaptura guztiak Irudiak karpetan daude. Irudien izenak modulu bakoitzaren aurrizkiarekin hasten dira (sb-, glpi-), horrela karpetan erraz bereizten direlako.

Dokumentu guztiek egitura bera dute: izenburua, atal zenbakituak, taulak datuentzat eta kaptura bakoitza dagokion azalpenaren ondoan.

### 2.3 GitHub Pages

Biltegia GitHub Pages bidez argitaratu dugu, dokumentazioa web orri gisa irakurtzeko GitHub-en kontua izan gabe: https://barrerourtzi-dotcom.github.io/Erronka1_T6/

Settings, Pages atalean main adarra eta erro karpeta aukeratu ditugu. GitHub-ek .md fitxategiak HTML orri bihurtzen ditu Jekyll-ekin. _config.yml fitxategian Cayman gaia jarri dugu, orriak irakurtzeko errazagoak izan daitezen.

README.md fitxategia hasierako orria da. Bertan dago dokumentu guztietarako esteka duen aurkibidea, eta hortik edozein ataletara heltzen da klik batekin.

## 3. Plangintza

T6 taldea. Erronkaren zereginak moduluka eta bakoitzaren egoera.

### 3.1 Zereginak

#### SEA: Sistema eragileen administrazioa

| Zeregina | Egoera |
|---|---|
| core.lan domeinua eta Active Directory instalatu | Eginda |
| DNS eta DHCP konfiguratu | Eginda |
| OUak, erabiltzaileak eta taldeak sortu | Eginda |
| Bezeroak domeinuan sartu | Eginda |
| GPOak sortu eta estekatu | Eginda |
| Inprimagailuak Windows Server-en partekatu | Eginda |
| Inprimagailuen baimenak saileko taldeei eman | Egiteke |
| Zerbitzuak eta prozesuak kudeatu (IE2) | Egiteke |
| Inprimaketa Linuxen CUPSekin eta sistemen artean | Egiteke |

#### SB: Sistema banatuak

| Zeregina | Egoera |
|---|---|
| Proxmox instalatu eta sareak sortu | Eginda |
| GLPI eta GLPIBackup makina birtualak sortu | Eginda |
| pfSense makina birtuala sortu | Eginda |
| CT102 edukiontzia sortu | Eginda |
| Erabilgarritasun handiko soluzioa proposatu | Eginda |
| GLPI pfSense-ren atzean jarri | Egiten |

#### WAE: Web aplikazioen ezarpena

| Zeregina | Egoera |
|---|---|
| GLPI instalatu | Eginda |
| Ekipoak, lizentziak eta tiketak erregistratu | Eginda |
| GLPI erabiltzaileak profilekin sortu | Eginda |
| GitHub biltegia eta adarrak sortu | Eginda |
| GitHub Pages argitaratu | Egiteke |

#### Hardwarea

| Zeregina | Egoera |
|---|---|
| Hardware eta lizentzien aurrekostua | Eginda |
| Osagaien dokumentazioa | Eginda |

### 3.2 Erronkan zehar egindako aldaketak

| Aldaketa | Zergatia |
|---|---|
| Aurrekostuan zerbitzari bakoitzarentzat ekipo fisiko bat jarri dugu, makina birtualak erabili beharrean | Erronkak zerbitzari bakoitza ekipo fisiko batean egotea eskatzen du |
| Aurrekostuan 2 bezero izatetik 10 izatera pasa gara | Domeinuan 10 erabiltzaile daude eta bakoitzak bere ordenagailua behar du |
| CT102 edukiontzia zerbitzurik gabe utzi dugu | Irakasleak esan digu nahikoa dela edukiontzia sortzea |
| GLPI pfSense-ren barneko sarera eramatea erabaki dugu | GLPI zuzenean ikastetxeko sarean zegoen, suebakirik gabe |
