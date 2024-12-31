---
title: "Mein erster H5P Content Type"
date: "2023-01-16"

type: post
author: asbl
image: /images/h5p-ide/1.png
categories:
  - Informatik
  - miniworldmaker
tags:
  - Informatik
  - Moodle
  - H5P
---

Manchmal ist es einfach ein gutes Gefühl, Projekte abzuschließen - Sofern man beim Programmieren vom "Abschließen" sprechen kann.

Nachdem ich gestern eine größere Version vom miniworldmaker committed habe, folgt nun die erste Alpha meines ersten H5P-Plugins, genauer gesagt meiner Sammlung an H5P Plugins.

Das Plugin `H5P-content-python-ide` ist für mich zunächst das wichtigste. Es erlaubt es einen einfachen Python-Editor (mit Turtle-Grafik! mit processing über p5js!) per H5P einzubinden, z.B. in ein beliebiges Moodle.

![Screenshot 1](images/h5p-ide/1.png)

Dabei habe ich verschiedene Plugins geschrieben, die Teilarbeiten übernehmen: 

  * `H5P-lib-skulpt` kommuniziert mit der Javascript-Bibliothek Skulpt, welche Python einbinden.
  * `H5P-lib-markdown` rendert Markdown (Da der Editor kein code-Tag erlaubt, musste ich mir so behelfen)
  * `H5P-lib-ace` stellt den Editor und ggf. Buttons dar.

![Screenshot 1](images/h5p-ide/2.png)

Wie man vielleicht sieht ist dies ein Projekt, welches einige Wochen in Anspruch genommen hat.

Den Quellcodefindet man [hier](https://codeberg.org/a_siebel/h5p-content-python-ide) und [hier](https://codeberg.org/a_siebel/h5p-content-python-ide/releases) die H5P-Datei zum Einbinden in Moodle

Jetzt läuft der Editor aber in unserem Moodle und ich bin froh, dieses Projekt abgeschlossen zu haben.

Ein weiteres H5P-Plugin steht in den Startlöchern: [H5P-lib-python-question](https://codeberg.org/a_siebel/h5p-content-python-question) überprüft Eingaben mit Hilfe von Testcases - Prinzipiell ist auch dieses Plugin "fertig", erfordert aber noch einige Tests, bis ich es als wirklich fertig und stabil bezeichnen würde.

![Screenshot 1](images/h5p-question/1.png)

![Screenshot 1](images/h5p-question/2.png)

Ein paar Ideen gibt es auch schon zur Weiterentwicklung - Entsprechende Ideen habe ich mir offen gehalten: Ich überlege auch weitere Sprachen, z.B. SQL einzubinden. Das Grundgerüst steht und ich habe an verschiedenen Stellen die Schnittstellen bereits so entwickelt, dass auch eine weitere Bibliothek angeschlossen werden kann.


Zunächst muss ich mich aber erstmal wieder anderen Projekten widmen...

(An der Stelle auch ein Dank an M Degrange, er etwas ähnliches bereits programmiert hatte. Ich habe einige Ideen seiner Implementierung wieder aufgegriffen.)