---
title: "Session Token Attacks"
tags: 
- Security
- Technik
---
Session-Token-Angriffe sind Cyberangriffe, die darauf abzielen, einen oder mehrere Session Tokens im Browser zu stehlen, um Zugang zu den Accounts der Opfer zu erlangen. Diese Art von Angriffen wird in letzter Zeit immer häufiger bei großen YouTube-Kanälen durchgeführt. Das aktuellste und wahrscheinlich bisher prominenteste Beispiel ist der Angriff auf den Kanal [LinusTechTips](https://www.youtube.com/watch?v=yGXaAWbzl5A).

## Was sind Session Token?
Session Tokens ermöglichen es dir, **bei einer Webseite angemeldet zu bleiben**, selbst wenn du deinen Browser schließt. Wenn du dich bei einer Webseite anmeldest, wird häufig ein solcher Session Token im lokalen Browser-Speicher angelegt. Wenn du den Browser am nächsten Tag öffnest und die Webseite erneut besuchst, bist du automatisch angemeldet.

## Wie funktioniert die tokenbasierte Authentifizierung?
Bei einer tokenbasierten Authentifizierung muss sich ein Benutzer zunächst bspw. mit seinem Benutzernamen und Passwort authentifizieren. Danach verifiziert der Server die Anmeldedaten und stellt dem anfragenden Benutzer (bei erfolgreicher Authentifizierung) einen Token zur Verfügung. Dieser Token wird dann im Browser gespeichert und bei zukünftigen Authentifizierungsanfragen mitgesendet. Abhängig davon, ob der Token gültig ist oder nicht, werden diese Anfragen gewährt oder abgelehnt. Allerdings können Administratoren oder Entwickler einer Anwendung bestimmte Einschränkungen für die Verwendung des Tokens festlegen. So kann beispielsweise bestimmt werden, ob der Token nur einmalig verwendet werden darf und nach dem Abmelden des Benutzers ungültig wird (siehe nächsten Abschnitt), oder ob er nach einer bestimmten Zeit automatisch ungültig wird.

## Simulieren eines Session Token Angriffs
Um solche Angriffe nachzustellen, habe ich die Webanwendung Gitea verwendet. Wenn wir uns zunächst die Login-Maske anschauen, sehen wir dort eine Option, um eingeloggt zu bleiben. Diese Funktion schreibt normalerweise einen Cookie, der den Benutzer auch nach dem Schließen des Browsers eingeloggt lässt.

![[notes/images/gitea_1.png]]


Wenn wir uns nun die Cookies anschauen, erkennen wir dort ein Cookie namens **i_like_gitea**. Dieses Cookie (oder Token) authentifiziert die aktuelle Sitzung des Benutzers.

![[notes/images/gitea_2.png]]

Wenn ein Angreifer Zugriff auf diesen Token hat, kann er ihn einfach in seinen Cookie-Speicher kopieren und hat nun Zugriff auf das System. Um dies zu simulieren, habe ich ein Inkognito-Fenster geöffnet und den Token kopiert.

![[notes/images/gitea_4.png]]

Nach neu laden der Seite, bin ich als Benutzer des Token angemeldet.

![[notes/images/gitea_5.png]]

Loggt sich nun allerdings der Benutzer aus seiner Session **aktiv** aus, dann wird der Token ungültig und auch die Session des Angreifers wird automatisch beendet.


## Gegenmaßnahmen die du tun kannst
1. **Inkognito Modus** verwenden damit keine Tokens gespeichert werden die ein Angreifer verwenden kann. 
2. **Least Priviledge** - Wenn möglich nur Accounts verwenden die keine Administrativen Rechte haben. Falls Admin Account benötigt wird, dann einen Inkognito Browsertab nutzen. Im zweifel hat ein Angreifer dann nur Zugriff auf einen normalen Benutzeraccount ohne Admin Rechten 
3. **Automatisches löschen aller Cookies** nachdem der Browser geschlossen wurde. Diese Funktion bieten viele Browser an (u.a. Firefox und Edge). 
4. **Updates** - Betriebssystem und Browser aktuell halten.
5. **Awareness** - Öffne nicht jeden E-Mail Anhang der komisch ausschaut und schalte die Dateierweiterung an 

>[!INFO]
>Achtung
>
>Natrürlich hat ein Angreifer Zugriff auf die Tokens, wenn man gerade in diesem Augenblick angemeldet ist. Allerdings reduzieren insbesondere Maßnahme 1 und 3 die Anzahl der Systeme auf die ein Angreifer potenziell Zugriff haben. 





