<head>
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
</head>

---
layout: post
title: Introduzione alla robotica teorica
subtitle: Catene cinematiche
date: 2016-06-019 15:17:00
author: Basilio Bona
categories: Teorica
---



# Catene Cinematiche

In questo post descrivo le catene cinematiche, che sono una rappresentazione astratta dei bracci robotici.
Successivamente sarà possibile discutere le funzioni cinematiche dirette e inverse, cosa che farò in uno dei prossimi post. 

Per ragioni di spazio mi limito a considerare la classe dei robot industriali, tralasciando i robot umanoidi o quelli su zampe, anche se i concetti evidenziati qui si possono applicare a queste categorie di robot.

Una **catena cinematica** rappresenta in sintesi un modello astratto della geometria di un robot fisico e nel fare ciò si introducono alcune ipotesi semplificative.

La prima ipotesi è che ogni parte della catena cinematica sia perfettamente rigida. La rigidezza perfetta non esiste in natura, ma nel nostro caso la diamo per scontata.

La seconda ipotesi è che sul moto delle varie parti della catena cinematica non agiscano forze di attrito di alcun genere.

La terza ipotesi è che il moto della catena cinematica sia generato in modo astratto; cioè per ora non viene introdotto alcun tipo di motore o azionatore. La relazione che le forze/coppie applicate alle masse hanno con la generazione del moto della catena cinematica (e viceversa) sarà descritta in futuro quando parleremo del **modello dinamico** del manipolatore.

La studio delle catene cinematiche fa riferimento quindi alle sole grandezze cinematiche, che sono le posizioni, le velocità e le accelerazioni delle varie parti della catena, prescindendo come detto dall'effetto di forze/coppie interne o applicate dall'esterno.

Detto ciò,  una **catena cinematica** è composta da un certo numero di bracci (in inglese *arms* o *links*), ipotizzati privi di massa e, come detto, perfettamente rigidi, collegati tra loro tramite giunti (in inglese *joints*), anch'essi privi di massa, perfettamente rigidi, su cui non agiscono forze/coppie di attrito. 

Il movimento della catena cinematica è reso possibile dalla presenza dei giunti, che permettono un moto relativo tra i bracci ad esso collegati.  

I giunti che considero in questa trattazione sono solo di due tipi, 

 1. di **rotazione** o **rotoidali**
 2. di **traslazione** o **prismatici**

illustrati schematicamente nella figura seguente.

![](http://i.imgur.com/UVpr5mu.png)

Qui sotto invece è illustrato un tratto di catena cinematica con un braccio e due giunti rotoidali. Come potete osservare, il braccio è rappresentato da un semplice segmento, supposto privo di massa, come pure sono privi di massa i giunti.

![](http://i.imgur.com/WvCPcAl.png)

## Giunto di rotazione ##

Il giunto di rotazione permette un movimento di rotazione intorno ad un asse, detto **asse di rotazione** o **asse del moto**, che consente di modificare l'angolo tra il braccio a monte del giunto e quello a valle .

Poiché spesso si devono disegnare le catene cinematiche senza aggiungere troppi particolari, si usano rappresentazioni semplificate sia in 3D sia in 2D. Purtroppo la rappresentazione di solito avviene sulla superficie piana di un disegno e quindi bisogna rappresentare la catena in prospettiva.

I giunti di rotazione si rappresentano in 3D come dei cilindri in assonometria ortogonale, orientati secondo la prospettiva desiderata. Nel disegno sottostante si deve immaginare che l'asse $x$ sia orizzontale, l'asse $y$ verticale e l'asse $z$ esca dal piano verso l'osservatore. Le frecce curve indicano il verso positivo del moto angolare, secondo una convenzione che chiariremo in seguito.

![](http://i.imgur.com/SmCjpO0.png)

Qui sotto invece è illustrata la rappresentazione grafica in 2D, dove i giunti hanno rappresentazioni diverse a seconda del punto di vista (da sopra o di lato) e corrispondono a cerchi oppure a due triangoli affacciati ad un vertice

![](http://i.imgur.com/dROwFhk.png)

L'asse $z$ nella vista 2D è convenzionalmente quello normale al piano del disegno e può essere indicato con un pallino dentro un cerchio per indicare che "esce" dal piano e il verso positivo dell'angolo è antiorario, mentre si usa una X dentro un cerchio per indicare che "entra" nel piano e il verso positivo è orario. Torneremo più avanti a precisare come determinare il verso di rotazione a seconda del segno dell'angolo, utilizzando la "regola della mano destra" che penso sia nota a tutti voi.

## Giunto di traslazione

Il giunto di traslazione, detto anche giunto **prismatico**, introduce una traslazione lungo un solo asse, detto asse di traslazione o asse del moto, permettendo così ai bracci collegati a monte e a valle di modificare la loro distanza relativa.

I  giunti prismatici si rappresentano in 3D con dei cubi o parallelepipedi attraversati da un segmento che rappresenta l'asse di traslazione. 

![](http://i.imgur.com/o8AMZj7.png)

Nella figura a) rappresenta un giunto con asse di traslazione lungo l’asse $z$ normale al foglio, b)  un giunto con asse di traslazione lungo l’asse $x$ e assi colineari; c) un giunto con asse di traslazione lungo l’asse $x$,  e assi ortogonali; d) un giunto con asse di traslazione lungo l’asse $y$ (assi colineari); e) un giunto con asse di traslazione lungo l’asse $y$ (assi ortogonali).

