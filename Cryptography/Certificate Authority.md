
Wir brauchen ein Weg zum prüfen ob ein Public-Key [[Authentifizierung|authentisch]] ist. Schaffung einer vertrauenswürdigen Institution, die öffentliche Schlüssel beglaubigt und publiziert

Vertrauenswürdige Institution = Zertifizierungsstelle = CertificateAuthority (CA)

* Durch die Beglaubigung ordnet die CA den öffentlichen Schlüssel zweifelsfrei einem Subjekt zu
* Durch die Publikation wird er allen Kommunikationspartnern zugänglich gemacht
* Die digitale Beglaubigung eines öffentlichen Schlüssels wird als "Zertifikat" bezeichnet.
* Hinweis: Zertifikate können nicht nur für Personen ausgestellt werden, sondern auch für Computer

**Anforderung an Öffentliche Schlüssel** müssen beglaubigt, d.h. eindeutig einer Person (einem Computer) zugeordnet werden können: Bei der Beglaubigung den Schlüssel in ein Zertifikat «verpacken»

**Anforderung an private Schlüssel** müssen sicher (d.h. nur für den Besitzer zugänglich) aufbewahrt werden ➔ Schlüssel auf Smart-Card ablegen oder andere sichere Ablagemedien

Ohne Authentizitätsprüfung des öffentlichen Schlüssels:
![[ManInTheMiddle.png]]

### Herstellung Zertifikat

1. Antragssteller identifiziert sich bei der CA mithilfe eines Identitätsdokuments (z.B. Pass od. ID)
2. Aus Namen des Antragsstellers, dessen öffentlichem Schlüssel und weiteren Informationen wird ein Datensatz gebildet (Zertifikatsinhalt)
3. Dieser Datensatz wird mithilfe des privaten Schlüssels der CA signiert (=digitale Beglaubigung)➔Zertifikat
4. CA veröffentlicht das Zertifikat

![[CertificateProduction.png]]

### Zertifikatsklassen
Zur Beurteilung der Vertrauenswürdigkeit von Zertifikaten wird in der Regel ein Klassifizierungssystem verwendet
- Dieses System macht u.a. Vorgaben für folgende Faktoren
- Registrierungsprozess inkl. Art des geforderten Identitätsnachweises des Antragsstellers
- Im Zertifikat verwendeter Name des Antragsstellers
- Zu verwendender Token (Hard-/Soft-Token)
- Erlaubte Zertifikatsinhaber (z.B. natürliche Personen)
- Anforderungen an die CA (Betrieb, Personal, Prozesse)


| Klasse        | Sicherheitsniveau                                                                   | Beschreibung                                                                                                                                                                                                                        | Bsps                                                                                                                                                                                                                                                                              |     |
| ------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| Class 1 Certs | niedrig                                                                             | - Keine Identitätsüberprüfung<br>- Inhabername einmalig<br>- Self-Service Beantragung/Ausstellung<br>- Bei Let's Encrypt, automatischer Prozess mit<br>File auf Webserver mit Nounce<br>drin, welche Let's encrypt vorgegeben hatte | <ul><li>Freemail-Certs<br>Identitätsprüfung: <br>E-Mail-Verifikation<br>«Persona not validated» statt Name</li><li>Let's Encrypt: Free TLS-Certificates<br>CA prüft ob Antragssteller Domaininhaber darstellt<br>Domain-Validated-Certificates<br>(DV-TLS-Certificates)</li></ul> |     |
| Class 2       | mittlere                                                                            | - Identiätsprüfung mittels<br>Dokumenten und DBs<br>- Privat-Person: Pass/ID<br>- Firma: Rechtliche und Operationelle Existenzprüfung<br>- Pass/ID von Firmenvertreter                                                              | <ul><li>TLS-Zertifikate<br>Organization-Validated-Certificates<br>(OV-TLS-Certificates)</li></ul>                                                                                                                                                                                 |     |
| Class 3       | hohe                                                                                | - Strenge Identiätsprüfung<br>- Persönlicher Termin / Pass / ID<br>- beglaubigtes Antragsdokument<br>- Video-Identifikation<br>- biometrische Pass                                                                                  |                                                                                                                                                                                                                                                                                   |     |
| Class 3       | Qualified Certificates<br>höchste Sicherheit<br>Gleich handschrift.<br>Unterschrift | CA unter staatlicher Kontrolle<br>Anerkennung der CA + Rezertaudits<br>Nur natürliche Personen                                                                                                                                      | SwissID                                                                                                                                                                                                                                                                           |     |
| Class 3       | Extended Validation Certificates                                                    | Strenge Identitätsprüfung<br>Weitere Prüfungen<br>CA steht unter Kontrolle                                                                                                                                                          | TLS-Zertifikate mit grüner Addresszeile                                                                                                                                                                                                                                           |     |


