---
title: "Slides with Jupyter"
date: "2022-02-03"
publishdate: "2022-02-03"
type: post
author: asbl
image: /images/jupyter1.png
categories:
  - Mathematik
tags:
  - Mathematik
---

[Jupyter Notebooks](https://jupyter.org/install) kann man hervorragend nutzen um damit Folien zu erstellen. Man benötigt dafür das Plugin [RISE](https://github.com/damianavila/RISE)

Unter Manjaro kann man beides direkt aus dem Paket-Manager installieren. 

Unter Windows kann jupyter am besten aus der WSL heraus intalliert werden. Dann kann man jupyter mit folgenden Schritten starten:

1. Installiere jupyter mit `sudo apt install jupyter-core`

2. Installiere RISE mit `pip install RISE`

3. Starte jupyter mit 'python -m notebook' im Verzeichnis in dem die Folien liegen.

Wie man RISE benutzt kannst du [hier](https://janakiev.com/blog/creating-slides-with-jupyter-notebook/) nachlesen.

So sehen z.B. meine Folien in der Jupyter-Übersicht aus.

![Jupyter](/images/jupyter1.png)

...und so sehen meine Folien aus:

![Jupyter](/images/jupyter2.png)

Code kann darin direkt ausgeführt werden. [Hier](https://codeberg.org/a_siebel/flask-workshop) kann man dies in den ersten Folien auch in Bewergung sehen.