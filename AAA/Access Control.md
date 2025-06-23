Regelt den Zugriff von Subjekten auf Objekte
Jeder Zugriffsversuch auf Objekte muss kontrolliert werden auf Zugriffsberechtigung.

* DAC (Discretionary Access Control
* RBAC (Role Based Access Control)
* MAC (Mandatory Access Control)

* TrustedComputing Base (TCB): Alle SW, HW, FW sicherheitsrelevant
* Reference monitor concept: Beziehung zwischen Subjekten und Objekten definierten Regeln folgt. Grundlage modernen Zugriffsschutzes
* Security Kernel: Eine TCB, Reference Monitor Concept implementiert

![[ReferenceMonitor.png]]

## DAC  (Discretionary Access Control)
Jedem Objekt ist ein Subjekt als Besitzer zugeordnet. Dieser ist verantwortlich für Zugriffsrechtevergabe.
Alle Zugriffsrechte werden in Zugriffskontrolllisten verwaltet.

Nachteil: Skalierbarkeit

## RBAC (Role Based Access Control)
Alle Nutzer (Subjekten) werden in Rollen eingeteilt. Jedem Objekt wird eine Liste von zugriffsberechtigten Rollen zugewiesen.
Rollenhierarchien möglich
Principle of Least Priviledge

Vorteil: Bessere Skalierbarkeit, sehr geeignet für Systeme mit grosser Anzahl Benutzer

## SRBAC (Spatial Role Based Access Control)
Ortsabhängige, rollenbasierte Zugriffskontrollstrategie
Zugriffsberechtigung zusätzlich zur Rolle noch vom Sicherheitskontext (Ort) abhängig

Vorteil: Bessere Skalierbarkeit, sehr geeignet für Systeme mit grosser Anzahl Benutzer

![[SRBAC.png]]

## MAC (Mandatory Access Control)

Systembestimmte Zugriffskontrollstrategie
Zugriffsschutz über Vertraulichkeitsstufen (Jeder Benutzer erhält Freigabe für eine Vertraulichkeitsstufe)
Basis = {Vertraulichkeitsstufen}

Regeln:
* Read-Down-Regel: Vertraulichkeitsstufe[Objekt] <= Vertraulichkeitsstufe[Subjekt]
* Write-Up-Regel: Vertraulichkeitsstufe[Objekt] >= Vertraulichkeitsstufe[Subjekt]

Nachtel: Vertraulichkeitsstufen sind statisch, bei häufig wachsenden Anforderungen zu statisch

## Multi Layer Security (Bell-LaPadula): Sensitivity Labels

> Basiert auf der Idee wie eine Organisation funktioniert. 
> Manager müssen Verantwortung durchsetzen (Daten durchsuchen), dürfen dabei aber keine Korruption begehen (keine Datenmodifikation). 
> Mitarbeiter unterhalb des Datenbesitzers müssen Datenbanken ergänzen mit Workflow Data (Datenaddition - Modifikation) aber dürfen die Datenbanken nicht durchsuchen, da sonst Firmendaten auf DatenCDs landen.
> Der Datenbesitzer darf … 

Ein Label besteht aus Klassifikationen und Kategorien:
- TOP SECRET > SECRET > CONFIDENTIAL > UNCLASSIFIED
* CORPORATE > BRANCH > DEPARTEMENT
* EYES ONLY > OFFICERS ONLY > COMPANY PROP > PUBLIC
* Aufbau der Klassifikation ist frei definierbar (Policy!!)

Die Kategorien sind nicht hierarchisch (eine Menge), z.B. Accounting, PR, Marketing, Sales, R&D
`SECRET[Accounting, Sales]`
Classification ← Categories →

Entscheidungsbaum:
1. Label von Subjekt und Objekt wird verglichen wie MAC
2. Für Read-Access: Das Subjekt muss das Objekt dominieren:
	1. Klassifikation Subjekt >= Klassifikation Objekt
	2. Kategorien des Objekts $\subseteq$ Kategorien des Subjekts
3. Für Write-Access: Das Objekt muss das Subjekt dominiern:
	1. Klassifikation Subjekt <= Klassifikation Objekt
	2. Kategorien des Subjekts $\subseteq$ Kategorien des Objekts

!! Leere Menge $\emptyset$ ist auch eine Teilmenge !! 


Abstraktes Model, kann mit Problemen verbunden sein, Blindes schreiben kann zu Integritätsproblemen führen

Labeling ist verbreitet: SELinux, Windows, verwendet zur OS-Härtung.