---
Category: Functions
Lektionen: Grundlagen, PKI
---

> Ordnet Zeichenketten (Strings) neue Zeichenketten mit fester Länge zuordnet (Einwegfunktion = Trap-Door-Fnc)

Eine Hashfunktion ist eine Abbildung, die eine grosse Eingabemenge auf eine kleinere Zielmenge (Hashwert) abbildet. Aus dem Hashwert können die eingegebenen Daten (Eingabemenge) nicht mehr wieder hergestellt werden. Hashfunktionen werden deshalb auch als Einwegfunktionen bezeichnet.

Wichtige Eingenschaften:
* Einwegfunktion: f: (string) -> hash, f einfach berechenbar, f' computionell unendliche Laufzeit (im Falle von Hash-Fnkt konzeptionell nicht lösbar da Eingabemenge für ein gegebenes f¨' unendlich sein kann)
* Kollisionsresistent: Komputionell unendliche Laufzeit einen anderen Input zu finden mit gleichem Hash.
* Effizienz: Die Funktion muss schnell berechenbar sein
* ***Bitsensensitivität**: Eine Hashfunkt ist kryptographisch, wenn ein Bit Änderung am Input im Mittel 50% vom Output Hash ändern. 

In Datenbanken sollten PW immer als Hash abgespeichert werden um Logins verhindern, wenn die DB entwendet wird. Im Moment muss das PW Brute-Forced werden mit Hashcat, wenn nur der Hash vorhanden ist.

> [!info]
> Brute-Force Kollisionssuche ist $\neq$ Preimage-Angriff, siehe [[#Knacken (Preimage-Angriff)]]

Eine Hash-Funkt gilt als geknackt, wenn es ein Verfahren gibt, dass exponentiell weniger Operation durchführbar ist als Brute-Force-Obergrenze (O(n))

| Hash   | Länge                  | Verwenden | Seit | Brute-Force-Kollisionssuche (o(n))                                                                               |
| ------ | ---------------------- | --------- | ---- | ---------------------------------------------------------------------------------------------------------------- |
| MD-5   | Geknackt               | ❌         |      |                                                                                                                  |
| RIPEMD | Geknackt               | ❌         |      |                                                                                                                  |
| SHA-1  | 160 Bit Geknackt       | ❌         |      | $2^{80} \longrightarrow^{2005} 2^{69}$ aka 170'000 Jahre<br>$2^{80} \longrightarrow^{2009} 2^{52}$ aka 1.3 Jahre |
| SHA-2  | 224, 256, 384, 512-Bit | ✓         |      |                                                                                                                  |
| SHA-3  | 224, 256, 384, 512-Bit | ✓         | 2012 |                                                                                                                  |

### Knacken
> [!info]
> Bei Passwort-Hashes reicht es aus irgend ein Input zu finden, welcher sich auf den gewünschten Hash auflösen lässt. Wenn der Input vorgegeben ist, dann ist es ein [[#Preimage-Angriff]]. 

>Gesucht sind zwei beliebige und unterschiedliche Dokumente M und M’, welche den gleichen Hashwert haben.

* Brute-Force Attack: Alle möglichen PW hashen und mit Ziel vergleichen
* Rainbow-Table: Wir verbinden Hash-Reduktions-Funktionen zu langen Ketten, die wir schnell durchsuchen können. Dann können wir z.B. schnell erkennen welchen Prefix das PW hatte
	* Hashfunktion erzeugt aus PW Hashwert
	* Reduktionsfunktion: Bildet Hashwert auf ein Passwort (möglichen Input in Hashfnk) ab
	* Dadurch sinkt der Raum aller möglichen PW (für geg. Zeichenvorrat) ab
	* Trade-off zwischen Rainbow-Table-Grösse und Zeitaufwand das PW zu knacken

![[RainbowTableChain.png]]

Anwendung:
![[Pasted image 20250619103434.png]]

Gegenmassnahme:
* Salt - ein String der mit dem PW Kombiniert wird und zufällig gewählt ist. Das Salt darf in der DB abgespeichert werden.
* Pepper - Parameter der für ALLE hashes gleich ist und *nicht* in der DB abgespeichert wird sondern geheim bleibt. (Hilft bei DB Diebstahl)

Password_Hash= H(Password || Salt || Pepper)

### Preimage-Angriff

> Zu einem gegebenen Dokument M wird ein anderes Dokument M’ gesucht, das den gleichen Hashwert hat (komplexeres Problem!).

Bei Signaturen reicht es nicht ein x beliebigen Inhalt zu finden, zu dessen die Signatur angeklebt werden kann um ein gültiges Fake zu produzieren. Meistens will man eine ganz bestimmte Änderung im Dokument vornehmen und dann die alte Signatur dranpflatschen und voià **der Preimage-Angriff**.

