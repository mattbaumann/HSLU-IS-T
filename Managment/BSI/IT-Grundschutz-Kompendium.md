Beantwortete Fragen:
* Was muss ich tun, um einen angemessenen Schutz für einen Informationsverbund zu erreichen?
* Mit welchen Gefährdungen ist für bestimmte IT-Schutzobjekte zu rechnen?
* Welche Anforderungen müssen für bestimmte IT-Schutzobjekte/Bausteine erfüllt werden?
## Inhalt
Rollendefinitionen: Verantwortliche für die Initiierung und Umsetzung von Massnahmen

Beschreibung von elementaren Gefährdungen
* G0.01 Feuer
* …
* G0.47 Schädliche Seiteneffekte IT-gestützter Angriffe

Die Beschreibung der Gefährdungen dient lediglich der Sensibilisierung und der Begründung von Massnahmen und hat im Grundschutz-Vorgehen keine weitere Funktion!

Beschreibung von Bausteinen
* Bausteine: Gelten für sämtliche oder grosse Teile des Informationsverbunds
* System-Bausteine: Gelten für einzelne oder Gruppen von Objekten (z.B. Server, Netzwerkkomponenten etc.)
* Beide Gruppen sind unterteilt in sog. Schichten
![[BSIBausteine.png]]


### Schichten zur Gruppierung der Bausteine:
Schichten der prozessorientierten Bausteine (übergreifend)
* ISMS: Sicherheitsmanagement
* ORP - Organisation und Personal
* CON - Konzepte und Vorgehensweisen
* OPS - Operativer IT-Betrieb
* DER - Überprüfung von Massnahmen, Detektion und Reaktion auf Sicherheitsvorfälle

Schichten der systemorientierten Bausteine (für einzelne Objekte)
* APP: Absicherung von Anwendungen und Diensten
* SYS - IT-Systeme
* IND - Industrielle IT
* NET - Netzwerke und Kommunikation
* INF- Baulich-technische Gegebenheiten (Infrastruktur)

## Informationen bei den Bausteinen (z. B. SYS.1.1 Allgemeiner Server)
* Beschreibung
* Gefährdungslage (spezifische Bedrohungen und Schwachstellen)
* Anforderungen, damit ein bestimmtes Sicherheitsniveau erreicht werden kann
	* Basis-Anforderungen: MUSS-Formulierung
	* Standard-Anforderungen: SOLLTE-Formulierung
	* erhöhtem Schutzbedarf: SOLLTE-Formulierung
	* Nummerierungsschema: Schicht.Teilschicht.[Teilschicht.]Baustein.Anforderung
		* Beispiele: SYS.1.1.A1, SYS.1.2.2.A5
* Verantwortlichkeiten für die Umsetzung der Anforderungen
* Weiterführende Informationen (z.B. Literatur)
* Kreuzreferenztabellen (siehe «Aufgaben IT-Grundschutz nach BSI», weiter hinten)
* Reihenfolge der Baustein-Umsetzung (vgl. Kap. «Bearbeitungsreihenfolge der Bausteine» IT Grundschutz-Kompendium)
	* R1: Bausteine vorrangig umsetzen
	* R2: Bausteine nachfolgend umsetzen
	* R3: Bausteine immer erst am Schluss umsetzen
* Die Kennzeichnung zeigt nur die sinnvolle zeitliche Reihenfolge für die Umsetzung der Anforderungen des jeweiligen Bausteins auf. Sie stellt keine Gewichtung der Bausteine untereinander dar (alle relevanten Bausteine müssen umgesetzt werden).


### Beispiele
Elementare Gefährdungen
![[ElementareGefaehrdungen.png]]

![[BeispielElementareGefaehrdung.png]]

Bausteine der Schicht IT-Systeme
![[BausteineITSysteme.png]]

Baustein SYS.1.1 Allgemeiner Server
![[BauteilSYS1.1-Part1A.png]]
![[BauteilSYS1.1-Part2A.png]]