Esistono anche giunti che permettono una combinazione di traslazioni e rotazioni intorno a più assi come, ad esempio, in un giunto elicoidale, ma nella descrizione delle catene cinematiche non è necessario introdurli.

## Gradi di movimento

Esistono anche giunti che permettono una rotazione contemporanea intorno a più assi, come succede, ad esempio, in un joystick, oppure che permettono rotazioni e traslazioni contemporanee, come nel movimento di una vite elicoidale, ma questi non verranno introdotti nella presente descrizione delle catene cinematiche.

I giunti che consideriamo hanno un solo **grado di movimento** proprio perché permettono o una rotazione intorno ad un singolo asse o una traslazione lungo un singolo asse.

## Catene aperte e catene chiuse 
Convenzionalmente il basamento su cui si fissa il manipolatore è detto braccio zero (un po' come la terra nei circuiti elettronici) a cui fa seguito il giunto 1, il braccio 1, il giunto 2, e così via fino al braccio terminale, detto braccio $n$ che ha il compito di portare l'attrezzo o la pinza. 

La **catena cinematica aperta** è quella in cui non ci sono circuiti che si rinchiudono su sé stessi, ossia  ogni braccio è collegato ad un solo altro braccio a monte e a valle, salvo il primo, che non ha bracci a monte (tranne il braccio zero) e l’ultimo, che non ha bracci a valle; nel secondo caso qualche braccio può essere collegato a pi`u di un braccio a monte e/o a valle, mentre una **catena cinematica chiusa** è quella in cui qualche braccio può essere collegato a più di un braccio a monte e/o a valle

Nella figura che segue sono illustrati i due tipi di catena cinematica

![](http://i.imgur.com/hGr7MbC.png)
Catena cinematica aperta

![](http://i.imgur.com/ukxJXaq.png)
Catena cinematica chiusa

Esistono anche delle catene cinematiche dette a bracci paralleli che sono anche note come piattaforme di Stewart. Sono composte da 6 giunti prismatici collegati a coppie a tre punti di una piasta che sorregge l'attrezzo. Vengono utilizzate per quei movimenti che devono avvenire a grande velocità, ma in un volume di lavoro non troppo grande. Alcune stampanti 3D sono basate su questo tipo di catena cinematica.

![](http://i.imgur.com/Dy3BjHs.png)

Piattaforma di Stewart

![](http://i.imgur.com/10fkZI0.png)

Nelle catene aperte è consuetudine descrivere la catena con una lista di simboli, dove R rappresenta un giunto rotoidale e P un giunto prismatico, a partire dalla base fino alla punta. 

Nell'immagine seguente è schematizzata una catena aperta, descritta come R-R-P-R-R-R-R e detta anche 2R-1P-4R, in quanto ci sono 2 giunti di rotazione, quindi 1 giunto prismatico che è seguito da 4 giunti di rotazione. La catena ha perciò  7 gradi di movimento, o meglio. il grado di movimento è 7.

![](http://i.imgur.com/sr5WHbS.png)

## Spazio di lavoro

Si chiama **spazio di lavoro** del manipolatore il volume di spazio raggiungibile dalla punta operativa, per ogni possibile movimento dei giunti, date la forma e le caratteristiche geometriche dei bracci. 

Lo spazio di lavoro è quindi formalmente deﬁnibile come un sottoinsieme dello "spazio cartesiano", cioè lo spazio tridimensionale in cui tutti noi operiamo.

![](http://i.imgur.com/cRCWI8S.png)

Nello spazio di lavoro vengono deﬁniti un certo numero di sistemi di riferimento cartesiani; ad esempio: il riferimento alla base del robot, il riferimento locale della ﬂangia porta-attrezzo, il riferimento locale del pezzo da manipolare o dell’attrezzo. Tra questi si sceglie il sistema di riferimento principale, ad esempio quello alla base del robot, e si dice allora che i punti in questo riferimento sono dati come **coordinate mondo** o **coordinate assolute**; analogamente si deﬁniscono le coordinate attrezzo, le coordinate trasportatore, le coordinate pezzo ecc. 

![](http://i.imgur.com/R1Soztb.png)

Altri sistemi di riferimento vengono convenzionalmente ﬁssati ai bracci del manipolatore, in un modo che speciﬁcheremo in un altro post, per descriverne i movimenti relativi e ottenerne la descrizione cinematica e dinamica. Le rotazioni (ove il giunto è rotoidale) e le traslazioni (ove il giunto è prismatico), deﬁniscono le cosiddette **coordinate giunto** o **coordinate macchina**.

Tratterò in dettaglio in uno dei prossimi post i sistemi di riferimento e le rappresentazioni vettoriali di punti geometrici e di variabili fisiche non scalari.

## Tipologie di catena cinematica 

Sulla base della struttura della catena cinematica è possibile classificare i robot in alcune classi caratteristiche.

I costruttori di robot industriali fanno in modo che i primi tre bracci, che formano quella che viene chiamata **spalla**, servano a posizionare nello spazio i successivi tre bracci, che costituiscono quello che viene comunemente chiamato **polso**; a quest’ultimo in genere è affidato il compito di fornire l’orientamento nello spazio della punta operativa. 

Esistono anche strutture meccaniche a bracci paralleli che non rispettano questo schema spalla-polso; queste strutture vengono chiamate, come abbiamo già visto, manipolatori a cinematiche parallele o, più semplicemente, manipolatori paralleli.

Il polso ha una struttura praticamente standard, di solito RRR o 3R, mentre la spalla
pu`o essere progettata in molti modi diversi.
A seconda della struttura cinematica della spalla, i robot si possono classiﬁcare
in:
• robot cartesiani (3P);
• robot cilindrici (1R-2P);
• robot polari (2R-1P);
• robot articolati o antropomorﬁ (3R);
• robot SCARA (Selective Compliance Assembly Robot Arm) (2R-1P con assi di
movimento verticali).
1.3.1 Robot cartesiano
La struttura 3P `e studiata per fornire tre traslazioni lungo i tre assi ortogonali, da
cui il nome di robot cartesiano. Esso pu`o assumere la conﬁgurazione a colonna, come
illustrato in Fig. 1.9 a), oppure a “carro-ponte” come in Fig. 1.9 b). Lo spazio di
lavoro di questo tipo di robot `e dato idealmente da un parallelepipedo.
1.3.2 Robot cilindrico
Un robot cilindrico realizza le coordinate cilindriche: quindi ad un giunto di rotazione,
di solito verticale, seguono un primo giunto prismatico, con asse anch’esso verticale, ed
un secondo giunto prismatico, con asse orizzontale. Lo spazio di lavoro `e idealmente
una corona cilindrica (si veda Fig. 1.10).1.3. CLASSIFICAZIONE DEI ROBOT 13
Figura 1.9: Schema di manipolatore cartesiano: a) a colonna; b) a “carro ponte”.
1.3.3 Robot polare
Il robot polare realizza le coordinate polari: si ha un giunto di rotazione verticale,
seguito da un secondo giunto di rotazione, con asse orizzontale, ed un giunto prisma-
tico, con l’asse allineato lungo l’ultimo braccio (si veda Fig. 1.11). Lo spazio di lavoro
`e idealmente una corona sferica.
1.3.4 Robot articolato o antropomorfo
Viene comunemente indicato anche con il nome di robot antropomorfo, perch´e la sua
struttura `e simile a quella del tronco, braccio e avambraccio umano, su cui si innesta il
polso. Consta di tre giunti rotoidali, il primo dei quali ha solitamente asse di rotazione
verticale, mentre gli altri due sono orizzontali (vedi Fig. 1.12).
In Fig. 1.13 `e riportato il robot antropomorfo Comau Smart S2, mentre in Fig.
1.14 `e riportato un robot antropomorfo per saldatura e in Fig. 1.15 `e illustrato un
robot articolato per verniciatura.
1.3.5 Robot SCARA
Questo tipo di robot, simile come struttura ad un robot polare, si diﬀerenzia per il
fatto che tutti gli assi dei giunti rotoidali sono verticali; in questo modo l’eﬀetto della
gravit`a `e compensato staticamente dalla struttura stessa. Questo tipo di struttura `e
stato inizialmente concepito per compiti di montaggio di circuiti integrati; la pinza
`e dotata di un dispositivo pi`u cedevole in alcune direzioni rispetto ad altre (da cui
il termine selective compliance), che permette l’inserimento dei pezzi senza causare
rotture, come potrebbe avvenire con un dispositivo troppo rigido (vedere Fig. 1.16).
Nella Fig. 1.17 `e illustrato un robot SCARA di saldatura.14 CAPITOLO 1. INTRODUZIONE E DEFINIZIONI
Figura 1.10: Schema di manipolatore cilindrico.
Figura 1.11: Schema di manipolatore polare.
Il robot illustrato in Fig. 1.18 non appartiene ai tipi di robot indicati in precedenza,
ma viene riportato come esempio di manipolatori a catena cinematica chiusa e bracci
paralleli.
1.3.6 Il polso
Il polso di un manipolatore ha essenzialmente il compito di fornire i tre gdl necessari
all’assetto della punta operativa. Per alcuni manipolatori, con compiti ridotti, il polso
pu`o consentire solo uno o due gradi di libert`a.
Le strutture cinematiche pi`u comunemente utilizzate nel polso sono quelle 3R, ma
`e possibile un diverso allineamento degli assi; si pu`o avere una realizzazione meccanica
detta ad angoli di Eulero, oppure una realizzazione che viene chiamata roll-pitch-yaw
o RPY .
Il primo tipo di polso, rappresentato in Fig. 1.19 a), rientra nella categoria dei
polsi sferici, ossia quei polsi per cui i tre assi di rotazione si intersecano in un punto,


![](http://i.imgur.com/pZpRFTE.png)