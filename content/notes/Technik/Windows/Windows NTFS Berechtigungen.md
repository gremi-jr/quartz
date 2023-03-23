---
title: "Windows NTFS Berechtigungen"
aliases: NTFS
tags:
- Windows 
---

- Berechtigungen über den "Security" Tab im Explorer
- "Full Control" kann Ownership über Dateien übernehmen
- "Modify" kann alles was "Full Control" kann **außer Ownership** 
	- **Modify kann Dateien löschen** - Read/Write nicht!
- Bei nur "Write" Permission kann die Person zwar Dateien dort erstellen und bearbeiten allerdings können sie diese Dateien danach **nicht mehr sehen** weil ihnen die "Read" Rechte fehlen
	- Nützlich wenn man bspw. in der Schule Aufgaben "abgibt" zum Leherer

## Standard Berechtigungen (vererbt von C:)
- (Domain) Admins = Full Control
- Authenticated User = Modify
- (Domain) Users = Read & Execute

## Verschachtelte Berechtigungen - Mehere Gruppen mit unterschiedlichen Rechten
- Zwei Gruppen - Eine "Allow" andere "Deny" = **"Deny"**
	- **Deny always overrule Allow**
- Berechtigungen sind **kummulativ** - sie rechnen sich auf
	- User AB = lesen **und** schreiben
		- Gruppe A = Lesen
		- Gruppe B = Schreiben
