---
layout: post
title:  Robotica, Open Source, ROS e Cloud Robotics
date:   2017-06-30
author: Ludovico Russo
categories: Teorica
---

Scrivo questo post perchè ho visto molto interesse all'interno della community Rokers sul tema ROS (Robot Operating System). Il mio intento è quello di fare alcune precisazioni sul progetto, spiegare perchè è tanto interessante nonchè tanto popolare.

In futuro, vorrei creare, all'interno di questo blog, una serie di tutorial pratici che spiegano come utilizzarlo in pratica.

Ma prima di tutto, vediamo esattamente cosa è questa tecnologia!

## La Robotica di Servizio

Per introdurre ROS, dobbiamo necessariamente introdurre il concetto di **Robotica di Servizio**. Molto spesso, infatti, quando si parla di Robotica, si pensa principalmente a tre differenti aspetti:

 - La robotica industriale, che è quella a cui tecnologicamente e realisticamente siamo più abituati. E il prof. Basilio Bona, su questo argomento, vi sta già tediando abbastanza :D
 - La robotica nella fantascienza, in cui solitamente si parla di Roboti Umanoidi non tanto distinguibili dagli essere umani (e che molto spesso tantano di distruggere la razza umana)!
 - La robotica educativa/making, che ha invaso le scuole e i fablab negli ultimi anni, in cui vediamo piccoli robottini con pochissima autonomia, realizzati per scopi didattici o per puro divertimento.

Tuttavia, negli ultimi anni, un nuovo campo di applicazione della robotica sta sempre più prendendo piede, sia dal punto di vista della ricerca, ma anche con applicazioni reali sul mercato: si parla della **robotica di servizio**.

Ora, definire esattamente cosa è la robotica di servizio è molto difficile, in quanto esistono tantissime applicazioni pratiche molto diverse tra di loro (e con hardware molto diverso). Tuttavia, cercherò di dare la mia personalissima definizione (che non comprende tutti i casi, come è ovvio che sia):

> Un **sistema robotico** di **servizio** è un sistema robotico in grado di aiutare gli esseri umani a svolgere un certo tipo di compito in modo **(semi)autonomo**, **senza essere programmato** dall'utente.

Dal mio personalissimo punto di vista, un sistema robotico (ho scelto appositamente questa il termine *sistema robotico*, e non *robot*) di servizio deve avere una specifica caratteristica per essere definito tale:

 - Non necessitare di una programmazione dell'utente per svolgere il suo lavoro.

Questo è infatti ciò che distingue, sia da un punto di vista tecnologico che da un punto di vista applicativo, un sistema di robotica di servizio dai classici sistemi di robotica industriale.

Applicativamente, infatti, un utente non deve essere "esperto" in robotica per poter usare il sistema. Pensate per esempio al Roomba (o ai vari robot per pulire i pavimenti): il loro utilizzo è quasi come quello di un'applicazione per uno smarphone: apri la scatola, accendi, fine. Il robot fa quasi tutto lui, con le dovute limitazioni, ma è quasi completamente autonomo.

Il problema è tecnologico: infatti sviluppare un robot con un alto grado di autonomia è un casino.
Limitiamoci al caso specifico di robot su ruote: i programmatori non possono fare "assunzioni" su cosa succede intorno al robot, come avviene invece nei robot industriali. Il robot deve essere autonomo, sicuro e deve durare, e questo implica che questa debba essere in grado di eseguire alcuni compiti complessi, che sono (pricipalmente) quelli che trovate qui sotto:

 - **mapping**: Il robot deve essere in grado di costruire una "mappa" (cioè un modello matematico) dell'ambiente in cui si trova.
 - **localization** Il robot deve essere in grado di determinare la propria posizione all'interno dell'ambiente (utiilizzando la mappa di cui sopra).
 - **path planning** Il robot deve essere in grado di pianificare una traiettoria da seguire per raggiungere un punto specifico della mappa.
 - **path following** Il robot deve essere in grado di seguire una traittoria pianificata nel punto sopra, considerando la possibilità di trovare ostacoli non previsti come persone in movimento o oggetti non presenti in fase di costruzione della mappa.

 Queste 4 capacità vengono solitamente raggruppate sotto il noto problema detto **robot navigation**, problema ancora tecnologicamente aperto e non completamente risolto.

 Si noti inoltre che le 4 capacità sopra citate sono anchesse non ben definite, e dipendono molto dalla specifica applicazione. Per un robot che si muove in esterno le prime due sono quasi gratuite: basta sfruttare un qualsiasi servizio che fornisce mappe terrestri e dei GPS (anche se ci sarebbe un grosso discorso da fare sulla precisione degli stessi); ma il path following diventa molto delicato. Al contrario, in un robot che si muove all'interno di un edificio **mapping** e **localizzazione** spesso sono problemi che devono essere risolti contemporaneamente (il robot mentre costruisce la mappa deve sapere la posizione di se stesso nella mappa in contruzione): in questo caso, si parla di un noto e importante problema nella robotica chiamato **SLAM** (Simultaneous Localization and Mapping).

 A tale complessità, si aggiungono altri problemi quando si sviluppano le applicazioni robotiche:

  - Interazione con la persona
  - Limiti di batteria
  - Costo dell'hardware e del software

Capite quindi che, per un ingegnere robotico (come me), il tutto è un grosso casino. E tutto questo macello sta alla base del progetto ROS.

## ROS: The Robot Operating System

> Why ROS? Because creating truly robust, general-purpose robot software is hard. From the robot's perspective, problems that seem trivial to humans often vary wildly between instances of tasks and environments. Dealing with these variations is so hard that no single individual, laboratory, or institution can hope to do it on their own. \[[ros.org/about-ros/](http://www.ros.org/about-ros/)\]

Provo a tradurre:

> Perchè ROS? Perchè sviluppare software robusti e general-porpose per robot è difficile. Dal punto di vista di un robot, problemi che sembrano banali agli essere umani spesso variano molto per le funzioni e gli ambienti. Affrontare queste variazioni è così difficile che nessun singolo individuo, laboratorio o istituto possa sperare di farlo da solo.

La volontà e l'intuizione degli ideatori di ROS era quindi quella di fornire un ecosistema per spingere vari gruppi di ricerca in tutto il mondo a collaborare per risolevere questi problemi tanto complessi unendo le forze.

Dopo circa 10 anni dalla prima versione realizzata di ROS, posso certamente affermare che lo scopo principale (quello di creare una community a livello mondiale), è stato realizzato, ed infatti, all'interno del mondo ROS, è possibile trovare pacchetti che risolvono (o tentano di risovlere, in quanto la tencologia ancora non è perfetta) praticamente tutti i problemi tecnologici legati alla robotica di servizio.

### Ma quindi, cosa cavolo è 'sto ROS???

Mi aspetto che chi è riuscito a leggere questo articolo fino a qui si sia fatto questa domanda. Vediamo di capire esattamente cosa è. Ma prima sfatiamo un mito: a dispetto del nome, ROS **non è un sistema operativo per robot**. ROS, invece, è:

 - Un framework per lo sviluppo di applicazione robotiche (connesse).
 - Un set di Librerie, strumenti di sviluppo e convenzioni che forniscono una base tecnologica robusta da cui partire per lo sviluppo di tali applicazioni.
 - Una grossisima community di ricercatori, scienziati e appassianati da tutto il mondo.