## Cerificate Policy

Anforderungen, die an die Ausstellung von Zertifikaten oder Betrieb einer CA gestellt werden. RFC3647 (Certificate Policy and Certification Practices Framework)

* **Certificate Policy (Zertifikatsrichtline)** Rahmenbedingungen für die Ausstellung von Zertifikaten entsprechend der definierten Zertifkatsklasen beschreibt
* **Certificate Practice Statement (Zerifikatsverwendungserklärung)** Dokument, das beschreibt, wie eine Organisation eine CA betreibt, um deren Sicherheit und die Einhaltung der CertificatePolicy zu gewährleisten


### Angriffsvektoren / Verwundbarkeiten / Massnahmen
* Direkter Angriff auf schwache Validationssysteme (Comodo)
* Zertifikate für Phishing Sites ausgestellt und diese legitimiert mit EV
* Certificate Pinning, Assozierung eines Hosts mit dem erwarteten X.509 Zertifikat
  Gut für Apps welche im Notfall updaten werden können
  Schlecht für Browser, wo Pin nach Erstellung nicht mehr entfernt werden kann und Provider kann sich selber aussperren aus ihren Nutzern
* Ungültigkeitserklärung (Revokation), Zertifikate können vor Ablauf Gültigkeitsdatum für ungültig erklärt werden. Identifiziert durch Seriennummer. Revokationsliste (Certificate Revocation List; CRL)
	* Privater Schlüssel gebrochen
	* Zertifikatsbesitzer verlässt das Unternehmen
	* Metadaten veraltet / Neuausstellung Zertifikat
* OCSP Online Certificate Status Protocol


![[Pasted image 20250627084507.png]]

Revokationslisten müssen kurze Ablaufdaten haben, damit die Clients regelmässig aktualisieren.

**Vollständige Revokationsliste (Base CRL):** Enthält Verweise auf sämtliche Zertifikate, welche bis zum Ausgabezeitpunkt der Liste revoziert worden sind
**Delta Revokationsliste (Delta CRL)**: Enthält Verweise auf diejenigen Zertifikate, welche seit der Ausgabe der letzten Base CRL revoziert worden sind

### Asymmetrisch Verschlüsselung

![[Pasted image 20250627084842.png]]
![[Pasted image 20250627084917.png]]

### Personal Security Environment

Ablagemedium für private Schlüssel
* Soft-Token (Passwort-geschützte Datei/DB)
* Kryptoprozessor (Chip-Karte, Hard-Token, Smart-Card, Crypto-Card)
* Hardware Security Module (HSM), Krypto-co-prozessor auf Mainboard

![[Pasted image 20250627085358.png]]

* Hybridkarte: 2 + unabhängige Chips, individuelles Interface. Z.B. 2 RFID und ein kontaktbasiert (Zutrittskontrolle, Bezahlung und PKI zum einstecken)
* Personal Security Environment mit Krypto-Prozessor um Private Keys auf der Karte zu generieren, dieser ist nur einmal vorhanden und die Berechnung kann auch auf die Karte ausgelagert werden.

### Directory Service
Ablageort der ausgestellten Zertifikate und CRL. Datenabgleich mit anderen Verzeichnisdiensten

