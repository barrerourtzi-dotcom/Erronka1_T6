# Aurrekostua

T6 taldea. Prezioak 2026ko urriaren 13an begiratu ditugu, Espainiako dendetan, eta BEZa barne dute.

## 1. Zer erosi behar den

Hamalau ekipo fisiko behar dira: Windows Server-entzako zerbitzari bat, Proxmox-entzako zerbitzari bat, Ubuntu-rentzako bi zerbitzari eta Windows 11 duten hamar bezero. Domeinuan 10 erabiltzaile daude, beraz bakoitzak bere ordenagailua du.

## 2. Hardwarea

| Ekipoa | Eredua | Kopurua | Prezioa | Guztira |
|---|---|---|---|---|
| Windows Server zerbitzaria | Dell PowerEdge T160, Xeon 6315P, 32 GB RAM, 2 TB | 1 | 1.974,25 € | 1.974,25 € |
| Proxmox zerbitzaria | Dell PowerEdge T160, Xeon 6315P, 32 GB RAM, 2 TB | 1 | 1.974,25 € | 1.974,25 € |
| Ubuntu zerbitzaria | Dell PowerEdge T160, Xeon 6315P, 32 GB RAM, 2 TB | 2 | 1.974,25 € | 3.948,50 € |
| Windows 11 bezeroa | Dell Pro QCM1250, Core i5-14500T, 16 GB RAM, 512 GB SSD | 10 | 849,00 € | 8.490,00 € |

Hardwarea guztira: 16.387,00 €

Lau zerbitzarietarako eredu bera aukeratu dugu. Begiratu ditugun zerbitzarien artean merkeena da, eta denak berdinak izanda ordezko piezak eta mantentze-lana berdinak dira lauretan. Dorre formatukoa da, enpresak ez duelako rack armairurik.

32 GB RAM nahikoa dira Windows Server-ek dituen roletarako (Active Directory, DNS, DHCP, fitxategiak eta inprimaketa) eta Proxmox-en makina birtual batzuk izateko.

Bezeroetarako ordenagailu txikiak aukeratu ditugu, bulegoko lanerako nahikoa direlako eta Windows 11 Pro instalatuta dakartelako.

## 3. Lizentziak

| Lizentzia | Kopurua | Prezioa | Guztira |
|---|---|---|---|
| Windows Server 2025 Standard, 16 nukleo | 1 | 1.359,63 € | 1.359,63 € |
| Windows Server 2025 erabiltzaile CALak, 5eko paketea | 2 | 276,59 € | 553,18 € |
| Windows 11 Pro | 10 | Ordenagailuarekin dator | 0,00 € |
| Proxmox VE | 1 | Doakoa | 0,00 € |
| Ubuntu Server | 2 | Doakoa | 0,00 € |

Lizentziak guztira: 1.912,81 €

Windows Server Standard edizioa aukeratu dugu, Datacenter edizioa garestiagoa delako eta makina birtual asko dituzten zerbitzarientzat delako. Lizentzia zerbitzariaren nukleoen arabera erosten da eta gutxienekoa 16 nukleo da, zerbitzariak gutxiago izan arren.

CALak beharrezkoak dira zerbitzarira konektatzen den erabiltzaile bakoitzeko. Domeinuan 10 erabiltzaile ditugu, beraz 5eko bi pakete behar dira. Erabiltzaile CALak hartu ditugu eta ez gailu CALak, erabiltzaile bat ordenagailu batean baino gehiagotan sar daitekeelako.

Windows 11k Pro edizioa izan behar du, Home edizioa ezin delako domeinuan sartu.

Proxmox VE eta Ubuntu Server software librea dira eta ez dute lizentziarik behar. Proxmox-ek ordainpeko harpidetza bat du, baina aukerakoa da eta ez dugu sartu.

## 4. Guztira

| Atala | Zenbatekoa |
|---|---|
| Hardwarea | 16.387,00 € |
| Lizentziak | 1.912,81 € |
| Guztira, BEZa barne | 18.299,81 € |

Zenbateko horretatik 15.123,81 € oinarria da eta 3.176,00 € BEZa (%21).

## 5. Aurrekostutik kanpo utzi duguna

Bezeroen pantailak, teklatuak eta saguak ez ditugu sartu. Sareko kableak eta switch-a ere ez.

Zerbitzari bakoitzak disko bakarra dakar. Disko hori hondatzen bada zerbitzari horretako dena galtzen da, beraz bigarren disko bat erostea eta biak ispiluan jartzea komeni da. Segurtasun-kopietarako kanpoko disko bat edo NAS bat ere beharko litzateke.

Proxmox-en Community harpidetzak 120 € inguru balio du urtean prozesadore bakoitzeko, eta eguneratze egonkorren biltegirako sarbidea ematen du.

## 6. Prezioen iturriak

- Zerbitzariak: https://www.pccomponentes.com/servidor-dell-poweredge-t160-intel-xeon-6315p-32gb-2tb-torre-no-os
- Bezeroak: https://www.pccomponentes.com/categorias/mini-pcs
- Windows Server 2025 Standard: https://www.senetic.es/product/DG7GMGF0PWHC-0003
- Erabiltzaile CALak: https://www.europeanpc.es/microsoft-windows-server-2025-cals-user-pack-5-unidades-370413
