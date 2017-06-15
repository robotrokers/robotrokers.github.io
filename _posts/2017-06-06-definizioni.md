---
layout: post
title: Introduzione alla robotica teorica
subtitle: Che cos'è un robot?
date: 2017-06-06 15:17:00
author: Basilio Bona
categories: Teorica
---


# Che cos'è un robot?

Perchè un Rokeriano dovrebbe chiedersi che cos'è un robot? Lo sa benissimo, visto che li costruisce tutti i giorni e ne parla con gli altri amici della comunità Rokers.

Tutti sanno che i robot sono apparecchiature meccatroniche complesse, che di solito si muovono nel piano o nello spazio, e sono composte da numerose parti, componenti e strutture meccaniche, circuiti elettrici, schede elettroniche, attuatori, sensori, e che hanno a bordo un qualche tipo di unità di controllo (Arduino, Raspberry o altro) su cui girano i programmi per la movimentazione e la gestione del robot stesso.

Tuttavia non sempre siamo d'accordo su che cosa sia veramente un robot e quali siano le caratterisctiche principali che lo contraddistinguono da altri apparati automatici.

Ad esempio, esistono elettrodomestici chiamati **_robot da cucina_**, come quello in figura

<img src="http://i.imgur.com/K2TbVJ2.jpg" width="100">

ma sappiamo bene che questo non è un robot come lo intendiamo noi.

Esiste una confusione sui termini e vogliamo provare a fare chiarezza.

In questo primo post vedremo l'origine della parola ***robot*** e successivamente presenteremo  una serie di **definizioni** che saranno discusse per capire se corrispondono alla nostra percezione di cosa sia un robot.

## Storia della parola robot

Sebbene i robot siano apparecchiature con una storia relativamente recente, in quanto i primi esemplari per telemanipolazione di sostanze radioattive vennero prodotti negli Stati Uniti a partire dal 1944, l'idea di robot, inteso come una creatura meccanica che sostituisce l'uomo nelle lavorazioni più ripetitive e pericolose, ha invece radici che affondano in tempi remoti.

Tralasciando un certo numero di realizzazioni meccaniche mosse dalla forza dell'acqua o del vapore, alcune delle quali si possono far risalire fino alla civiltà greca, nel Settecento appaiono alcuni ***automi meccanici***, realizzati ad opera dell'artigiano svizzero Pierre Jaquet-Droz e di suo figlio Henri-Louis. Questi oggetti sono in grado di ripetere una serie di azioni prefissate, come scrivere, disegnare e suonare strumenti musicali, simulando perfettamente il movimento umano. Pur trattandosi di oggetti meravigliosi, essi però non permettono una riprogrammazione dei movimenti, poiché questi ultimi sono ottenuti attraverso una serie di leve, ingranaggi e rinvii meccanici fissi, molto simili ai movimenti di un orologio.

Questi automi meccanici vengono anche chiamati **androidi** a causa della loro forma umana. Essi sono privi di ogni intelligenza e autonomia e rivestono solo un interesse storico e artistico, per l'eccellenza meccanica e la maestria dei loro costruttori. Questi automi si possono ancora oggi ammirare nel [Museo di Arte e Scienza di Neuchâtel](http://www.neuchateltourisme.ch/en/decouvertes/museums/art-and-history-museum-neuchatel.4740.html), in Svizzera. 