### Sicherheitsapplikation
Direkter Zugriff auf Private Key oder Kommunikation mit Crypto Card. Zugriff auf eigenes Zertifikat oder Zertifikat des Kommunikationsparters, Zugriff auf Verzeichnisdienst

- IPSEC (Layer 3)
- TLS (Layer 4)
- SSH
- FTPS
- S/MIME oder PGP (Sichere E-Mail)
- POP3S, IMAPS, SMTPS
- LDAPS
- EAP-TLS (Extensible Authentication Protocol)

![[Pasted image 20250627101305.png]]

TLS 1.3 aus 2008
Verbesserungen der Sicherheit
- Ablösung unsicherer Algorithmen und Verfahren (MD5, SHA-1, DES, RC4, CBC-Modes, Compression, Regeneration)
- Verschlüsselung ab Schritt 2 des Handshakes (Zertifikat verschlüsselt)
- Forward Secrecy obligatorisch
- Performance: # Schritte / 2 beim Verbindungsaufbau
- 03.22 Browser unterstützen TLS1.0 - 1.1 nicht mehr
![[Pasted image 20250627101630.png]]

## Publikation PKI Implementation
* Microsoft Server
* OpenSSL

Aufgaben CA:
- Herstellen, Erneuerung und Publizieren von Zertifikaten
- Zertifikate für ungültig erklären und in CRL aufnehmen
- CRL publizieren
- Kreuzzertifizierung (Zertifikate für andere CAs ausstellen)
- Key-(Certificate-) Update: Erzeugen eines neuen Zertifikats auf der Basis eines neuen Schlüsselpaars
- CertificateRenewal: Erzeugen eines neuen Zertifikats auf der Basis des bestehenden Schlüsselpaars
- Wie ist der Vorgang des CertificateRenewalsicherheitstechnisch zu beurteilen?

![[Pasted image 20250627101853.png]]

Für unterschiedliche Schlüsselverwendungszwecke kommen unterschiedliche Zertifikate zum Einsatz. Ein Benutzer verwendet beispielsweise drei Zertifikate.
- Zertifikat zum Verschlüsseln (mit Backup)
  Key Usage: Daten-oder Schlüsselverschlüsselung
  Extended Key Usage: Sichere E-Mail, Dateiverschlüsselung etc.
- Zertifikat zum Signieren/Authentifizieren (ohne Backup)
  Key Usage: Digitale Signatur
  Extended Key Usage: Sichere E-Mail, Client-Authentifikation, Smart-Card Logonetc.
- Zertifikat um Erstellen von qualifizierten Signaturen (ohne Backup)
  Key Usage: Nicht-Abstreitbarkeit(non-repudiation)
  Extended Key Usage: -


**Zertifikatsprüfungen**
Zert ist gültig wenn:
* Gültigkeitsdauer: Aktuelles Datum liegt im Gültigkeitsbereich des Zertifikats
* Ungültigerklärung: Zertifikat wurde nicht revoziert, d.h. vor Ablauf für ungültig erklärt
* Zertifikatssignatur: Zertifikat wurde von der CA gültig signiert und gilt somit als echt

![[Pasted image 20250627110520.png]]

CA-Zertifikate ohne übergeordneten CA werden Root-CA bezeichnet: Trust-Anchor, können nicht über die Signatur, nur durch den Fingerprint geprüft werden
Subzertifikate können mithilfe des Zertifikats der ausstellenden CA überprüfen

Generell kann die Echtheit eines jeden Zertifikats durch einen Vergleich von dessen Fingerprint mit dem Fingerprint des Original-Zertifikats überprüft werden. Die automatische Prüfung von Subjekt-Zertifikaten über die Signatur setzt das Vorhandensein von Root-CA Zerts voraus.

Betriebssystem-und Browser-Hersteller liefern vorinstallierte Root-CA Zertifikate. Manuell nachinstallierbar. DigiCert publizieren die Fingerprints ihrer Root-CA Zertifikate im Web.

![[Pasted image 20250627111548.png]]

