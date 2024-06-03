---
title: "Training W-LOI Net"
summary: "Die Methode verbessert die Wissensdestilierung, indem ein kleineres Modell den Lernprozess eines größeren Modells reguliert, was über traditionelle Lehrer-Schüler-Ansätze hinausgeht. Diese Technik kombiniert Online-Training und Konsistenzregulierung. Im PPN und der Zellsegmentierung werden genaue Positionsbestimmungen für eine zielgenaue Segmentierung genutzt, unterstützt durch spezifische Anpassungen im Lernprozess und Optimierungsstrategien gegen Übersegmentierung."
#externalUrl: ""
#showSummary: true
date: 2024-01-22
draft: false
---

## Wissenstransfer
Das Konzept des Wissenstransfers, basierend auf der Methode der Wissensdestilierung, zielt darauf ab, Wissen von einem größeren, komplexeren Modell (dem "Lehrer") auf ein kleineres, effizienteres Modell (den "Schüler") zu übertragen. Eine Evolution dieser Idee ist das Online-Model-Training, bei dem zwei Modelle gleichzeitig trainiert werden, ohne eine strikte Rollenverteilung zwischen Lehrer und Schüler festzulegen.

Die hier beschriebene Methode erweitert und modifiziert das Konzept der Wissensdestilierung weiter, indem sie ein kleineres Modell als regulativen Term im Trainingsprozess des größeren Modells einsetzt. Diese Herangehensweise differenziert sich durch die Implementierung signifikant unterschiedlicher Architekturen für die beiden Modelle. Ferner geht die Funktion des kleineren Modells über die eines herkömmlichen Schülermodells hinaus, indem es aktiv zur Regulierung und Beschränkung des Suchraums des größeren Modells beiträgt.

Diese Methode vereint die Konzepte des Online-Model-Trainings und der Consistency-Regularization, um eine effiziente und effektive Lernumgebung zu schaffen, die die Vorteile beider Ansätze nutzt: die Flexibilität und Effizienz des Wissenstransfers zwischen unterschiedlich konzipierten Modellen sowie die Stärkung der Lernprozesse durch die Einführung eines regulativen Elements.

---

### Überblick über das Position-Proposal-Network (PPN) und die Zellsegmentierung

- Das PPN-Modell verwendet zwei Tensoren, um präzise Positionsvorschläge und Verschiebungen zu generieren.
- Zusätzliche Tensoren repräsentieren die Ground-Truth-Bewertungen und -Verschiebungen.
- Der Verlust im PPN-Modell kombiniert verschiedene Loss-Funktionen, um eine effiziente und genaue Positionierung und Segmentierung zu ermöglichen.
- Die Segmentierung nutzt die hochauflösenden Eigenschaften des Bildes für eine effiziente Verarbeitung.
- Durch das gezielte Aufheben der Translationsinvarianz von CNNs mittels Integration spezifischer Positionsdaten wird die Genauigkeit der Segmentierung einzelner Zellen basierend auf ihrer genauen Lage im Bild signifikant verbessert.

---

![Alt text](images/Semi-Supervised.png)
### Lernprozess, Semantische Segmentierung und Optimierung

#### Lernmechanismen und Segmentierung
- Das Hauptmodell adaptiert semantische Segmentierungen vom Auxnet durch Berechnung der maximalen Logits der Instanzsegmentierungen an jedem Pixel.

#### Wahrscheinlichkeitsumwandlung und Integration von Vorwissen
- Die Anwendung einer Sigmoid-Funktion ermöglicht die Transformation der Logits in Wahrscheinlichkeiten, wobei zweidimensionale Verteilungen zusätzliches Vorwissen über die Instanzgrößen integrieren.

#### Optimierungsstrategien
- Anstelle des Cross-Entropy-Loss wird für das Auxnet ein linearer Loss genutzt, der weiche Labels ohne feste 0 oder 1 Werte effektiver handhabt.

### Anpassungsreaktionen und Übersegmentierungsvermeidung

#### Anpassung an die Vorhersagesicherheit
- Die Loss-Funktion des Modells passt sich der Sicherheit der Vorhersagen an, mit verstärkten Reaktionen bei hohen Sicherheitsgraden und abgeschwächten bei Unsicherheit.

#### Strategien gegen Übersegmentierung
- Eine spezielle Loss-Funktion fördert die Übereinstimmung der Segmentierung einzelner Instanzen mit der Gesamtsegmentierung und bestraft Überlappungen, um Übersegmentierung zu verhindern.

### Zellränder und Modellaktualisierung

#### Wissenstransfer für Zellränder
- Zur Vorhersage von Zellrändern wird ein Sobel-Filter eingesetzt, der die segmentierten Vordergründe in Ränder umwandelt.

#### Trainings- und Aktualisierungsprozess
- Beide Modelle aktualisieren sich durch Standard-Gradientenabstieg, wobei sie unterschiedliche Loss-Funktionen für das Hauptmodell und das Auxnet anwenden, um die Trainingseffizienz zu optimieren.

#### Vereinfachte Visualisierung
![Alt text](images/Training_vis_extra.png)
