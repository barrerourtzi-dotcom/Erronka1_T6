# 1. Erronka: SEA dokumentazioa

T6 taldea. core.lan domeinua.

## 1. Domeinua eta zerbitzaria

### 1.1 Domeinua

Baso berri bat sortu dugu domeinu bakarrarekin: core.lan. NetBIOS izena CORE da eta maila funtzionala Windows Server 2016. Ez dugu azpidomeinurik ez beste zuhaitzik sortu, enpresa txikia delako eta egoitza bakarra duelako; domeinu batekin dena leku beretik administratzen da.

.lan amaiera erabili dugu barneko domeinua delako, eta horrela ez dator bat Interneteko benetako domeinu batekin.

### 1.2 Zerbitzaria eta rolak

Domeinu-kontrolatzailea WS_T6 da. 192.168.10.1 IP finkoa jarri diogu, bezeroek DNS gisa erabiltzen dutelako eta helbide hori ezin delako aldatu. Bere DNSak bere buruari begiratzen dio (127.0.0.1) eta atebidea pfSense da, 192.168.10.254.

Instalatuta dituen rolak hauek dira:

| Rola | Zergatik instalatu dugun |
|---|---|
| AD DS | Direktorioa da. Erabiltzaileak zerbitzarian egiaztatzen dira, ez ekipo bakoitzean. |
| Fitxategi-zerbitzaria | LANGILEAK karpeta partekaturako; hor daude sailen karpetak eta karpeta pertsonalak. |
| Inprimaketa-zerbitzaria | Inprimagailuak zerbitzaritik partekatzeko. |

![Zerbitzariaren panela, instalatutako rolekin](Irudiak/01-zerbitzari-panela.png)

### 1.3 Ekipoak

| Ekipoa | Funtzioa | IPa | Administrari kontua |
|---|---|---|---|
| WS_T6 | Domeinu-kontrolatzailea | 192.168.10.1 | CORE\Administrador |
| WIN11BEZ1 | Windows 11 bezeroa | 192.168.10.40 (DHCP erreserba) | |
| WIN11BEZ2 | Windows 11 bezeroa | 192.168.10.102 (DHCP) | |
| pfSense | Bideratzailea eta suebakia | 192.168.10.254 | |

## 2. Antolakuntza-unitateak, erabiltzaileak eta taldeak

### 2.1 Antolakuntza-unitateak

Core izeneko OU bat sortu dugu, eta haren barruan bat sail bakoitzeko: IT, Finantzak, Giza Baliabideak eta Erosketak. Taldeak izeneko OU bat ere badago, talde guztiekin.

![OUen zuhaitza Active Directoryn](Irudiak/07-ou-zuhaitza.png)

Core OUa enpresarena Active Directoryk dakartzan edukiontzietatik bereizteko dago, eta denentzako gidalerroak hor behin bakarrik estekatzen direlako. Sailen OUak daude sail bakoitzak gidalerro desberdinak behar ditzakeelako. Taldeak aparte jarri ditugu Taldeak OUan, erabiltzaileekin nahastuta ez edukitzeko.

### 2.2 Erabiltzaileak eta taldeak

Erabiltzaile bakoitza bere saileko OUan dago eta izen bereko taldean. Sareko unitatea taldearen arabera doa; norbait berria sartzen denean nahikoa da taldean sartzea.

Arduradunak taldea arduradunentzat da. Oraingoz Urtzi bakarrik dago.

| Erabiltzailea | Kontua | OUa | Taldeak |
|---|---|---|---|
| Oier | obravo | IT | IT |
| Peru | pmalatsetxebarria | IT | IT |
| Lierni | lgarcia | IT | IT |
| Urtzi | ubarrero | IT | IT, Arduradunak |
| Joseba Lopez | jlopez | Finantzak | Finantzak |
| Aritz Arrue | | Finantzak | Finantzak |
| Luis Tellabide | ltellabide | Giza Baliabideak | Giza Baliabideak |
| Estibaliz Zendoia | | Giza Baliabideak | Giza Baliabideak |
| Iker Herran | iherran | Erosketak | Erosketak |
| Jon Galarza | | Erosketak | Erosketak |

Kontuek izenaren lehen letra eta abizena dituzte.

![Finantzak OUko erabiltzaileak](Irudiak/08-finantzak-ou.png)

![Taldeak OUko segurtasun-taldeak](Irudiak/09-taldeak-ou.png)

![Finantzak taldeko kideak](Irudiak/10-finantzak-kideak.png)

![Giza Baliabideak taldeko kideak](Irudiak/11-giza-baliabideak-kideak.png)

![Erosketak taldeko kideak](Irudiak/12-erosketak-kideak.png)

## 3. Bezeroak

Bi Windows 11 sartu ditugu domeinuan: WIN11BEZ1 eta WIN11BEZ2. IPa zerbitzariaren DHCPtik hartzen dute, beraz haren tarte berean daude.

WIN11BEZ1 ekipoaren kontua IT OUra eraman dugu. WIN11BEZ2 ekipoarena Computers edukiontzian dago oraindik; ekipo bat domeinuan sartzean hor agertzen da.

![WIN11BEZ1 ekipoa IT OUan](Irudiak/13-it-ou-bezeroa.png)

## 4. Talde-gidalerroak

Bost GPO sortu ditugu. Denak erabiltzailearen konfiguraziokoak dira, aldatzen dena saioa nork hasten duen araberakoa delako eta ez ekipoaren araberakoa.

