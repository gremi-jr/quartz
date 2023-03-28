---
title: Installation einer VM unter Windows auf Basis von Hyper-V
---
## Hyper-V Installation
> [!INFO] Information!
> 
>Diese Anleitung beschreibt die Installation und Einrichtung von Hyper-V auf einem Windows 10 Pro Gerät.

1. Um Hyper-V zu installieren muss zunächst das Feature aktiviert werden. Suche dazu in der Windows Suchleiste nach "Windows-Feature aktivieren oder deaktivieren" und öffne das Programm.  
	![[notes/images/HyperV1.png]]
2. Setze den Haken bei "Hyper-V" und bestätige mit "OK"
	![[notes/images/HyperV2.png]]
3. Nun werden die Komponten identifiziert und ggf. heruntergeladen.
	![[notes/images/HyperV3.png]]
4. Beachte das du nun dein Computer neustarten musst!
	![[notes/images/HyperV4.png]]
5. Nach einem Neustart kannst du den "Hyper-V-Manager" starten. Herzlichen Glückwunsch! Du hast Hyper-V installiert!
	![[notes/images/HyperV5.png]]

## Installation
### Download Client ISO
Das Windows 11 ISO kann [hier](https://www.microsoft.com/en-us/software-download/windows11) heruntergeladen werden. Wähle dazu einfach deine passenden Daten aus.
![[notes/images/Windows 11 ISO.png]]

### Virutelle Maschine erstellen
 
1. Öffne Hyper-V-Manager falls noch nicht offen und wähle auf der Rechten Seite deinen Computernamen aus. Klicke anschließen auf der rechten Seite auf "Neu" -> "Virtueller Computer".
	![[notes/images/VM-Install-1.png]]

2. Klicke bei der "Vorbemerkung" auf "Weiter"
3. Vergebe unter "Namen und Pfad angeben" einen Namen für deine VM. Optional kannst du auch den Pfad anpassen, wo deine VM gespeichert werden soll.
	![[notes/images/VM-Install-2.png]]

4. Wähle "Generation 2" bei "Generation angeben"
> [!Important] Achtung!
> 
> Generation 1 funktioniert grundsätzlich auch, kann allerdings zu inkompatibilitäten führen wenn man bspw. Windows 11 benutzen möchte. 

	 ![[notes/images/VM-Install-3.png]]

5. Unter dem Punkt "Speicher zuweisen" wird der Arbeitsspeicher der VM zugewiesen. Je nach Verfügbaren Arbeitsspeicher empfehle ich min. 1GB. Mehr ist immer besser. Dynamischer Arbeitsspeicher steigert oder verringert automatisch nach vorhandenen Arbeitsspeicher die Zuweisung.
	![[notes/images/VM-Install-4.png]]

6. Im Fenster "Virtuelle Festplatte verbinden" wird eine neue virutelle Festplatte erstellt. Dabei kannst du aussuchen wie Groß die Festplatte deiner VM sein soll. Für Windows Systeme empfehle ich min. 64GB.
	![[notes/images/VM-Install-5.png]]

7. Wähle unter "Installationsoptionen" den Punkt "Betriebssystem zu einem späteren Zeitpunkt installieren" und klicke auf "Fertigstellen".
	![[notes/images/VM-Install-6.png]]

8. Wähle die eben erstelle VM im Hyper-V-Manager aus und klicke im rechten unteren Menü auf "Einstellungen"
	![[notes/images/VM-Install-7.png]]

9. Wähle unter "SCSI-Controller" die Option "DVD-Laufwerk" aus und klicke auf "Hinzufügen". 
	![[notes/images/VM-Install-8.png]]

10. Wähle das neu hinzugefügte DVD-Laufwerk aus und wähle im Menü "Imagedatei" aus und durchsuche dein Laufwerk nach dem ISO welches du installieren möchtest. Klicke anschließend auf "Anwenden".
	![[notes/images/VM-Install-9.png]]

11. Zuletzt muss die Boot-Order angepasst werden. Hierzu klicke auf "Firmware" und wähle das DVD-Laufwerk aus um anschließen mit dem Button "Nach oben" das ISO an erster Boot Stelle zu setzen.
	![[notes/images/VM-Install-10.png]]

12. Klicke auf "Anwenden"
13. Optional kannst du unter den Menüpunkten Prozessor noch weitere CPU Kerne zuweisen.
14. Klicke im Hyper-V-Manager auf deine erstelle VM und klicke anschließend im rechten Menü auf Verbinden. Dann kannst du die VM starten und die ISO Installationsschritte ausführen.
	![[notes/images/VM-Install-11.png]]
