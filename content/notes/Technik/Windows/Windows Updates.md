---
title: "Windows Updates"
tags:
- Windows
---

## Signaturen
- Windows Update Signaturen sind unter dem Ordner **catroot** und **catroot2** gespeichert
- Der **Cryptographic Dienst** benutzt das *%windir%\System32\catroot2\edb.log*
- Löschen oder Resetten des catroot Ordner kann bei Update Problemen helfen
	- Kann dabei vorkommen das es nicht gelöscht werden kann weil es vom **Cryptographic Dienst** genutzt wird (Access Denied / Used by another Program) 
		- `net stop cryptsvc`
		- `md %systemroot%\system32\catroot2.old`
		- `xcopy %systemroot%\system32\catroot2 %systemroot%\system32\catroot2.old /s`
		- Next, delete all the contents of the catroot2 folder. Having done this, in the CMD windows, type the following and hit Enter:
		- `net start cryptsvc`
- Ordner wird resettet wenn Windows Update wieder gestaret wird 

## Inplace
- Windows Inplace Upgrades benötigt immer das **Default** Image von Microsoft
	- **Kein Custom Image**