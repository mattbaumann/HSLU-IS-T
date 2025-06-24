
### IT-Sicherheit
ISO: die Minimierung der Verwundbarkeit von Werten (Assets) und Resourcen.

* Schützt die Informationen (Daten, Programme)
* Schützt die Infrastruktur (Computer, Drucker, Netzwerke, ...)

Kann unterteilt werden in 3 aufbauende Sicherheitsstufen:

| Level | Deutsch                    | Eng      | Beschreibung                                                                        |
| ----- | -------------------------- | -------- | ----------------------------------------------------------------------------------- |
| 3     | **Datensicherheit**        |          | Sicherheit vor Datenverlust                                                         |
| 2     | **Informationssicherheit** | Security | Schutz von unauthorisierter Informationsveränderung und Zugriff (Programme + Daten) |
| 1     | **Funktionssicherheit**    | Safety   | Ist-Funktionalität = Soll-Funktionalität                                            |
***Schutzziele der IT-Sicherheit:*** 

| Schutzziel                                        | Beschreibung                                                      | Bsp Mittel                                                                                                                                                                                                        |
| ------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vertraulichkeit<br>Confidentiality                | Information kann nur durch authorisierte Subjekten gelesen werden | **Verschlüsselung:** Klartext → Geheimtext (Cyphertext)                                                                                                                                                           |
| Integrität<br>Integrity                           | Korrektheit und Vollständigkeit Infos und Methoden                | - Korrekter Inhalt<br>- Unmodifizierter Zustand<br>- Erkennung Modifikation<br>- Temporale Korrektheit![[SchutzzieleIntegritaet.png]]                                                                             |
| Verfügbarkeit<br>Availability                     | Sicherstellung, dass Subjekte Zugriff auf das System haben        | $Verfugbarkeit=\frac{Gesammtzeit - Gesammtausfallzeit}{Gesammtzeit}$                                                                                                                                              |
| ***Weitere***                                     | ***Schutzziele***                                                 |                                                                                                                                                                                                                   |
| Verbindlichkeit<br>non-repudiation                | Subjekt kann Aktion im Nachhinein nicht abstreiten                |                                                                                                                                                                                                                   |
| Anonymisierung<br>Pseudonymisierung               |                                                                   | Anonymisierung → Entfernen Identifier<br>Pseudonymisierung → Verändern Identifier <br>1. Direkt → Keytabelle wird getrennt verwaltet<br>2. Indirekt → Hashing, kann nur durch Probieren der Möglichkeiten gesucht |
| Authenizität<br>Authentifizierung                 | Echtheit und Glaubwürdigkeit<br>(Bist du wer du vorgibst?)        | Login Prozess                                                                                                                                                                                                     |
| Authorisierung<br>Zugriffschutz<br>Access Control | Zugriffsrechte prüfen<br>(Was darfst du?)                         | Authorisierung von Benutzergruppen auf HTTP Endpunkte                                                                                                                                                             |
![[Authentifizierung.png]]

Sichere Authentifizierung ⇒ Zugriffschutz
Single Sign-on
Federated Identity Management

## 2-Faktor Authentifizierung

1-Faktor: Der Standard Login via Passwort
2-Faktor: Zwei Faktoren von unterhalb implementiert mit einer Technologie des Faktors

Faktoren:
* Etwas, das Du _weisst_ (PIN, Passwort)
* Etwas, das Du *besitzt* (Keycard, TAN-Liste)
* Etwas, das Du bist (Fingerprint, Iris)

## Passwort/Passphrase

> Subjekt beweisst seine Identität mit etwas was nur der Benutzer weiss

- Passwort / Passphrase
- Antwort auf eine Frage
- Einmal-Passwort

Passwort muss durch einweg Funktion geschützt werden: [[Hash-Funktion]] gespeichert wird der Hash-Wert. Siehe [[Hash-Funktion]] für Cracking, RainbowTable etc

## Authentifizierung durch Haben

* Smartcard
* Slüssel
* Smartphone
* RSA-Token (SecureID), alt, problematisch bei Support-Firmen
* SMS One Time Passwort (MTAN)
* Flicker Code Karten

Häufig mit PIN geschützt und Zertifikate eingesetzt

## Authentifizierung durch Sein

* Fingerprint, Iris, Retina, Face, Voice
![[Pasted image 20250619105502.png]]

Fingerabdrücke in Forensik typisch, Sensoren günstig, 2% keine brauchbaren Abdrücke (Schuppenflechte)

Voice-Recognition
* Textabhängige Verfahren: Dynamic Time Warping (DTW)
* Textunabhängige Verfahren: Gaussian Mixture Models

Gesichtserkennung
Austrixen durch Makeup, welches unterscheidbarkeit von Gesichtern reduziert
Gegenmassnahme:  Algorithmen mit Makeup trainieren

Wenn man nicht erkannt werden möchte durch Image Scraper:
Image Cloaking: zufälige Striche zeichnen beim Lernen. 

Iris (Retina-Scanner)
Erkennt die Muster der Blutgefässe auf der Retina, Infrarot Kamera beläuchtet und Fotografiert