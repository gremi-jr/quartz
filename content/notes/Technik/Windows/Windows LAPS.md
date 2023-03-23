---
title: "Windows LAPS"
tags:
 - Windows
---
---

# Windows LAPS
- LAPS Lösung welches neu in Windows eingebaut wurde
- (Legacy) [[Microsoft LAPS]] benötigte separate MSI Installation
- Integriert sowohl mit [[Azure AD|AAD]] als auch OnPrem AD
- Hat eigenen Eventlog Channel im Eventviewer
- Nach Passwort Benutzung gibt es verschiedene Möglichkeiten das Passwort zurück zu setzen
	- Bspw. *Reset PW and Reboot* oder *Reset PW and Logout*
## Migration
- Windows LAPS berücksichtigt (legacy) [[Microsoft LAPS]] Policies
- Legacy Microsoft LAPS muss nicht installiert sein, wird alternativ auch automatisch deaktiviert (self-diable)
- Benutzt allerdings legacy LAPS UI
- Recommended to move to new Windows LAPS Config (Wegen neuen Encryption Features)

---
# References
https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-overview#windows-laps-supported-platforms-and-azure-ad-laps-preview-status
https://www.youtube.com/watch?v=jdEDIXm4JgU