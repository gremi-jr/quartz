---
title: "Windows Integrity Level"
tags:
- Windows
---

# Windows Integrity Level

Windows Integrity Level beschreibt die Vertrauensstellung oder die Rechte eines Programmes oder eine Datei besitzt.
Dabei gibt es 4 verschiedene Level: Low, Medium, High, System.
Jede Datei/Programm eines Levels besitzt nur Rechte im selben oder darunterliegenden Level. Bspw. darf ein Programm im Medium Integritätslevel auch auf die Dateien im Low Level zugreifen. 
Meistens laufen die Browser in Low oder Unstrusted Level damit, im Falle des Falls, Schadcode nur eingeschränkt zugriff hat.

>[!INFO]
>Im Process Explorer von den [[Sysinternals]] Tools kann das Integritätslevel eingesehen werden.

## Low
Low hat sehr stark eingeschränkte Rechte worin die Datei oder das Programm lesen und schreiben darf.
Nur der Status "Nicht Vertrauenswürdig" (Untrusted) hat weniger Rechte

## Medium
Auf dem Medium Level befinden sich die normalen Benutzerrechte.

## High
- Administrative Rechte

## System
Vergleichbar mit root-Rechten auf einem Linux System. 

## Installer
Das Level des Installer ist abgekapselt von den eigentlichen Leveln und stehen eher für sich alleine.

![[notes/images/Windows Integrity Level 1.png]]

---
# References
[What Are the Different Windows "AppData" Folders for, Anyway? - YouTube](https://www.youtube.com/watch?v=3XjSTG-oIMw)