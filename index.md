---
title: 1. Erronka
---

<div class="hero">
  <h1>1. Erronka: T6 taldea</h1>
  <p>Core enpresarentzako informatika-azpiegitura diseinatu eta muntatu dugu: Windows Server domeinua, sareko zerbitzuak, Proxmox birtualizazioa, GLPI, datu-baseak eta azpiegitura osoaren aurrekostua.</p>
  <div class="tags">
    <span>core.lan</span>
    <span>Windows Server</span>
    <span>Proxmox VE</span>
    <span>GLPI</span>
    <span>Jitsi Meet</span>
  </div>
</div>

## Dokumentazioa

<div class="cards">
  <a class="card" href="Dokumentazioa_SEA.html">
    <div class="card-icon">◧</div>
    <h3>SEA</h3>
    <p>Active Directory, OUak, erabiltzaileak, GPOak eta inprimaketa.</p>
  </a>
  <a class="card" href="Dokumentazioa_SZI.html">
    <div class="card-icon">⇄</div>
    <h3>SZI</h3>
    <p>DHCP, DNS eta Jitsi Meet audio eta bideo zerbitzua.</p>
  </a>
  <a class="card" href="Dokumentazioa_SB.html">
    <div class="card-icon">▦</div>
    <h3>SB</h3>
    <p>Proxmox, makina birtualak, edukiontzia eta erabilgarritasun handia.</p>
  </a>
  <a class="card" href="Dokumentazioa_WAE.html">
    <div class="card-icon">◎</div>
    <h3>WAE</h3>
    <p>GLPI, WordPress, GitHub biltegia eta plangintza.</p>
  </a>
  <a class="card" href="Dokumentazioa_SEG.html">
    <div class="card-icon">🔒</div>
    <h3>SEG</h3>
    <p>Kontingentzia-plana, pasahitzak, sarbide fisikoa, suebakia, VPN eta IDS.</p>
  </a>
  <a class="card" href="Dokumentazioa_HW.html">
    <div class="card-icon">⚙</div>
    <h3>HW</h3>
    <p>Aurrekostua, osagaiak, tresnak, hondakinak eta tailerra.</p>
  </a>
  <a class="card" href="Datu_Base_eta_Segurtasun_Estrategia.html">
    <div class="card-icon">⛁</div>
    <h3>Datu-baseak</h3>
    <p>MySQL eta MongoDB, erabiltzaileak eta baimenak.</p>
  </a>
  <a class="card" href="Jasangarritasun_Plana-Core.html">
    <div class="card-icon">♻</div>
    <h3>Jasangarritasuna</h3>
    <p>Core-ren jasangarritasun plana: ingurumena, gizartea eta gobernantza.</p>
  </a>
</div>

## Azpiegitura laburki

| Ekipoa | Funtzioa | IP helbidea |
|---|---|---|
| WS_T6 | Windows Server, core.lan domeinuko kontrolatzailea, DNS eta DHCP | 192.168.10.1 |
| USWordpress | Ubuntu Server, WordPress (www.core.eus) | 192.168.10.2 |
| JitsiErronka | Ubuntu Server, Jitsi Meet (jitsi.core.eus) | 192.168.10.3 |
| WIN11BEZ1, WIN11BEZ2 | Windows 11 bezeroak | 192.168.10.40, 192.168.10.102 |
| PFSENSE | core.lan sarearen atebidea | 192.168.10.254 |
| proxmox | Proxmox VE birtualizazio-zerbitzaria | 192.168.71.185 |
| GLPI | GLPI makina birtuala Proxmox-en | 192.168.71.186 |

## Biltegia

Iturburu-fitxategiak eta aldaketen historia GitHub-en daude: [barrerourtzi-dotcom/Erronka1_T6](https://github.com/barrerourtzi-dotcom/Erronka1_T6)
