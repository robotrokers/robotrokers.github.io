---
layout: post
title: Introduzione alla robotica teorica
subtitle: Definizione di robot e robotica
date: 2016-06-06 15:17:00
author: Basilio Bona
categories: Teorica
---
Come promesso, questo secondo post analizza le varie definizioni di robot che sono state date nel corso degli anni e successivamente fornisce alcune classificazioni dei vari tipi di robot.

# Cos'è la Robotica 

La Robotica si può definire come un insieme di teoria e di pratica: la teoria che descrive il robot e le sue funzioni, e la pratica che permette di costruirlo.

La teoria comprende molti aspetti: dalle equazioni cinematiche ai modelli dinamici del robot, dai controlli automatici all'informatica, dalla sensoristica agli azionamenti.

La pratica, come si può immaginare, riguarda la capacità di tradurre la teoria in un funzionamento concreto della struttura che si è descritta matematicamente.

Nei post successivi affronterò principalmente gli aspetti teorici della Robotica.

Ma ora alcune definizioni.

## Varie definizioni di robot 

Il **Robotics Institute of America** fornisce la  seguente definizione 
> **Un robot è un manipolatore riprogrammabile, multi-funzionale, progettato per muovere materiali, parti, attrezzi o dispositivi specializzati, lungo cammini programmati e variabili, allo scopo di eseguire una varietà di compiti.**

La definizione mette in evidenza due caratteristiche fondamentali


- la capacità di **manipolare**. 
Un robot deve essere in grado di afferrare e muovere materiali e attrezzi nello spazio di lavoro e compiere lavorazioni specifiche su oggetti fissi o in movimento, come, ad esempio, effettuare saldature di particolari meccanici, procedere al taglio laser di lamiere, assemblare parti, applicare vernici o collanti e molte altre ancora.

- la **riprogrammabilità**.
Consiste nella capacità di modificare movimenti, traiettorie e operazioni al variare dei compiti che il robot deve assolvere.

Questa definizione andava bene per i primi robot manipolatori usati all'interno delle linee di produzione, soprattutto automobilistiche, mentre ora le tipologie di robot sono diventate molto numerose e risulta un po' riduttiva.

Un'altra definizione più aggiornata ci viene data da Maja Mataric, professoressa di Robotica all'*University of Southern California*
> #### Un robot è un sistema autonomo, che esiste ed opera nello spazio fisico, che può percepire l'ambiente mediante sensori e che può agire su di esso (e io aggiungo, *modificandolo*) per raggiungere qualche obbiettivo.

I fattori caratteristici di un robot sono quindi l'autonomia, la percezione e l'azione.


- **autonomia** significa che opera sulla base di un insieme di leggi che gli permettono di svolgere un compito senza l'intervento diretto dell'utente, cioè dell'essere umano che lo ha progettato o lo sta usando. Di solito le leggi sono codificate in un insieme di programmi software (algoritmi), mentre nel caso dei robot meccanici del Settecento, le leggi erano di tipo "meccanico" e corrispondevano ai meccanismi interni, simili a quelli di un cronometro. Spesso si dice che il robot possiede un'**intelligenza**, che però non ha nulla a che fare con l'intelligenza umana

- **percezione** significa che può misurare, attraverso opportuni sensori, alcune grandezze fisiche che caratterizzano lo stato del robot e/o l'ambiente in cui esso opera, a seconda dell'obbiettivo che viene formulato dall'utente

- **azione** significa che, sulla base delle misure e delle regole di autonomia, può agire in modo diretto o indiretto sull'ambiente che lo circonda.

Facciamo qualche esempio.


