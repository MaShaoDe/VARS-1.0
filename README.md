# VARS – Vehicle Attitude Reference System

VARS ist ein ESP32-basiertes, farbiges Cockpit-Display zur Anzeige der Fahrzeuglage (Roll und Pitch).
Es richtet sich an Camper Vans und ähnliche Fahrzeugprojekte und unterstützt das ruhige Ausrichten des Fahrzeugs im Stand.

Der Fokus liegt auf klarer Geometrie, stabiler Darstellung und defensiver Warnlogik für Parkieren und Schlafkomfort.

VARS ist ein DIY-Open-Source-Projekt und nicht für sicherheitskritische oder zertifizierungspflichtige Anwendungen gedacht.

## Projektstatus

Status: Phase 1a Core  
Implementierung in Arbeit  
Nicht produktiv  
Nicht zertifiziert  

## Ziel des Projekts

VARS zeigt Roll und Pitch in Echtzeit als künstlichen Horizont auf einem Farbdisplay.
Im Parkmodus unterstützt das System das Ausrichten des Fahrzeugs und liefert eine visuelle Einschätzung von Komfort und Sicherheit.

Schwerpunkte:
- ruhige, stabile Anzeige im realen Fahrzeugumfeld
- klare Trennung von Normalbetrieb und Parkmodus
- explizite Kalibrierung durch den Nutzer
- defensive, nachbarschaftstaugliche Warnlogik

## Nicht-Ziele und Abgrenzung

VARS ist kein Ersatz für:
- professionelle Fahrzeugmesstechnik
- Flug- oder Fahrzeugavionik
- sicherheitskritische Assistenzsysteme

Das Projekt dient der Orientierung, dem Komfort und der experimentellen Erweiterung im DIY-Umfeld.

## Technischer Rahmen

Zielplattform:
- ESP32

Sensorik:
- Eine IMU mit integrierter Sensorfusion
- Roll und Pitch als zentrale Grössen

Anzeige:
- Farbdisplay, bevorzugt TFT
- Fokus auf Geometrie und Farbe statt Zahlen

Toolchain:
- PlatformIO als Referenz
- Arduino IDE optional, nicht der empfohlene Entwicklungsweg

## Designprinzipien

- Eine Wahrheit für die Lage
- Ruhige Anzeige durch Filter und Deadband
- Keine automatischen Überraschungen
- Warnungen nur im expliziten Parkmodus
- Audio standardmässig AUS
- Erweiterbar ohne Umbau

## Betriebsmodi

Normalmodus  
Anzeige von Roll und Pitch ohne aktive Warnungen. Kein Audio.

Parkmodus  
Explizit aktivierbar.  
Farbige Neigungszonen für Komfort- und Sicherheitsbewertung.  
Optionale Audioausgabe, immer manuell aktiviert.

## Kalibrierung

Kalibrierung erfolgt explizit durch den Nutzer in gewünschter Referenzlage.
Roll- und Pitch-Offsets werden persistent gespeichert.
Es gibt keine automatische Kalibrierung.

## Warnlogik

Warnungen sind ausschliesslich im Parkmodus aktiv.
Alle Grenzwerte arbeiten mit Mindestdauer, Hysterese und Cooldown.
Akustische Warnungen sind optional und werden beim Verlassen des Parkmodus immer deaktiviert.

## Projektstruktur

Empfohlene Repository-Struktur:

- README.md  
  Projektübersicht und Einstiegspunkt

- docs/  
  Konzept, Kalibrierung, Parkmodus, Warnlogik und Testplan

- firmware/  
  Quellcode des ESP32-Systems, modular aufgebaut

- assets/  
  Screenshots, UI-Mockups und visuelle Referenzen

- hardware/  
  Optional: Schaltpläne, Gehäuse, PCB-Dateien

## Roadmap

Aktuelle Phase: Phase 1a Core

Enthalten:
- ESP32 als Zielplattform
- Eine zentrale IMU
- Roll- und Pitch-Berechnung
- Künstlicher Horizont
- Fixes Fahrzeug-Referenzsymbol
- Manuelle Kalibrierung

Nicht enthalten:
- GPS oder Navigation
- Parkmodus-Warnlogik
- Audioausgabe
- Touchbedienung
- Zweitdisplay

## Getting Started

VARS richtet sich an Anwenderinnen und Anwender mit Grundkenntnissen in Embedded-Systemen.

Grundannahmen:
- ESP32-basierte Hardware
- IMU mit Sensorfusion
- Farbdisplay
- Entwicklung unter macOS oder Linux

Eine detaillierte Anleitung folgt nach Stabilisierung der Core-Funktionen.

## Safety and Disclaimer

VARS ist ein nicht zertifiziertes DIY-System.
Es ist nicht für sicherheitskritische Anwendungen vorgesehen.
Die Nutzung erfolgt vollständig auf eigene Verantwortung.

## Contributing

Beiträge sind willkommen.
Bitte Pull Requests klar halten, Konfiguration zentralisieren und Diskussionen über Issues führen.

## License

BSD 2-Clause License  
Siehe LICENSE Datei.
