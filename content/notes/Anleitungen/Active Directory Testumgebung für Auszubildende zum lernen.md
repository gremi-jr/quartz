---
title: Active Directory Testumgebung für Auszubildende zum lernen
tags:
  - Anleitung
  - Active Directory
  - Ausbildung
---
## Einleitung
Diese Anleitung soll dabei helfen eine Test Active Directory Umgebung für Gruppenrichtlinien oder auch AD Gruppen und User zu erstellen. 
Zielgruppe der Anleitung ist in erster Linie Auszubildende, welche sich mit einer AD Umgebung vertraut machen möchte ohne etwas "kaputt" zu machen. Allerdings kann ebenso jeder diese Anleitung zur Hilfe nutzen.
> [!Important] Achtung!
> Bitte beachte das dies **keine** Anleitung ist, wie ein Active Directory in einer Firmenumgebung nach Best Practices installiert wird! Die Anleitung ist alleinig für Testzwecke gedacht!

Ich habe diese Anleitung öfters genutzt um in meiner Ausbildung mich mit dem AD vertraut zu machen. 

### Voraussetzungen
- Hardware Empfehlung
	- min. 16GB RAM
	- min. 4 CPU Kerne
- Windows 10 oder 11 Pro
- Stabile Internetverbindung
- [[notes/Anleitungen/Installation einer VM unter Windows auf Basis von Hyper-V|Funktionierende Virtualisierungsumgebung]] 

### Virtuelle Maschine Installation
Installiere dir als erstes sowohl eine Windows 10 als auch eine Windows Server 2019 VM.
> [!Important] Achtung!
> Beachte das bei dem Windows Server die **Desktop Experience** und bei Windows 10/11 als zu installierende Version **Pro** auszuwählen.

## Active Directory Installation
1. Öffne auf deinem Windows Server den Server Manager
	![[notes/images/ADinstall1.png]]

2. Klicke auf "Manage" im rechten oberen Rand des Server Managers und klicke auf "Add Roles and Features"
	![[notes/images/ADinstall2.png]]

3. Klicke "Next" auf der *Before you begin* Seite
	![[notes/images/ADinstall3.png]]

4. Stelle Sicher dass "Role-based or feature base installation" ausgewählt ist und klicke "Next"
	![[notes/images/ADinstall4.png]]

5. Klicke Next beim Auswahl des Zielservers
	![[notes/images/ADinstall5.png]]

6. Klicke auf die linke Checkbox bei der Rolle "Active Directory Domain Services"
	![[notes/images/ADinstall6.png]]

7. Im Folgefenster klicke auf "Add Features" und dann auf "Next"
	![[notes/images/ADinstall7.png]]

8. Im Fenster "Select Features" klicke auf Next
9. Klicke im Fenster AD DS auf Next
10. Klicke unter Confirmation auf "Install"
	![[notes/images/ADinstall11.png]]

11. Die Installation vom AD DS wird nun gestartet
	![[notes/images/ADinstall12.png]]

12. Nach fertiger Installation kann das noch offene Fenster geschlossen werden
13. Klicke im Server Manager auf die Flagge mit gelben Warnzeichen und anschließend auf "Promote this server to a domain controller"
	![[notes/images/ADinstall14.png]]

14. Wähle "Add a new forest" und vergebe ein Root Domain Name. Klicke anschließend auf "Next"
	![[notes/images/ADinstall15.png]]

15.  Stelle sicher das bei "Domain Name System (DNS) Server" ein Haken gesetzt ist und vergebe ein Passwort
	![[notes/images/ADinstall16.png]]

16. Klicke bei *DNS Options* auf "Next"
17. Unter *Additional Options* wird automatisch der Domain Name eingetragen
	![[notes/images/ADinstall18.png]]

18. Wähle Next unter *Paths* und *Review Options*
19. Wähle "Install" unter *Prerequisites Check* - die Warnungen kannst du ignorieren.
	![[notes/images/ADinstall21.png]]

20. Nach der Installation wirst du automatisch ausgeloggt und der Server startet sich automatisch neu
	![[notes/images/ADinstall22.png]]

21. Nach erfolgreichem Neustart kannst du dich mit dem Administrator und deinem vergebenen Passwort anmelden. Herzlichen Glückwunsch - Du hast ein Active Directory mit Domain Controller installiert!
	![[notes/images/ADinstall23.png]]

Nachdem du dich angemeldet hast, kannst du bspw. das "Group Policy Management" nutzen um Gruppenrichtlinien zu erstellen. Unter "Active Directory Users and Computers" kannst du Benutzer- und Computerobjekte verwalten. 

> [!Information] Information!
> Es ist ratsam eine statische IP für den Domain Server zu vergeben. Entweder im Netzwerkadapter auf dem Server oder auf deinem DHCP Server/Router.

## Client Domain Join
Um nun ein Gerät in die Domäne hinzuzufügen, installiere zuvor eine Windows 10 oder Windows 11 Pro virtuelle Maschine oder sogar auf einer Hardware.

**Voraussetzung ist, dass sich die VM oder Hardware im selben Netz befindet und die Domain Server IP erreichbar ist!**  


1. Trage die IP Adresse des Domain Controller als DNS Server im Netzwerkadapter auf dem Windows Client ein. Außerdem empfiehlt sich IPv6 im Netzwerkadapter zu deaktivieren um Fehler vorzubeugen.
   Alternativ kann der DNS Name auch auf einem DNS Server eintragen, worauf der Client Zugriff hat.
	![[notes/images/Windows Domain Join1.png]]

2. Trage in den Systemeinstellungen die Domäne ein und melde dich mit den Anmeldedaten des Administrators der Domäne an!
	![[notes/images/Windows Domain Join2.png]]

3. Ist das Gerät erfolgreich der Domäne beigetreten erscheint folgende Meldung. Der Computer muss danach neugestartet werden.
	![[notes/images/Windows Domain Join3.png]]

4. Im AD können wir nun auch schon das Geräteobjekt erkennen.
	![[notes/images/Windows Domain Join4.png]]


## Übungsaufgabe
*Fiktives Szenario*

Die neugegründete Firma ThinkMax ist gerade dabei alle notwendigen Systeme zu installieren und konfigurieren.
Ihr seid auserwählt worden den notwendigen Domänen Controller samt Domäne aufzusetzen. Dabei soll die Domäne den Namen der Firma (um Gruppen-Nummer ergänzen) tragen.
Strukturiert wird das AD nach ihren Abteilungen "Einkauf", "Marketing" und "IT".
Unter diesen Organisation Units (OU) werden die User und Computer gepflegt. Die IT hat den Zusatz, dass neben den Computer auch Server hinterlegt sind.

Nach dem ihr die Domäne konfiguriert habt sollen Gruppenrichtlinien (GPOs) erstellt werden, die folgende Anforderungen umsetzen:
- Setzten des Hintergrundbildes für die jeweilige Abteilung
- Passwort Richtlinie für Benutzer (min. 4 Zeichen, 1 Sonderzeichen und 1 Zahl)
- Setzen des AD Account "L-ADMIN" als lokaler Administrator
- Eingehende Ping Anfragen in der Windows Firewall Aktivieren (// Stichwort ICMPv4)

Im Anschluss soll für jede Abteilung ein zentraler Netzwerkordner, auf dem DC bereitgestellt werden. Die Benutzer erhalten den Zugriff über eine Benutzergruppe. Die IT Abteilung hat Zugriff auf jedem Ordner. Die Marketing und Einkauf Abteilung nur auf ihre eigenen.

-> [[private/Musterlösung AD Testumgebung|Musterlösung]]