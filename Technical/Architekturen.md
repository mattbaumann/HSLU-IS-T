# Client-Server
Server steht im Zentrum und wird von Clients zugegriffen, 90er Jahre, 2-Tier Architektur

Vorteile:
	* Client einfach implementierbar
	* Einfache Architektur mit klaren Verantwortlichkeiten

Nachteile:
	* Wartung des Clients ist komplex, neue Releases müssen auf allen Clients ausgerollt werden
	* Abhängigkeit der Applikation vom Setup des Clients

## Multitier Architektur
Unterteilung in 3 Schichten (1) Datenschicht (2) Logikschicht, Businesslogik, Application (3) Präsentationsschicht, keine Businesslogik, Webbrowser, FAT-Client

Kommunikationsprotokolle: SOAP, RMI, Corba, .net

Vorteile:
* Gutes GUI
* Zentrale Installation der Businesslogik
* Effizient und gut Skalierbar
* Unterschiedliche Clients unterstützt

Nachteile: Komplexer Aufbau, Entwicklung, Betrieb

## Terminal Server Achitektur
GUI wird auf Server generiert und durch Client bloss angezeigt

Motivation:
* Zentrale Installation der Client-Applikation
* Remote-Zugriff auf Server
* Fernzugriff auf Firmen-Infra

Implementationen: Bildschirmübertragung (RDC, Citrix, X+SSH), Client ist Applikationsinhalt-Viewer

Applikationsinstallation auf Server, Thin-Client am Arbeitsplatz, nur Graphikinfo übertragen. Arbeitsplatz-Integration bei grösseren Firmen, Outsourcing von Mitarbeitern, Zugang für externe Mitarbeiter

## Virtualisierung
HW wird über Virtualiser für das OS abstrahiert. OS sieht standardisierte HW. Mehrere OS auf einer HW.

Gute Performance, HW-/SW-Unterstützung und OS, Zusatzfunktionen wie Snapshotting, Clustering, Moving, High Availability

Einsatzbereiche: (1) Serverkonsolidierung in RZ, Test-Konfig in DEV, Desktop-Virtualization