1. I bracci robotici industriali, come quelli illustrati in figura, sono strutture montate su una base fissa, dove l'unico movimento possibile è quello dei bracci che compongono la cosiddetta "catena cinematica". 

	![](http://i.imgur.com/yXR0yOj.jpg)
	
	![](http://i.imgur.com/BMz3Fbg.jpg)
	
	Essi operano sulla base di un programma detto 'part program', codificato nel computer di bordo, che misura   gli angoli dei motori e, sulla base di queste misure e dell'obbiettivo da raggiungere, fa muovere i bracci per raggiungere il punto desiderato nello spazio. Una volta raggiunto il punto finale, il robot può o meno effettuare la lavorazione prevista.
	In questo caso l'azione corrisponde alla lavorazione che modifica l'ambiente in cui il robot opera. Se poi il robot non effettua alcuna lavorazione, ma si è limitato a muovere la catena cinematica, la modifica dell'ambiente corrisponde al fatto che l'ambiente intorno al robot non è più quello di prima in quanto il robot stesso si è mosso.

2. I robot mobili, come quelli illustrati in figura, al contrario dei robot industriali, possono muoversi nello spazio in cui si trovano mediante le ruote, ma non possiedono bracci in grado di effettuare lavorazioni.

	![](http://i.imgur.com/nYfbBZg.jpg)
	![](http://i.imgur.com/qn4gjf5.jpg)
	
     Anch'essi operano sulla base di un programma memorizzato da qualche parte (a bordo, oppure "in the cloud" - nella nuvola - come fa HotBlack Robotics). Percepiscono l'ambiente circostante mediante sensori. Nella figura vediamo che i robot hanno a bordo sensori ad ultrasuoni e piccole telecamere. 
     L'azione modifica l'ambiente nel senso detto prima; cioè l'ambiente "oggettivo" non cambia, ma quello "soggettivo" si è modificato grazie al fatto che il robot si è mosso.
 

3. I robot umanoidi, come quelli illustrati in figura, possono muoversi nello spazio mediante le gambe o le ruote di cui sono dotati, è in più utilizzano un paio di braccia capaci di afferrare oggetti, spostarli o effettuare semplici lavorazioni. Anch'essi operano sulla base di un programma e percepiscono l'ambiente circostante mediante sensori. Hanno la possibilità di agire sull'ambiente e comunicare con gli esseri umani attraverso la voce. 


![](http://i.imgur.com/UxCtu2w.jpg) 	
![](http://i.imgur.com/97tGCiN.jpg)


Quest tre esempi ci fanno concludere che la definizione di Mataric è sostanzialmente corretta, perché descrive bene le caratteristiche che un oggetto deve avere per essere definito robot. Il lettore può provare a pensare se il robot da cucina presentato nel post precedente ricade in questa definizione oppure no. 

# Classificazione dei robot

I robot possono essere classificati secondo diverse tipologie. Ad esempio, a seconda dell'ambiente in cui operano, al loro uso, alla struttura meccanica, ecc.

## Robot industriali

Si tratta di strutture meccaniche simili al braccio umano, che come sappiamo è composto da un una spalla, un braccio, un gomito, un polso e una mano. Una struttura meccanica analoga caratterizza questi robot, detti anche *manipolatori robotici*, alla cui estremità è montato un polso e un organo di presa o un attrezzo per effettuare lavorazioni; si usa il termine "punta operativa" per definire genericamente l'estremità del robot.

![](http://i.imgur.com/ivfwZET.jpg)

Di solito sono fissati al pavimento o al soffitto delle linee di produzione, oppure montati su guide mobili che consentono una traslazione di qualche metro.

Le principali caratteristiche dei robot industriali sono queste:


- La struttura è molto rigida per garantire la ripetibilità e la precisione dei movimenti.

- Sono provvisti di motori dotati di motoriduttori per garantire una coppia elevata a parità di potenza trasmessa.

- Ciascun motore è provvisto di un sensore angolare che ne misura la rotazione; talvolta sono dotati di sensori di visione sulla punta operativa.

- Possono portare masse elevate. Il rapporto massa sollevata su massa propria un tempo era sfavorevole; per sollevare 10 kg un tipico robot pesava 1000 kg, quindi un rapporto 1/100. Ora questo rapporto è migliorato e si trovano robot che pesano 30 kg e portano una massa di 10 kg con uno sbraccio di 1 m.  

- Operano in ambienti ben noti e strutturati dal punto di vista geometrico. Ciò significa che tutti gli elementi necessari per la produzione che si trovano intorno al robot sono noti nelle caratteristiche geometriche e occupano posizioni stabili. Inoltre non sono presenti ostacoli mobili all'interno dello spazio di lavoro.

- La potenza elettrica viene fornita da sorgenti esterne al robot.

- I movimenti sono quasi sempre ripetitivi e vengono definiti  da programmi caricati in memoria. Quando bisogna variare le sequenze di lavorazione, occorre modificare il programma o caricarne un altro.

- È molto raro che siano dotati di sensori per percepire eventuali ostacoli nell'ambiente di lavoro ed evitarli; e quindi sono molto pericolosi per gli operatori. Per questa ragione devono lavorare all'interno di zone protette da apparecchiature di sicurezza che fermano il robot in caso di necessità, oppure operano in ambienti privi di operatori umani.

Negli ultimi anni sono disponibili sul mercato robot industriali che possono lavorare vicino ad operatori umani senza particolari problemi o pericoli. Sono i cosiddetti "robot collaborativi" o cobots, come quello nell figura seguente

![](http://i.imgur.com/Et56r7e.jpg)

Si vede che l'operatore può avvicinarsi senza particolari problemi al braccio che sta effettuando delle lavorazioni su una portiera.

Il video seguente illustra le potenzialità dei bracci prodotti dalla Universal Robot, un'azienda danese che in pochi anni ha venduto migliaia di esemplari.

[![ ](http://i.imgur.com/1EYao33.jpg)](http://www.youtube.com/watch?v=Kb9uzqkfoHI)


## Robot umanoidi 

Hanno una struttura simile a quella dell'intero corpo umano; sono dotati di un torso, due gambe, due braccia con mani, e una testa. 

![](http://i.imgur.com/L40tw0r.jpg)

Possiedono quindi quattro catene cinematiche, due per le braccia, due per le gambe, che partono dal torso, su cui è montata la testa, anch'essa dotata della possibilità di muoversi in orizzontale e in verticale (un movimento che si definisce "pan-tilt"). Sulla testa vengono montati di solito numerosi sensori per l'analisi dell'ambiente circostante.

![](http://i.imgur.com/1HR0TDk.png)

Le mani possono essere semplici, con due o tre dita, o più complesse in modo da simulare la mano umana.

![](http://i.imgur.com/Cs8SwLe.jpg) 
![](http://i.imgur.com/p3OYeIv.jpg)

Ecco le principali caratteristiche dei robot umanoidi:

- La struttura meccanica è molto più complessa di quella dei robot industriali, perché comprende più catene cinematiche, che devono muoversi in maniera combinata per garantire la mobilità e la manipolabilità di oggetti

- Il numero di motori è quindi molto più alto. Possono essere dotati di motoridottori oppure no (ad esempio quelli delle mani), spesso la loro collocazione è rese complessa dalla necessità di garantire il centro di massa sulla verticale. Alcuni movimenti possono essere azionati da fili metallici o altre soluzioni simili ai tendini umani.

- Non è necessario garantire una rigidezza elevata dell'insieme, in quanto non è previsto che vengano compiuti movimenti precisi e ripetibili. Tuttavia questo può comportare un'andatura a scatti, tipica dei robot umanoidi costruiti dai makers.

- Sono dotati di sensori sia interni sia esterni, questi ultimi di solito sono sensori a ultrasuoni e/o telecamente

- Sono dotati spesso di strumenti per omunicare con l'utente attraverso suoni o parole e possono anche possedere sistemi di riconoscimento vocale.

- Il carico che possono trasportare con le braccia è molto limitato.

- Operano in ambienti scarsamente strutturati e spesso ignoti a priori. Funzionano quasi sempre bene solo su superfici piane.

- Hanno un'autonomia limitata, perché le batterie, se sono collocate a bordo, non devono essere troppo pesanti o ingombranti. I molti casi i robot umanoidi in fase sperimentale sono collegati ad una sorgente di potenza fissa attraverso un "cordone ombelicale".

- I requisiti di sicurezza non sono ancora esattamente definiti, ma è chiaro che i robot umanoidi non devono arrecare danno alle persone o agli ambienti entro cui si muovono.

- Poiché questi robot operano a contatto con persone che non sono necessariamente dei tecnici, occorre prevedere delle interfacce uomo-macchina più sofisticate e usabili che non quelle di un robot industriale.

- Esiste un problema di "accettabilità sociale" di questo tipo di robot. Nella nostra cultura, per ragioni che non voglio approfondire qui, un robot con forme "troppo" umane desta preoccupazione o anche rifiuto. Talvolta è opportuno de-umanizzare il robot per farlo chiaramente percepire come una macchina.

Recentemente, la società giapponese SoftBank ha acquistato da Alphabet, holding a cui fanno capo Google Inc. e altre società controllate, l'azienda Boston Dynamics, un leader nel settore della robotica mobile, che produce diversi robot umanoidi e su zampe, come si può vedere nei seguenti video

[![ ](http://i.imgur.com/VLVT2Wp.png)](http://www.youtube.com/watch?v=rVlhMGQgDkY)

[![ ](http://i.imgur.com/OT95zk6.png)](http://www.youtube.com/watch?v=tf7IEVTDjng)

[![ ](http://i.imgur.com/F2g9fx7.png)](http://www.youtube.com/watch?v=-7xvqQeoA8c)

