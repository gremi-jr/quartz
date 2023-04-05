---
title: DoT und DoH? - DNS Verschlüsselung
aliases: DoH, DoT
date: 2023-04-05 13:08
---

## Warum DNS Verschlüsselung?
Standardmäßig sind DNS Anfragen unverschlüsselt, was es ermöglicht einem Angreifer oder dem Internet Provider mitzulesen, welche Webseiten besucht werden. Diese Daten können zum Profiling oder Werbezwecke genutzt, analysiert und verkauft werden.

## DNS over HTTPS
DNS over HTTPS (DoH) ist eine Möglichkeit [[DNS]] Anfragen zu verschlüsseln. DoH ist die bessere Wahl für private Nutzungszwecke, da es durch den HTTP Traffic verschleiert wird. DoH Anfragen können außerdem nicht verhindert werden ohne nicht auch den gesamten Web Traffic zu blockieren.

Bei DoH werden die Anfragen über das HTTP bzw. HTTP/2 Protokol verschickt und verschlüsselt, was bewirkt das es nach normalen Webtraffic ausschaut. Ein Netzwerkadministrator oder Angreifer, welcher das Netzwerk mit schneidet, kann also nicht unterscheiden ob es sich um normale Web Request handelt oder um verschlüsselte DNS Anfragen. 

![[notes/images/DoH.png]]


## DNS over TLS

DNS over TLS (DoT) ist eine weitere Möglichkeit seine [[DNS]] anfragen zu verschlüsseln. Allerdings wird dies über TLS und einen separaten Port realisiert. Dies stellt eine bessere Wahl aus dem Standpunkt der Netzwerksicherheit und Administration dar. Durch die Nutzung eines speziellen Ports kann der Traffic überwacht und ggf. blockiert werden.

![[notes/images/DoT.png]]

## Unterschiede zwischen DoH und DoT
Anders als DoH wird DoT über einen (neuen/separaten) Port 853 angefragt und bearbeitet. Somit wird auch nicht das HTTP Protokoll verwendet sonder mittels TLS verschlüsselt. Durch die Eigeschaft das DoT über einen separaten Port kommuniziert, können Netzwerkadministratoren oder auch jeder andere mit Einsicht im Netzwerk, DoT Anfragen erkennen und deuten. Gegebenenfalls kann auch der Port blockiert werden, möchte jemand nicht das verschlüsselte [[DNS]] Anfragen genutzt werden.


## Der Resolver kennt eure Webseite trotzdem!
Dabei ist allerdings nur der Weg vom Client zum DNS Resolver verschlüsselt. Da der DNS Resolver die Anfrage bearbeiten muss, wird sie logischerweise dort entschlüsselt und bearbeitet. **Somit müssen wir den Resolver mit unseren Daten vertrauen.**

Es gibt verschiedene Anbieter, welche DoH anbieten, unter anderem Google und Cloudflare. Im Firefox ist Cloudflare DoH standardmäßig integriert. 

![[notes/images/firefox_doh.png]]




---
# References
- https://www.cloudflare.com/learning/dns/dns-over-tls/