Chi fosse interessato agli automi meccanici, può leggere la voce [Automa meccanico](https://it.wikipedia.org/wiki/Automa_meccanico "Wikipedia") su Wikipedia.

Nell’Ottocento, i robot trovano un antenato letterario nel personaggio del romanzo **Frankenstein (1816)** di Mary Shelley, in cui viene narrata la storia di un essere artiﬁciale, creato in laboratorio dall’innesto di un cervello umano su un cadavere. Il romanzo racconta poi la ribellione di questa creatura e la sua sconﬁtta ﬁnale.

Il termine robot è stato coniato dallo scrittore ceco Karel Čapek nel suo romanzo fantapolitico R.U.R. (Rossumovi univerzální roboti, ossia I Robot Universali di Rossum), scritto nel 1920 e rappresentato a teatro nel 1921. 

![](http://i.imgur.com/LivQU6J.jpg)

Si tratta di un’utopia negativa, dove uno scienziato/ingegnere di nome Rossum costruisce creature biologiche, al ﬁne di utilizzarle come macchine simili all’uomo, ma instancabili, più precise ed aﬃdabili, destinate a sostituire con maggior proﬁtto gli operai nelle fabbriche. Alla ﬁne della storia queste creature artiﬁciali si ribellano, minacciando di distruggere l’intera razza umana.

Questo lavoro propone una riflessione sulle paure ancestrali che l'uomo del XX secolo prova di fronte alla rapidità  con cui il progresso scientifico avanza. La creazione di un uomo artificiale, il suo sfruttamento nel mercato del lavoro e perfino lo scoppio di guerre distruttive sono all'epoca temi già noti; la grande novità del dramma di Karel Capek consiste nel ridurre al minimo la distanza tra creatura artificiale e umana. Il robot è un operaio artificiale non meccanico, è una replica semplificata dell'uomo: nelle intenzioni dell'autore "R.U.R." è un grido d'allarme, "un ammonimento alla società tecnologica, perché si avveda in tempo del baratro in cui sta precipitando". Sarà invece l'aspetto spettacolare e drammatico della lotta tra uomini e robot a catturare l'attenzione degli spettatori e a inaugurare un filone che avrà grande successo letterario e cinematografico lungo tutto il Novecento e ancora oggi nel XXI secolo.

Pare che Karel Čapek non fosse il vero inventore della parola, che forse gli venne suggerita dal fratello Josef, scrittore e pittore cubista, che aveva già affrontato il tema in un suo racconto del 1917, “Opilec” (L’ubriacone), nel quale però aveva usato il termine **automat**. 

Nelle lingue slave, come il russo e il ceco, la parola lavoro si traduce in rabota, e quindi la scelta di chiamarlo robot richiama l'utilizzo di questi "esseri" come operai economici e instancabili.

La diffusione del romanzo di Karel Čapek diede un’enorme fama al termine robot, anche se ormai il libro è caduto nel dimenticatoio, almeno in Italia. In rete non è disponibile una versione in italiano dell'opera e bisogna accontentarsi di quella in inglese (disponibile [qui](http://preprints.readingroo.ms/RUR/rur.pdf))

Anche se i robot di Čapek erano uomini artificiali costruiti con materia organica, il termine viene generalmente utilizzato per indicare un uomo meccanico, mentre si usa il termine **cyborg** (“organismo cibernetico” o “uomo bionico”) per indicare una creatura che combina parti organiche e meccaniche, come il ben noto Terminator cinematografico.

![](http://i.imgur.com/dmAkmis.jpg)


R.U.R. alimenta una visione che, almeno in parte, persiste ancora oggi e che vede nel robot un essere artificiale di aspetto umano, dotato di intelligenza, sentimenti ed una personalità ben definita, ma ostile all'uomo e desideroso di distruggerlo per instaurare il proprio dominio. 

Il famoso film **Metropolis** di Fritz Lang (1926), anche se introduce per la prima volta creature interamente meccaniche, ma con sembianze umane, contribuisce a rinforzare questa sensazione, che è accompagnata da un senso di sottile paura verso le conseguenze di un uso indiscriminato di queste creature robotiche.

Un robot di cui non si parla molto è Eric, costruito dal Capitano William H. Richards, un veterano della prima Guerra Mondiale e dall'ingegner A. H. Reffell. Eric fu chiamato ad inaugurare la Mostra della Società degli Ingegneri Modellisti a Londra nel 1928, dove tenne anche un discorso. Esso aveva un corpo in allumino simile ad un'armatura medioevale. I suoi occhi erano lampadine su cui erano dipinte della pupille rosse. Scintille elettriche emanavano dai suoi denti dovute ad una tensione di 35.000 Volt.

![](http://i.imgur.com/9iz630G.jpg)

Per saperne di più c'è un [sito](http://cyberneticzoo.com/robots/1928-eric-robot-capt-richards-english/) in inglese dove si possono trovare altri particolari curiosi.

La parola "robotica" venne resa famosa da Isaac Asimov, ben noto scrittore di fantascienza, che nel 1942 pubblicò 
il racconto *Runaround* (in italiano tradotto con "Circolo Vizioso" o anche "Girotondo"). 

Questo ed altri racconti del ciclo robotico vennero inseriti nella raccolta "I Robot" pubblicata nel 1950.

![](http://i.imgur.com/szrvxPN.jpg)

Il racconto Runaround nella versione originale inglese è disponibile [qui](http://web.williams.edu/Mathematics/sjmiller/public_html/105Sp10/handouts/Runaround.html).

Contrariamente alla visione pessimistica di Čapek e Lang, Asimov definisce sostanzialmente un tipo di
comportamento positivo e collaborativo da parte dei robot, attraverso l'enunciazione delle
tre leggi della robotica}

1. Un robot non deve danneggiare un essere umano, o permettere che un essere umano sia danneggiato.
2. Un robot deve obbedire agli ordini di un essere umano, eccetto quando tali ordini entrano in conflitto con la prima legge.
3. Un robot deve proteggere la propria incolumità fino a quando questo comportamento non entra in conflitto con le prime due leggi.

Tuttavia le creature meccaniche immaginate dalla fantasia di questi artisti, erano e sono tuttora ben lontane dal poter essere realizzate concretamente, a causa delle limitazioni della tecnologia e della ancora superficiale comprensione dei meccanismi che reggono il funzionamento profondo del cervello umano e che permettono la formazione del pensiero, delle idee astratte, della conoscenza, in una parola di quelle leggi che sovraintendono al comportamento autonomo, responsabile e intelligente.

La dualità "robot buono - robot cattivo" persiste tuttora e nel corso di questi anni sono apparsi romanzi, racconti e film che presentano i robot ora come pericoli per l'intera umanità, ora come simpatici compagni di avventura.

Con l'aiuto dei lettori di questo blog, vorrei compilare una lista di queste due categorie di robot, per cui vi invito a segnalarmi i film e/o i romanzi che ritenete rappresentino queste due facce della robotica.

In attesa delle vostre indicazioni, il prossimo blog sarà dedicato a discutere la definizione di robot.



