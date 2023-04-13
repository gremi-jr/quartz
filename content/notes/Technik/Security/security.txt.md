---
title: security.txt
aliases:
tags:
- Security
date: 2023-04-12 13:45
---
# security.txt
Die security.txt ist eine Datei, welche sich im `.well-known` Verzeichnis (oder im Root-Verzeichnis `your-domain.com/security.txt`) einer Webseite hinterlegt ist und definiert wie und welche Personen/Postfach bei einem Sicherheitsproblem kontaktiert werden soll. Dies erleichtert Sicherheitsforscher und Entwickler mit den Betreibern in Kontakt zu treten und über diese Lücke aufzuklären. Neben normalen Personen lässt sie sich auch, ähnlich wie die [[robots.txt]], maschinell auslesen.

Dieses Vorhaben wurde im [RFC9116](https://tools.ietf.org/html/rfc9116) niedergeschrieben. Dabei beinhaltet die Datei neben verpflichtende auch optionale Angaben. [Hier](https://securitytxt.org/.well-known/security.txt) kann ein beispiel der security.txt von [securitytxt.org](https://securitytxt.org) angesehen werden. Die Webseite ermöglicht einem auch das erstellen einer solchen Datei mithilfe eines Formular, welche die Datei im passenden Format erzeugt. 


---
# References
- https://securitytxt.org/
- [EH20 Docker BugBounty Erlebnisse - Youtube](https://www.youtube.com/watch?v=qcMkBxCU6nk)