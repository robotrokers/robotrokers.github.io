---
layout: post
title:  Matrici e vettori
subtitle: Le basi matematiche della cinematica dei robot
date: 2017-07-10 00:00:00
author: Basilio Bona
categories: Teorica
---

# Matrici e vettori

Cari affezionatissimi lettori, forse questo post risulterà alla fine un po' indigesto, ma vi chiedo di essere pazienti, perché un digestivo non basta.

Da parte mia farò il possibile per essere chiaro e spiegare le ragioni per cui introduco certi concetti e insisto su questo o quel particolare. Non sono un sadico, ma se volete essere a conoscenza degli intimi segreti della robotica, dovrete fare un piccolo sforzo 

Infatti, per capire la **cinematica inversa** dei robot, soprattutto quelli industriali, è necessario prima capire che cos'è la **cinematica diretta**, ma per capire come scrivere le equazioni della cinematica diretta, occorre conoscere tre cose:

 1. Cosa sono i **vettori**, ma, soprattutto come si usano e come si devono interpretare. Forse pensate che sia tempo perso, perché sapete già tutto, ma vi assicuro che la mia esperienza di insegnamento ultra trentennale mi fa dire che così non è ... e poi ci sono i **quaternioni** alla fine del percorso ... yum yum!
 
 2. Cosa sono e come si usano le **matrici di rotazione**.  Anche tutti gli altri tipi di matrice sono importanti, ma in robotica le matrici di rotazione sono un must, un po' come per uno chef saper fare un riso al burro (o all'olio se siete vegani)
 
 3.  Le basi della **trigonometria**. Basta ricordarsi cosa sono seni e coseni degli angoli, e poco altro.

Incominciamo dai vettori

## Vettori, questi (s)conosciuti

### Quel che i vettori sono

I vettori sono astrazioni matematiche, oggetti scaturiti dalla mente dei matematici/fisici/ingegneri/ecc. dopo un lungo periodo di gestazione e una crescita, a tratti tormentata, nel corso del XIX secolo.

Per chi fosse interessato ad una storia del concetto di vettore, consiglio l'interessante libro di Michael J. Crowe intitolato "A History of Vector Analysis" del 1967 

![](http://i.imgur.com/EwuITji.png)

e poi, dello stesso autore, un breve intervento che potrete trovare [qui](http://worrydream.com/refs/Crowe-HistoryOfVectorAnalysis.pdf). 

Anche la [voce corrispondente](https://en.wikipedia.org/wiki/A_History_of_Vector_Analysis) su Wikipedia (purtroppo solo in inglese) merita di essere letta.

### Quel che i vettori non sono

**I vettori non sono delle frecce!** Le frecce, che ormai tutti conoscono e usano, sono delle semplici **icone**, utilizzate per riassumere delle proprietà, che però vanno capite e utilizzate correttamente. E' un po' come dire che gli atomi non sono dei sistemi solari in miniatura e le molecole non sono delle palle collegate da segmenti.

A proposito di icone, ecco un altro libro interessante: "Icons and Symmetries" di  Simon L. Altmann, pubblicato nel 1992, da cui ho tratto qualche utile insegnamento.

Adesso basta con i libri di storia e affrontiamo l'argomento
