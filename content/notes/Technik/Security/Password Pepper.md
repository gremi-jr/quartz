---
title: "Password Pepper"
tags:
- Security
---

Password Peppering ist eine Methode seine Passwörter im einem Passwort-Manager besser abzusichern, um ihn als Single Point of Failure zu minimieren. Das Passwort wird in zwei Teile aufgeteilt. Dem Passwort und dem Pepper. Man speichert dabei nie beide Teile, sondern nur ein Teil. Der zweite Teil wird gemerkt oder separat gespeichert.

## Vorgehen
Registriert man sich bei einer Webseite, so erstellt man in der Regel einen Benutzernamen und Passwort. Dabei lässt man sich vom Passwort-Manager ein Passwort erstellen und ergänzt es um weitere Zeichen. Man Teil das Passwort theoretisch in zwei Teile. Dieser zweite Teil ist das Pepper und werden nicht zusammen mit dem Passwort im Manager gespeichert. 

>[!Example] Beispiel
>1. Teil - Password: Qwddjt68uKF2934
>2. Teil - Pepper: P3pP3R
>
>Vollständiges Password: Qwddjt68uKF2934**P3pP3R**

Möchtet man sich Anmelden, kopiert man sich den ersten Teil des Passwortes aus dem Passwort-Manager und fügt ihn im Formular ein und erweitert es manuell um den Pepper Teil. 
Es wird empfohlen **nicht alle Passwörter** mit einem Pepper zu versehen, sondern nur die wichtigsten wie das E-Mail Passwort oder Bankaccounts .


## Vorteile
Falls der Passwort-Manager kompromitiert wurde, kann der Angreifer zwar alle Passworter im Vault nutzen. Wenn diese Passwörter allerdings durch ein weiteres Pepper geschützt sind, kann der Angreifer nicht auf die Accounts zugreifen. 
Ebenfalls schützt es vor Phishing-Programme, welche die Zwischenablage auslesen. Auch hier wird wieder nur ein Teil des Passwortes dem Angreifer zugänglich gemacht.

>[!Cite] 
> Security is about layers and peppering is just another layer. You’ll never have a perfect system but the more friction points you give to the attacker the better. - [[Peppering Your Passwords in Your Password Manager How-To Guide  Password Bits]]

## Unterschied zum "Secret Salt"
Häufig werden Passwörter in Datenbanken mit einem Secret Salt abgesichert. Der Unterschied zu Pepper ist allerdings, dass es nicht irgendwo gespeichert wird. Der Passwort Manager weiß nichts von dem Pepper. 

> [!cite]
>  Both salting and peppering is a method of adding something to the end of a password. What makes them different is that the salt is not meant to be secret and is often stored alongside the password in a database. A “secret salt” or, more commonly known, a pepper, is not stored anywhere near the password and is meant to be hidden. - [[Peppering Your Passwords in Your Password Manager How-To Guide  Password Bits]]

---
# References
[[Peppering Your Passwords in Your Password Manager How-To Guide  Password Bits]]
