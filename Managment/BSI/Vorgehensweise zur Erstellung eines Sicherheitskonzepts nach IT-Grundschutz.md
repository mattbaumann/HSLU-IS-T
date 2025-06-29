Konkrete Beispiele im Foliensatz Standards II

![[VorgehenErstellenIT-Sicherheitskonzepts.png]]

### IT-Strukturanalyse – Gruppenbildung/Komplexitätsreduktion
* Gleichartige Komponenten zu Gruppen zusammenfassen
* Mögliche Gruppierungskriterien
* Systeme von gleichem Typ
* Systeme mit gleicher oder nahezu gleicher Konfiguration
* Systeme mit gleicher oder nahezu gleicher Netzwerkanbindung
* Systeme mit gleichen administrativen und infrastrukturellen Rahmenbedingungen
* Systeme, welche für gleiche Aufgaben genutzt werden
* Systeme, welche den gleichen Schutzbedarf aufweisen

### Schutzbedarfsfeststellung
Bestimmung des Schutzbedarfs des betrachteten Informationsverbunds (nach Komplexitätsreduktion)

Zu beantwortende Fragen:
* Wie viel Schutz benötigen die identifizierten Objekte?
* Wie kann man den Schutzbedarf einschätzen?
* Welche Objekte haben einen erhöhten Schutzbedarf?


Definition der Schutzbedarfskategorien entsprechend der Besonderheiten der Organisation

Schutzbedarfsfeststellung
* von IT-Anwendungen und Daten
* davon abgeleitet von IT-Systemen => Vererbung
* davon abgeleitet von Kommunikationsverbindungen und IT-Räumen => Vererbung

Dokumentation und Interpretation der Ergebnisse

Die IT-Grundschutz-Vorgehensweise empfiehlt drei Schutzbedarfskategorien anhand der maximalen Schäden und Folgeschäden bei Verlust der Vertraulichkeit, der Integrität und der Verfügbarkeit:
* **Normal** Begrenzte und überschaubare Schäden
* **Hoch** Beträchtliche Schäden möglich
* **Sehr hoch** Existentiell bedrohliche, katastrophale Schäden möglich

Beispiel Anwendungen
![[SchutzbedarfAnwendungen.png]]
Beispiel IT-Systeme
![[Schutzbedarf IT-Systeme.png]]
Beispiel Räume
![[SchutzbedarfRäume.png]]
## Modellierung nach IT-Grundschutz
![[Modellierung.png]]
Nachbilden des erhobenen IT-Verbunds mit Hilfe der vorgegebenen IT Grundschutz-Bausteine

Ergebnis: IT-Grundschutz-Modell

Ziel: Alle Zielobjekte des Informationsverbunds sind angemessen durch IT-Grundschutz-Bausteine abgebildet


Die Modellierung erfolgt entsprechend dem Schichtenmodell des IT-Grundschutzes
![[BSIBausteine.png]]

Schichtweise werden diejenigen Bausteine ausgewählt, welche für die Sicherheit des IT-Verbunds notwendig sind (gemäss Strukturanalyse oder evtl. Schutzbedarfsfeststellung)

Ausgewählte Bausteine werden dem jeweiligen Zielobjekt (IT-Systeme, Räume etc.) zugeordnet

Bei Bedarf können Bausteine im Rahmen der Modellierung modifiziert werden (z. B. Ergänzung um zusätzliche Massnahmen oder Konkretisierung von technischen Details)

Ergebnis
![[ErgebnisModellierung.png]]

### Basis-Sicherheitscheck

Der Basis-Sicherheitscheck (= IT-Grundschutz-Check) soll folgende Fragen beantworten:
* Sind die Informationen und Systeme hinreichend geschützt?
* Wenn nicht, was ist zu tun?

Vorgehen:
* Bereits umgesetzte Massnahmen mit den Empfehlungen aus dem IT Grundschutz-Kompendium vergleichen
![[BasisSicherheitsCheck.png]]
![[BasisSicherheitscheck2.png]]

Soll-Ist-Vergleich:
* Erheben des Umsetzungsstatus der einzelnen Massnahmen mithilfe von Interviews
 * Mögliche Umsetzungsstati
	 * «Entbehrlich» – benötigt immer eine Begründung!
	 * «Ja» – Massnahme vollständig umgesetzt-
	 * «Teilweise» – Einzelne Aspekte nicht umgesetzt
	 * «Nein» – Massnahme überwiegend nicht umgesetzt
* Wichtig
	* Interviews dienen auch der Sensibilisierung
	* Aussagen verifizieren, Stichproben durchführen

Ergebnis
![[ErgebnisBasisSicherheitscheck.png]]

### Risikoanalyse
Sie ist durchzuführen, wenn für einzelne Zielobjekte
* die Schutzbedarfskategorie «hoch» oder «sehr hoch» bei mindestens einem der drei Schutzziele (CIA) vorliegt
* kein geeigneter Baustein im IT-Grundschutz-Kompendium zu finden ist
* oder
* Objekte in untypischer Weise oder Einsatzumgebung betrieben werden

### Realisierungsplan
Ergebnisse sichten (fehlende Sicherheitsmassnahmen zusammenstellen)

Massnahmen konsolidieren (überflüssige Massnahmen streichen, verbleibende konkretisieren ➔ Massnahmenliste)

Aufwand schätzen (finanziell, personell / einmalig, wiederkehrend)

Umsetzungsreihenfolge festlegen (vgl. Reihenfolge der Baustein Umsetzung)

Verantwortliche und Termine bestimmen (für Realisierung und Überwachung von jeder Massnahme)

Begleitende Massnahmen festlegen (Sensibilisierung und Schulung)

Ergebnis: Realisierungsplan
![[ErgebnisRealisierungsplan.png]]

