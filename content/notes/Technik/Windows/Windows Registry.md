---
title: "Windows Registry"
tags:
- Windows
---

## Hives
- HKEY_CURRENT_CONFIG / HKEY_LOCAL_MACHINE kann **nur bei Administratoren** geändert werden
	- HKEY_CURRENT_CONFIG <=> HKEY_LOCAL_MACHINE
	- HKEY_CURRENT_CONFIG ist **das selbe** wie HKEY_LOCAL_MACHINE
		- Nur ein Shortcut für die Einfachheit
		- Current_Config zeigt dabei auf einen weiteren Unterordner von HKLM
- HKEY_CURRENT_USER kann **von jedem Benutzer** geändert werden
	- HKEY_CURRENT_USER <=> HKEY_USERS

- Die "**CURRENT**" Hives speichern die Einstellungen zuerst in den **RAM** und dann auf die Festplatte
	- Bspw. werden Einstellungen von HKEY_CURRENT_CONFIG erst nach einem Reboot in HKEY_LOCAL_MACHINE gespeichert
