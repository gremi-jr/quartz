---
title: "Adobe AUSST"
tags:
- Anleitung
- Adobe
- AUSST
---
## Was ist AUSST?
Durch das starke Standing von Adobe Produkten in vielen Unternehmen und schwacher Konkurenz sind Anwendungen wie Photoshop oder Illustrator aus den Umgebungen nicht mehr wegzudenken. 
Ließt man allerdings ein wenig durch die Release Notes oder schaut man in den einschlägigen IT News Webseiten tauchen die Adobe Produkte immer mal wieder mit Sicherheitslücken auf. 
Das Adobe Update Setup Server Tool (AUSST) hilft Administratoren dabei das Update Management vieler Adobe Produkte zu zentralisieren, verwalten und zu steuern. Unter anderem werden dabei auch Netzwerkressourcen im Unternehmen entlastet - mit nur einem einzigen Server.

## Wie funktioniert er?
Der AUSST Server lädt zentral die Update von Adobe aus dem Internet auf einem zentralen Server herunter. Dieser Server hält die Update Pakete für die konfigurierten Geräte vor. Dazu wird auf den Geräten die Adobe Create Cloud Desktop Applikation durch eine Config Datei angepasst welche den internen Update Server enthält. Benötigt wird lediglich ein Webserver - in diesem Artikel wird ein Microsoft IIS Webserver genutzt.

![[notes/images/AUSST-Basic.png]]

## Vorteile
- Niedrigere Bandbreiten ins Internet
- Steuerung welche Updates installiert werden
- Single Application Paketierung (Nur Adobe Create Cloud Desktop notwendig)
- Mehrsprachenfähig

## Anleitung
### IIS Server Vorbereitung
#### Skript
Zur IIS Vorbereitung kann folgendes Skript genutzt werden:
 ```powershell {title="AUSST-IIS-Prep.ps1"}
 <Insert Script>
 ```

Manuelle Schritte werden in dieser Anleitung gut erklärt: https://www.wsus.de/ausst/

### AUSST Synchronisation
Nun Laden Sie die AUSST Anwendung aus der Adobe Admin Console herunter. 

### Client Konfiguration
#### Konfiguration erstellen
#### Konfiguration verteilen