---
title: Azure AD Joined Device Local Administrator - "Dieser Vorgang erfordert erhöhte Rechte"
tags:
- Windows
- Azure
---
## Fehlerbeschreibung
Wir haben im Projekt festgestellt das die [[Privileged Identity Management|PIM]] Rolle "Azure AD Joined Device Local Administrator" nicht sehr zuverlässig funktioniert. Da wir diese Rolle als alternative für das neu aufkommende [[notes/Technik/Windows/Windows LAPS|Windows LAPS]] oder generell LAPS gesehen haben, haben wir sie in der Testphase aktiviert.


Dabei zeigte sich folgendes Fehlerbild: An manchen neuinstallieren oder auch im schon länger im Betrieb befindlichen Geräten **lässt sich mit aktivierter Rolle keine Anwendung als Administrator starten** - sei es eine CMD oder Executable/MSI. Es erscheint die Fehlermeldung bei Eingabe der Credentials **"Dieser Vorgang erfordert erhöhte Rechte".**

## Ursache
Die Ursache liegt in einer zeitlichen Differenz zwischen der Aktivierung der Rolle und **der Aktualisierung des [Primary Refresh Token (PRT)](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-primary-refresh-token)** welcher sich noch im Cache vom Gerät befindet.
Dieser Primary Refresh Token handhabt vereinfacht gesagt verschiedene Aspekte der Azure AD Authentifizierung. Liegt somit kein neuer Token auf dem Client, welcher die PIM Rolle zum Local Administrator beinhaltet, hat euer Account mit der aktivierten Rolle noch keine Rechte.


Überprüfen kann man dies innerhalb der CMD den **SSO State** mit Hilfe von `desregcmd /status`  Befehl. Wenn dort das Attribut **AzureAdPrtUpdateTime** einen Zeitstempel vor der Aktivierung der Rolle besitzt, wird die neue Rolle nicht aktiviert werden bis sich der Token aktualisiert hat, was standardmäßig [**nur alle 4 Stunden**](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-primary-refresh-token#how-is-a-prt-renewed) der Fall ist.

![[notes/images/PRT_1.png]]

## Möglicher Workaround
Um nicht 4 Stunden zu warten kann man eine vorzeitige Aktualisierung des PRT anfodern.  Dies geschieht mit dem Befehl `dsregcmd /refreshprt`. Nach ein paar Minuten warten kann sich mit dem Benutzer ab und wieder anmelden, wonach sich der PRT aktualisiert haben sollte und man sich nun den Benutzer mit der Rolle nutzen könnte. **Alternativ kann ein Anmelden des Benutzers am lokalen Client helfen.**

![[notes/images/PRT_2.png]]