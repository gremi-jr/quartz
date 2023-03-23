---
title: "Windows Share Berechtigungen"
tags:
- Windows
---

$ nach dem Share Namen macht ihn "unsichtbar"
- Berechtigungen sind wie bei den [[Windows NFTS Berechtigungen|NTFS]] Berechtigungen kummulativ
	- Change = Modify
	- Read = Read & Execute

## Konflikte mit NTFS
- Es greifen die wenigsten Rechte bei Kombinationen an Rechten
- Die Rechte können "zusammengerechnet werden"
- Wenn Benutzer lokal angemeldet ist, sind die Share Rechte egal - dann greift nur NTFS

![[notes/images/NTFS-Permissions.png]]

---

- Wenn ein **lokaler Account schon angelegt** ist, muss sich der User bei einem Sharezugriff **nicht Authentifizieren**
	- Durch das anlegen des Benutzers (inkl. Passwort) ist der User schon bekannt