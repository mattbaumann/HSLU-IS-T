Teil der Vorlesung: Introduction

> Ordnet Zeichenketten (Strings) neue Zeichenketten mit fester Länge zuordnet (Einwegfunktion = Trap-Door-Fnc)

Wichtige Eingenschaften:
* Einwegfunktion: f: (string) -> hash, f einfach berechenbar, f' computionell unendliche Laufzeit
* Kollisionsresistent: Komputionell unendliche Laufzeit einen anderen Input zu finden mit gleichem Hash.

| Hash  | Länge   |
| ----- | ------- |
| SHA-1 | 160 Bit |
In Datenbanken sollten PW immer als Hash abgespeichert werden um Logins verhindern, wenn die DB entwendet wird. Im Moment muss das PW Brute-Forced werden mit Hashcat, wenn nur der Hash vorhanden ist.

Als Qualitätsmerkmal von Hashfunkt ist, dass ein Bit Änderung am Input wird min XX% vom Output Hash ändern.

### Knacken

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

