---
title: "Analyse des W-LOI Netzwerks"
summary: "Hier werden die Ergebnisse auf den verschiedenen Datensätzen analysiert und verglichen. Auch werden verschiedene Ablationen durchgeführt, um die Wichtigkeit der einzelnen Komponenten zu untersuchen."
#externalUrl: ""
#showSummary: true
date: 2024-01-20
draft: false
---

## Ergebnisse
### LIVECell
![Alt text](images/LIVECell.png)
In der vorliegenden Studie werden diverse maschinelle Lernmodelle anhand des LIVECell-Datensatzes evaluiert, einem der umfangreichsten annotierten Zelldatensätze, der acht unterschiedliche Zelllinien mit insgesamt etwa 1,6 Millionen Zellen umfasst.

Die Modelle von Nishimura et al. [1] und Qu et al. [2] repräsentieren aktuelle weakly-supervised Ansätze in diesem Forschungsfeld, während das Modell von Edlund et al. [3] als fully-supervised Benchmark dient.

Die Überlegenheit unserer Modelle W-LOI 1 und W-LOI 2 im Vergleich zu anderen weakly-supervised Modellen ist offensichtlich, da sie durchgängig bessere Ergebnisse liefern. Darüber hinaus erreichen unsere Modelle häufig Leistungen, die mit dem fully-supervised Ansatz von Edlund et al. vergleichbar oder sogar überlegen sind. Die Unterschiede zwischen W-LOI 1 und W-LOI 2 sind auf die jeweiligen Trainingsbedingungen zurückzuführen: W-LOI 1 wurde ausschließlich mit dem LIVECell-Datensatz trainiert, während W-LOI 2 zusätzlich mit Daten aus dem TissueNet-Datensatz vortrainiert wurde, was dessen Leistungsstärke weiter erhöht.

---

### TissueNet

---
[1] Kazuya Nishimura, Ryoma Bise. https://ieeexplore.ieee.org/document/10030481

[2] Hui Qu, Pengxiang Wu, Qiaoying Huang, Jingru Yi, Zhennan Yan, Kang Li, Gregory M Riedlinger, Subhajyoti De, Shaoting Zhang, Dimitris N Metaxas. https://pubmed.ncbi.nlm.nih.gov/32746112/


[3] Christoffer Edlund, Timothy R Jackson, Nabeel Khalid, Nicola Bevan, Timothy Dale, Andreas Dengel, Sheraz Ahmed, Johan Trygg, Rickard Sjögren. https://pubmed.ncbi.nlm.nih.gov/34462594/