- CA-Zertifikat: Zertifikat, das eine CA für eine CA (gleiche oder andere) ausstellt
- Kreuzzertifikat: CA-Zertifikat, das eine CA für eine andere CA ausstellt (Nennen Sie ein Beispiel!)
- Selbst signiertes CA-Zertifikat: CA-Zertifikat, das eine CA für sich selber ausstellt, wobei der private Schlüssel den zugehörigen öffentlichen Schlüssel signiert (Nennen Sie ein Beispiel!)
- Selbst signiertes Benutzer-Zertifikat: Zertifikat, das ein Benutzer für sich selber ausstellt, wobei der private Schlüssel den zugehörigen öffentlichen Schlüssel signiert (Nennen Sie ein Beispiel!)
![[Pasted image 20250627111707.png]]

![[Pasted image 20250627111718.png]]

## Zertifikat

- Ein Zertifikat ist eine digital signierte Datei, die über einen exakt definierten Aufbau verfügt
- Der Aufbau folgt i.d.R. dem ITU Standard X.509 (ITU = International TelecommunicationUnion)
- In der Vorlesung werden nur X.509 Zertifikate behandelt
- Neben den X.509 Zertifikaten gibt es noch Zertifikate, die anderen (z.T.) weniger verbreiteten Normen folgen
- PGP Zertifikate (Pretty GoodPrivacy)
- SPKI Zertifikate (Simple Public Key Infrastructure)


- «Klassische» Zertifikate
- Revokationslisten (CRLs)
- Attribut Zertifikate

![[Pasted image 20250627112225.png]]
Standard-Informationen sind REQUIRED.

![[Pasted image 20250627112409.png]]

![[Pasted image 20250627112426.png]]

Weitere Erweiterungen, die nicht im dargestellten Zertifikatsaufbau aufgeführt sind:
- AuthorityInformationAccess1(AIA):Zeiger auf weitere CA-Informationen. In Microsoft Zertifikaten z.B. ein Zeiger auf das CA-Zertifikat der ausstellenden CA (HTTP-oder LDAP-URL).
- QualifiedCertificateStatements:Hinweise zu einem qualifizierten Zertifikat (rechtsgültige Signaturen)
- BiometricInformation:Hashwert der biometrischen Daten des Zertifikatsinhabers oder ein Zeiger auf die biometrischen Daten selber



```
Certificate:
Data:
Version: 3 (0x2)
Serial Number:
61:03:ee:b6:00:00:00:00:00:0c
Signature Algorithm: sha1WithRSAEncryption
Issuer: DC=ch, DC=sanamed, CN=SanamedIssuingCA
Validity
Not Before: Aug 2 15:16:53 2005 GMT
Not After : Aug 1 15:16:53 2009 GMT
Subject: C=ch, L=Luzern, O=Sanamed, OU=Informatik,
CN=www.sanamed.ch/emailAddress=antonia.grisiger@sanamed.ch
Subject Public Key Info:
Public Key Algorithm: rsaEncryption
RSA Public Key: (1024 bit)
Modulus (1024 bit):
00:c0:d8:ca:66:f4:a9:dc:95:04:25:3c:ae:76:7e:
(…)
9b:d3:5b:50:85:fb:89:c1:4f
Exponent: 65537 (0x10001)
X509v3 extensions:
X509v3 Subject Key Identifier: 02:05:91:D5:2E:86:1F:8A:1D:76:56:AB:DE:39:A0:BC:20:82:00:6B
X509v3 Authority Key Identifier:
keyid:25:36:11:1B:C5:BE:19:DC:0D:78:D2:85:89:34:63:4D:9E:23:3E:DB
X509v3 CRL Distribution Points:
URI:ldap:///CN=SanamedIssuingCA,CN=winsrv1,CN=CDP,CN=Public%
20Key%20Services,CN=Services,CN=Configuration,
DC=sanamed,DC=ch?certificateRevocationList?
base?objectClass=cRLDistributionPoint
URI:http://pki.sanamed.ch/cdp/SanamedIssuingCA.crl
Authority Information Access:
CA Issuers - URI:ldap:///CN=SanamedIssuingCA,CN=AIA,CN=Public%
20Key%20Services,CN=Services,
CN=Configuration,DC=sanamed,DC=ch?
cACertificate?base?objectClass=
certificationAuthority
CA Issuers - URI:http://pki.sanamed.ch/aia/winsrv1.sanamed.ch_
SanamedIssuingCA.crt
X509v3 Basic Constraints: critical
CA:FALSE
X509v3 Key Usage:
Digital Signature, Key Encipherment
1.3.6.1.4.1.311.21.7:
0/.'+.....7.............(...t...R.^...w...0..d...
X509v3 Extended Key Usage:
TLS Web Server Authentication
1.3.6.1.4.1.311.21.10:
0.0
..+.......
Signature Algorithm: sha1WithRSAEncryption
5e:31:e9:0f:b7:3c:ae:d0:fb:8e:79:bc:87:a0:f0:b2:a9:ef:
(…)
da:bf:54:23
```

