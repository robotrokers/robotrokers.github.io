---
layout: post
title: Introduzione alla robotica teorica
subtitle: Catene cinematiche
date: 2016-06-019 15:17:00
author: Basilio Bona
categories: Teorica
---



# Catena Cinematica

In questo post descrivo le catene cinematiche, che sono una rappresentazione astratta dei bracci robotici.
Dopo sarà possibile discutere le funzioni cinematiche dirette e inverse, cosa che farò in uno dei prossimi post. 

Per ragioni di spazio mi limito a considerare la classe dei robot industriali, lasciando da parte i robot umanoidi o su zampe, anche se i concetti evidenziati qui si possono applicare anche a queste categorie di robot.

Una **catena cinematica** rappresenta un modello astratto della geometria di un robot fisico e quindi introduce qualche ipotesi semplificativa.

La prima ipotesi è che ogni parte della catena cinematica sia perfettamente rigida. La rigidezza perfetta non esiste in natura, ma nel nostro caso la diamo per scontata.

La seconda ipotesi è che sul moto delle varie parti della catena cinematica non agiscano forze di attrito di alcun genere.

La terza ipotesi è che il moto della catena cinematica sia generato in modo astratto; cioè per ora non viene introdotto alcun tipo di motore. La relazione che le forze/coppie applicate alle masse hanno con la generazione del moto della catena cinematica (e viceversa) sarà descritta in futuro quando parleremo del **modello dinamico** del manipolatore.

La studio delle catene cinematiche fa riferimento quindi alle sole grandezze cinematiche, che sono le posizioni, le velocità e le accelerazioni delle varie parti della catena, prescindendo come detto dall'effetto di forze/coppie interne o applicate dall'esterno.

Detto ciò,  una **catena cinematica** è composta da un certo numero di bracci (in inglese *arms* o *links*), ipotizzati privi di massa e, come detto, perfettamente rigidi, collegati tra loro tramite giunti (in inglese *joints*), anch'essi privi di massa, perfettamente rigidi, su cui non agiscono forze/coppie di attrito. 

Il movimento della catena cinematica è reso possibile dalla presenza dei giunti, che permettono un moto relativo tra i bracci ad esso collegati.  

I giunti che considero sono solo di due tipi, 

 1. di **rotazione** o **rotoidali**
 2. di **traslazione** o **prismatici**

illustrati schematicamente nella figura seguente.

![](http://i.imgur.com/UVpr5mu.png)

Qui sotto invece è illustrato un tratto di catena cinematica con un braccio e due giunti rotoidali. Come potete osservare, il braccio è rappresentato da un semplice segmento, supposto privo di massa, come pure sono privi di massa i giunti.

![](http://i.imgur.com/WvCPcAl.png)

## Giunto di rotazione ##

Il giunto di rotazione permette un movimento di rotazione intorno ad un asse, detto **asse di rotazione** o **asse del moto**, ottenendo di modificare l'angolo tra il braccio a monte del giunto e quello a valle .

Esistono anche giunti che permettono una rotazione contemporanea intorno a più assi, come succede, ad esempio, in un joystick, ma non saranno mai considerati nella presente descrizione delle catene cinematiche.

Poiché spesso si devono disegnare le catene cinematiche senza aggiungere troppi particolari, si usano rappresentazioni semplificate sia in 3D sia in 2D. Purtroppo la rappresentazione di solito avviene sulla superficie piana di un disegno e quindi bisogna rappresentare la catena in prospettiva.

I giunti di rotazione si rappresentano in 3D come dei cilindri in assonometria ortogonale, orientati secondo la prospettiva desiderata. Nel disegno sottostante si deve immaginare che l'asse $x$ sia orizzontale, l'asse $y$ verticale e l'asse $z$ esca dal piano verso l'osservatore. Le frecce curve indicano il verso positivo del moto angolare, secondo una convenzione che chiariremo in seguito.

![](http://i.imgur.com/SmCjpO0.png)

Qui sotto invece è illustrata la rappresentazione grafica in 2D, dove i giunti hanno rappresentazioni diverse a seconda del punto di vista (da sopra o di lato) e corrispondono a cerchi oppure a due triangoli affacciati ad un vertice

![](http://i.imgur.com/dROwFhk.png)

L'asse $z$ nella vista 2D è convenzionalmente quello normale al piano del disegno e può essere indicato con un pallino dentro un cerchio per indicare che "esce" dal piano e il verso positivo dell'angolo è antiorario, mentre si usa una X dentro un cerchio per indicare che "entra" nel piano e il verso positivo è orario. Torneremo più avanti a precisare come determinare il verso di rotazione a seconda del segno dell'angolo, utilizzando la "regola della mano destra" che penso sia nota a tutti voi.

## Giunto di traslazione ##

Il giunto di traslazione, detto anche giunto **prismatico**, introduce una traslazione lungo un solo asse, detto asse di traslazione o asse del moto, permettendo così ai bracci collegati a monte e a valle di modificare la loro distanza relativa.

I  giunti prismatici si rappresentano in 3D con dei cubi o parallelepipedi attraversati da un segmento che rappresenta l'asse di traslazione. 

***

METTERE FIGURA
--------------

***

Esistono anche giunti che permettono una combinazione di traslazioni e rotazioni intorno a più assi come, ad esempio, in un giunto elicoidale, ma nella descrizione delle catene cinematiche non è necessario introdurli.

## Catene aperte e catene chiuse ##

Convenzionalmente il basamento su cui si fissa il manipolatore è detto braccio zero (un po' come la terra nei circuiti elettronici) a cui fa seguito il giunto 1, il braccio 1, il giunto 2, e così via fino al braccio terminale, detto braccio $n$ che ha il compito di portare l'attrezzo o la pinza. 

La **catena cinematica aperta** è quella in cui non ci sono circuiti che si rinchiudono su sé stessi, ossia il braccio $n$ non è collegato a nessun giunto "a valle", mentre una **catena cinematica chiusa** è quella in cui l'ultimo braccio è collegato al primo giunto, o anche a uno intermedio; si ha perciò un circuito chiuso bracci-giunti.

Nella figura che segue sono illustrati i due tipi di catena cinematica

![](http://i.imgur.com/hGr7MbC.png)
Catena cinematica aperta

![](http://i.imgur.com/ukxJXaq.png)
Catena cinematica chiusa

Esistono anche delle catene cinematiche dette a bracci paralleli che sono anche note come piattaforme di Stewart. Sono composte da 6 giunti prismatici collegati a coppie a tre punti di una piasta che sorregge l'attrezzo. Vengono utilizzate per quei movimenti che devono avvenire a grande velocità, ma in un volume di lavoro non troppo grande. Alcune stampanti 3D sono basate su questo tipo di catena cinematica.

![](http://i.imgur.com/Dy3BjHs.png)

Piattaforma di Stewart

![](http://i.imgur.com/10fkZI0.png)