![Core OUari estekatutako GPOak](Irudiak/14-gpo-estekak.png)

### 4.1 Pantailako atzeko planoa

Erabiltzaile guztientzako gidalerroa da eta Core OUari estekatuta dago. Bi arau ditu Administrazio-txantiloiak, Active Desktop atalean. Batek Active Desktop gaitzen du eta besteak \\\\Ws_t6\langileak\GPO\AtzealdeaGPO.jpeg irudia jartzen du atzeko plano gisa, Bete estiloarekin.

Ekipo guztiek enpresaren atzeko planoa izateko egin dugu, erabiltzaileak aldatu ezin duena. Active Desktop araua dago JPEG irudi bat erabiltzea horrek uzten duelako. Irudia zerbitzariko karpeta partekatu batean dago, bezero guztiak bertara irits daitezen.

![Pantailako atzeko planoa GPOaren konfigurazioa](Irudiak/15-gpo-atzeko-planoa.png)

### 4.2 Mapeatu

Talde konkretuentzako gidalerroa da. P: unitatea saileko karpetara konektatzen du, \\\\Ws_t6\langileak\Departamentuak barruan. Sarrera bat du sail bakoitzeko, eta sarrera bakoitzak elementu-mailako iragazki bat du segurtasun-taldearekin. Finantzak taldeko erabiltzaile batek Finantzak karpeta du P: unitatean, eta Erosketak taldeko batek Erosketak karpeta.

Core OUari estekatuta dago. GPO bakarra erabili dugu taldekako iragazkiekin, OU bakoitzean GPO bat jarri beharrean, horrela gidalerro bakarra dagoelako mantentzeko; erabiltzaile bat sailez aldatzen bada, taldez aldatzea nahikoa da.

![Mapeatu GPOa: P unitatea eta taldearen iragazkia](Irudiak/16-gpo-mapeatu.png)

### 4.3 MapeatuPertsonala

Erabiltzaile bakoitzaren karpeta pertsonala sortzen du \\\\Ws_t6\langileak\Pertsonalak karpetan, bere kontuaren izenarekin. %username% aldagaia erabili dugu karpetak banan-banan ez sortzeko. Erabiltzailearen beraren baimenekin exekutatzen da, karpeta bere izenean gera dadin.

![MapeatuPertsonala GPOaren konfigurazioa](Irudiak/17-gpo-mapeatu-pertsonala.png)

### 4.4 IMP_Finantzak eta IMP_GizaBaliabideak

Saileko inprimagailu partekatua instalatzen dute. IMP_Finantzak gidalerroak \\\\WS_T6\Finantzak_Imprimagailua konektatzen du eta Core OUari estekatuta dago. IMP_GizaBaliabideak gidalerroak \\\\WS_T6\GizaBaliabideak_Imprimagailua konektatzen du eta oraindik ez dago estekatuta.

GPO bidez egin ditugu, erabiltzaileak saioa hastean inprimagailua izan dezan ezer instalatu gabe.

![IMP_Finantzak GPOaren konfigurazioa](Irudiak/18-gpo-imp-finantzak.png)

## 5. Inprimaketa

### 5.1 Inprimagailuak

Bi inprimagailu instalatu ditugu WS_T6 zerbitzarian, bat finantzetarako eta bestea giza baliabideetarako, sail horiek inprimatzen dituzten dokumentuak ez direlako besteenekin nahastu behar.

| Inprimagailua | Saila | Portua | Kontrolatzailea |
|---|---|---|---|
| Finantzak_Imprimagailua | Finantzak | IMP_F (lokala) | Generic / Text Only |
| GizaBaliabideak_Imprimagailua | Giza Baliabideak | IMP_GB (lokala) | Generic / Text Only |

Portu lokalak eta kontrolatzaile generikoa erabili ditugu, ingurune birtualean ez dagoelako inprimagailu fisikorik. Biak partekatuta daude eta direktorioan argitaratuta, bezeroetatik bilatu ahal izateko.

![Inprimaketaren administrazioa, bi inprimagailuekin](Irudiak/19-inprimagailuak.png)

![Finantzak_Imprimagailua partekatzeko aukerak](Irudiak/20-inprimagailua-partekatu.png)

### 5.2 Baimenak

Bi inprimagailuek berezko baimena dute oraindik, eta horrekin Todos taldeak inprimatzen du. Dagozkien baimenak hauek dira: inprimatu, saileko taldeak; dokumentuak administratu, Arduradunak taldeak; inprimagailua administratu, IT taldeak eta administratzaileek.

![Finantzak_Imprimagailua inprimagailuaren segurtasuna](Irudiak/21-inprimagailua-segurtasuna.png)

### 5.3 Portuak eta protokoloak

| Protokoloa | Portua | Non erabiltzen den |
|---|---|---|
| SMB | TCP 445 | Windows-eko inprimagailu partekatuak. Bezeroek hori erabiltzen dute \\\\WS_T6 zerbitzarira konektatzeko. |
| RPC | TCP 135 eta portu altu bat | Windows-eko inprimaketa-ilara |
| IPP | TCP 631 | CUPS Linuxen |
| LPD | TCP 515 | Windows-eko LPD zerbitzua eta cups-lpd Linuxen |
| RAW | TCP 9100 | Sareko inprimagailuak |
| mDNS | UDP 5353 | CUPSeko inprimagailuen iragarpena sarean |