### Object Identifier (OID)
Identifikationsnummer zur Adressierung von Objekten entsprechend einem weltweit eindeutigen, hierarchischen Adressierungsschema
- Die Nummern werden von der International TelecommunicationUnion (ITU-T) und der International OrganizationforStandardization(ISO) herausgegeben und verwaltet (Identifikation über die erste Ziffer: 0: ITU-T, 1: ISO, 2: Joint ISO/ITU-T)
- OIDs werden zur Identifikation von Objektklassen und Attributtypen in Verzeichnisdiensten verwendet
- Alle Elemente in Zertifikaten werden ebenfalls durch OIDs identifiziert
- Beispiel einer OID: 1.3.6.1.4.1.311.21.10

- Kritische Erweiterungen (critical)
	- Sie müssenvon der Sicherheitsapplikation berücksichtigt werden! Erkennt die Sicherheitsapplikation die Erweiterung nicht, oder kann sie sich nicht an die Anforderung halten, so darf sie das Zertifikat nicht verwenden.
- Sie schränken die Verwendbarkeit von Zertifikaten ein
	- Nicht kritische Erweiterungen (not critical)
	- Sie dürfen von der Sicherheitsapplikation ignoriert werden

![[Pasted image 20250627131625.png]]

![[Pasted image 20250627131716.png]]

![[Pasted image 20250627131735.png]]

## Risiken

- Mangelhafte Überprüfung der Identität von Antragsstellern für Zertifikate durch die CA (RA)
- Falsche Ungültigkeitserklärung eines Zertifikats (denialofservice)
- Umgehung der Hashfunktion (Kollisionsangriff)
- Schlechte Generierung von Zufallszahlen (Symmetrisches Verfahren)
- Brechen des asymmetrischen Verfahrens (Authentizität, Dokument-Signaturen unter fremden Namen, Vertraulichkeit kompromittiert => Unbekannte können entschlüsseln)
- Unsichere Aufbewahrung des privaten Schlüssel
	- Gleiche Auswirkungen wie beim Brechen des asymmetrischen Verfahrens
- Zu signierendes Dokument wird nur teilweise oder nicht mit Originalinhalt angezeigt
	- Der Unterzeichner signiert nicht das, was er glaubt zu signieren
- Signiertes Dokument wird nur teilweise oder nicht mit Originalinhalt angezeigt
	- Der Dokumentempfänger sieht nicht das, was in die Signaturüberprüfung einfliesst
- Zertifikate werden nicht richtig überprüft und deshalb nicht als ungültig erkannt
	- Zertifikatssignatur nicht überprüft
	- Vertrauenswürdigkeit der CA nicht überprüft (CA-Zertifikat nicht installiert)
	- Gültigkeitsintervall des Zertifikats nicht überprüft
	- evokationsstatus des Zertifikats nicht überprüft
- Keine unterschiedlichen Schlüsselpaare für Vertraulichkeit und Authentizität
	- Es gibt Angriffe, welche die Tatsache ausnutzen, dass keine unterschiedlichen Schlüsselpaare für Vertraulichkeit und Authentizität verwendet werden
- Versehentliche Veränderung des Inhalts von signierten Dokumenten (Dokumentsignatur wird dadurch ungültig)
