Symmetrisch:
Klartext - verschlüssln ->  Chiffrierter Text - entschlüsseln -> Klartext
Cleartext - encrypt -> Cyphertext - decrypt -> Cleartext
             |- Key                         -|

Symmetrische Verschlüsselung: Gleicher key für beide operationen.
3DES, IDEA, AES


Asymmetrisch:

Klartext - verschlüssln ->  Chiffrierter Text - entschlüsseln -> Klartext
Cleartext - encrypt -> Cyphertext - decrypt -> Cleartext
             |- public key  private key -|

Asymmetrische Verschlüsselung: Unterschiedliche Keys zum verschlüsseln und entschlüsseln
Jeder Teilnehmer hat ein Schlüsselpaar für sich. Aus dem einen Schlüssel lässt kein Rückschluss auf den anderen Schlüssel zu.

RSA, Elliptische Kurven, El Gamal auf Basis Diffie Hellmann

**Digitale Signatur**: Dort wird nur ein Hashwert anstelle des ganzen Dokuments verschlüsselt:
Beim Signieren wird der Hash-Wert einer Meldung mit dem privaten Schlüssel verschlüsselt
![[Signature.png]]

![[DigitaleSignaturErstellung.png]]

1. Im ersten Schritt wird über die zu signierenden Daten ein Hashwert berechnet. (Eine Hashfunktion ist eine kryptographische Operation, die eine Zeichenfolge beliebiger Länge auf eine Zeichenfolge fester Länge abbildet.)
2. Der Hashwert wird danach mit dem privaten Schlüssel des Unterzeichners verschlüsselt. Das Ergebnis ist die elektronische Signatur.
3. Die elektronische Signatur wird entsprechend des verwendeten Signaturstandards an die zu signierenden Informationen angehängt. Dabei können zusätzliche Informationen wie Zertifikate und Zertifikatsgültigkeitsinformationen mit integriert werden.

**Verifikation**:
Ae: privater Schlüssel (privatekey, encryptkey)➔Zum Erstellen der Signatur
Ad: öffentlicher Schlüssel (publickey, decryptkey)➔Zum Verifizieren der Signatur

Hinweis: Bei asymmetrischer Verschlüsselung mit RSA gerade umgekehrt!

![[DigitaleSignaturVerifikation.png]]

1. Die Signatur wird aus dem Dokument extrahiert.
2. Die Signatur wird mit dem öffentlichen Schlüssel des Unterzeichners entschlüsselt (der öffentliche Schlüssel wird mit dem Zertifikat des Unterzeichners mitgeliefert).
3. Daraus resultiert der wiederhergestellte Hashwert.
4. Der wiederhergestellte Hashwert wird mit dem aus dem Dokument berechneten Hashwert verglichen.
5. Die elektronische Signatur ist nur dann gültig, falls die beiden Hashwerte gleich sind und …
6. … das Zertifikat des Unterzeichners zum Zeitpunkt der Signatur gültig war.
7. Ist dies der Fall, so konnte die Signatur als gültig validiert werden. Ansonsten ist die Signatur ungültig.

**Beweisen**
* Integrität (Unverändertheit) des Dokuments
* Authentizität (Urheberschaft, Echtheit)
* effizient erstellt oder verifiziert werden

Verschlüsselung Mail:
- Alice möchte Bob eine signierte Meldung schicken
- Alice generiert ein Schlüsselpaar Ad und Aeund publiziert Ad (d: decryption, e: encryption)
- Alice verschlüsselt ihre Meldung mit Ae(nur sie ist im Besitz von Ae)

- Bob kann die Meldung mit Ad entschlüsseln
- Schluss: Die Meldung muss von Alice stammen, weil nur sie im Besitz von Aeist


|                                        | **public key**      | **private key**    |
| -------------------------------------- | ------------------- | ------------------ |
| **Authentizität<br>authenticity**      | Signatur überprüfen | Signatur erstellen |
| **Vertraulichkeit<br>confidentiality** | Verschlüsseln       | Entschlüsseln      |
