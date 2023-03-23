---
title: "Windows Access-based Enumaration"
tags:
- Windows
---

Wenn Acess-based Enumaration **aktiviert** ist, dann zeigt der Share auch nur die Ordner an auf denen der Benutzer **tatsächlich** Berechtigungen hat. 

Normalerweise werden die Berechtigungen **erst beim Zugriff auf den Ordner geprüft**.
Mit Hilfe von Acess-based Enumaration (ABE) werden die Berechtigungen bei Zugriff auf den Share geprüft und dann nur die Ordner angezeigt auf denen der Benutzer tatsächliche Rechte hat. 