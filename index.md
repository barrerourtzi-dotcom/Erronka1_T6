---
layout: default
title: Hasiera
---

# 1. Erronka: T6 taldea

Core enpresarentzako informatika-azpiegitura diseinatu eta muntatu dugu: Windows Server domeinua, sareko zerbitzuak, Proxmox birtualizazio-zerbitzaria, GLPI ekipoak eta intzidentziak kudeatzeko, datu-baseak eta azpiegitura osoaren aurrekostua.

## Dokumentazioa

| Ikasgaia | Edukia | Dokumentua |
|---|---|---|
| SEA: Sistema eragileen administrazioa | Active Directory, OUak, erabiltzaileak, GPOak eta inprimaketa | [Dokumentazioa SEA](Dokumentazioa_SEA.md) |
| SZI: Sareko zerbitzuak | DHCP, DNS eta Jitsi Meet audio eta bideo zerbitzua | [Dokumentazioa SZI](Dokumentazioa_SZI.md) |
| SB: Sistema banatuak | Proxmox, makina birtualak, edukiontzia eta erabilgarritasun handia | [Dokumentazioa SB](Dokumentazioa_SB.md) |
| WAE: Web aplikazioen ezarpena | GLPI, GitHub biltegia eta plangintza | [Dokumentazioa WAE](Dokumentazioa_WAE.md) |
| HW: Hardwarea | Aurrekostua, osagaiak, tresnak, hondakinak eta tailerra | [Dokumentazioa HW](Dokumentazioa_HW.md) |
| Datu-baseak eta segurtasuna | MySQL eta MongoDB, erabiltzaileak eta baimenak | [Datu-base eta segurtasun estrategia](Datu_Base_eta_Segurtasun_Estrategia.md) |

## Azpiegitura laburki

| Ekipoa | Funtzioa | IP helbidea |
|---|---|---|
| WS_T6 | Windows Server, core.lan domeinuko kontrolatzailea, DNS eta DHCP | 192.168.10.1 |
| JitsiErronka | Ubuntu Server, Jitsi Meet (jitsi.core.eus) | 192.168.10.3 |
| WIN11BEZ1, WIN11BEZ2 | Windows 11 bezeroak | 192.168.10.40, 192.168.10.102 |
| PFSENSE | core.lan sarearen atebidea | 192.168.10.254 |
| proxmox | Proxmox VE birtualizazio-zerbitzaria | 192.168.71.185 |
| GLPI | GLPI makina birtuala Proxmox-en | 192.168.71.186 |

## Biltegia

Iturburu-fitxategiak eta aldaketen historia GitHub-en daude: [barrerourtzi-dotcom/Erronka1_T6](https://github.com/barrerourtzi-dotcom/Erronka1_T6)
