# 1. Erronka: T6 taldea

Core enpresarentzako informatika-azpiegitura diseinatu eta muntatu dugu: Windows Server domeinua, Proxmox birtualizazio-zerbitzaria, GLPI ekipoak eta intzidentziak kudeatzeko, eta azpiegitura osoaren aurrekostua.

## Dokumentazioa

| Modulua | Dokumentua |
|---|---|
| Sistema eragileen administrazioa (SEA) | [Dokumentazioa_SEA](Dokumentazioa_SEA.md) |
| Sareko zerbitzuak (SZI) | [Dokumentazioa_SZI](Dokumentazioa_SZI.md) |
| Sistema banatuak (SB) | [Dokumentazioa_SB](Dokumentazioa_SB.md) |
| Web aplikazioen ezarpena (WAE): GLPI, WordPress, GitHub eta plangintza | [Dokumentazioa_WAE](Dokumentazioa_WAE.md) |
| Datu-baseak eta segurtasuna | [Datu_Base_eta_Segurtasun_Estrategia](Datu_Base_eta_Segurtasun_Estrategia.md) |
| Segurtasuna (SEG) | [Dokumentazioa_SEG](Dokumentazioa_SEG.md) |
| Hardwarea: aurrekostua, osagaiak eta tailerra | [Dokumentazioa_HW](Dokumentazioa_HW.md) |
| Jasangarritasuna | [Jasangarritasun_Plana-Core](Jasangarritasun_Plana-Core.md) |

## Azpiegitura laburki

| Ekipoa | Funtzioa | IP helbidea |
|---|---|---|
| WS_T6 | Windows Server, core.lan domeinuko kontrolatzailea | 192.168.10.1 |
| WIN11BEZ1, WIN11BEZ2 | Windows 11 bezeroak | 192.168.10.40, 192.168.10.102 |
| PFSENSE (Cloud) | core.lan sarearen atebidea | 192.168.10.254 |
| proxmox | Proxmox VE birtualizazio-zerbitzaria | 192.168.71.185 |
| GLPI | GLPI makina birtuala Proxmox-en | 192.168.71.186 |

## Biltegiaren antolaketa

Modulu bakoitzak bere adarra du (SEA, SZI eta Hardware) eta bukatutako lana main adarrera batzen da. Kaptura guztiak [Irudiak](Irudiak) karpetan daude. Dokumentazioa web orri gisa: https://barrerourtzi-dotcom.github.io/Erronka1_T6/
