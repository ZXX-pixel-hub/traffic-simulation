# Traffic Simulation with Monte Carlo

## Projektbeschreibung
.
In diesem Projekt wird eine vereinfachte eindimensionale Verkehrssimulation in Python
implementiert. Jede Simulation repräsentiert ein mögliches Verkehrsszenario mit zufälligen
Anfangsbedingungen, insbesondere zufällig initialisierten Fahrzeuggeschwindigkeiten.

Mithilfe eines Monte-Carlo-Ansatzes wird die Simulation viele Male wiederholt, um den
Erwartungswert der durchschnittlichen Fahrzeuggeschwindigkeit zu schätzen und die
statistische Unsicherheit dieser Schätzung anhand von Standardfehlern und
Konfidenzintervallen zu quantifizieren.

Der Fokus des Projekts liegt auf Monte-Carlo-Methoden und Unsicherheitsanalyse im Rahmen
des Moduls „Simulationstools“. Eine realistische Modellierung von Fahrzeuginteraktionen
oder expliziter Stauentstehung ist bewusst nicht Teil des Modells.

---

## Repository-Inhalt

- `traffic-simulation.ipynb`  
  Jupyter Notebook mit der Implementierung der Verkehrssimulation, dem Monte-Carlo-
  Experiment sowie der Sensitivitätsanalyse.

- `README.md`  
  Projektbeschreibung und Überblick.

- `requirements.txt`  
  Liste der benötigten Python-Bibliotheken.

---

## Voraussetzungen

- Python 3.x
- numpy
- matplotlib
 
---
## Installation

```bash
pip install -r requirements.txt

—-
```
## Ausführung

Das Projekt wird vollständig über das Jupyter Notebook ausgeführt.

1.	Notebook traffic-simulation.ipynb öffnen
2.	Alle Zellen der Reihe nach ausführen

Dabei werden:
	•	Monte-Carlo-Simulationen durchgeführt
	•	Erwartungswert und Standardfehler berechnet
	•	Konfidenzintervalle bestimmt
	•	Grafiken zur Ergebnisverteilung und Sensitivitätsanalyse erzeugt

—-

## Modulkontext

Dieses Projekt wurde im Rahmen des Moduls Simulationstools erstellt und demonstriert
die Anwendung von Monte-Carlo-Methoden zur Schätzung von Erwartungswerten sowie zur
Quantifizierung von Unsicherheiten in stochastischen Modellen.

## Ergebnisse & Visualisierung

Das Notebook erzeugt unter anderem:
	•	Ein Histogramm der durchschnittlichen Fahrzeuggeschwindigkeiten aus dem
Monte-Carlo-Experiment inklusive Mittelwert und Konfidenzintervall
	•	Eine Sensitivitätsanalyse der mittleren Geschwindigkeit in Abhängigkeit von der Anzahl
der Fahrzeuge

Diese Grafiken werden im Report verwendet.
