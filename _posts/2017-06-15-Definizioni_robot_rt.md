---
layout: post
title: Introduzione alla robotica teorica 2
subtitle: Definizione di robot e robotica
date: 2017-06-06 15:17:00
author: Basilio Bona
categories: Teorica
---
Come promesso, in questo secondo post analizzo le varie definizioni di robot che sono state formulate nel corso degli anni e successivamente fornisco alcune classificazioni dei vari tipi di robot.

# Cos'è la Robotica 

Si prevede che nei prossimi anni la robotica sia uno dei settori con il più alto tasso di crescita, insieme all'intelligenza artificiale fondata sul deep learning e i big data.  

Le stime per il 2020 del valore del mercato mondiale dei robot industriali è stimato intorno agli 80 miliardi di dollari e quello della robotica di servizio intorno ai 24 miliardi di dollari.

La rivista Fortune nel 2016 stimava che nel 2019 il valore complessivo mondiale della robotica si sarebbe aggirato intorno ai 135 miliardi di dollari.

Come si può definire la Robotica? 

Si può dire che sia un insieme sinergico di teorie e di tecnologie che formano la base per lo studio, la progettazione e la realizzazione dei robot.

Quindi la Robotica è sostanzialmente un insieme di teoria e di pratica: la teoria che descrive il robot e le sue funzioni, e la pratica che permette di costruirlo.

La teoria comprende molti aspetti: dalla definizione delle equazioni cinematiche ai modelli dinamici dei robot, dai controlli automatici all'informatica, dalla sensoristica agli azionamenti, per citarne solo alcuni. Intelligenza artificiale e big data saranno in futuro utilizzati per costruire robot sempre più "intelligenti" e adatti a lavorare spalla a spalla con gli esseri umani.

La tecnologia, come si può immaginare, riguarda la capacità di tradurre la teoria in un funzionamento concreto della struttura robotica che si è descritta matematicamente.

Nei post successivi affronterò principalmente gli aspetti teorici della Robotica, partendo dalla descrizione delle catene cinematiche e della loro rappresentazione matematica. In questo post mi limito a fornire alcune definizioni ed a individuare alcuni settori della robotica.

## Il Robot: definizioni 

Il **Robotics Institute of America** lo definisce così: 
> **Un robot è un manipolatore riprogrammabile, multi-funzionale, progettato per muovere materiali, parti, attrezzi o dispositivi specializzati, lungo cammini programmati e variabili, allo scopo di eseguire una varietà di compiti.**

La definizione mette in evidenza due caratteristiche fondamentali


- la capacità di **manipolare**. 
Un robot deve essere in grado di afferrare e muovere materiali e attrezzi nello spazio di lavoro e compiere lavorazioni specifiche su oggetti fissi o in movimento; ad esempio, effettuare saldature di particolari meccanici, procedere al taglio laser di lamiere, assemblare parti, applicare vernici o collanti e molte altre lavorazioni.

- la **riprogrammabilità**.
Consiste nella possibilità di modificare movimenti, traiettorie e operazioni al variare dei compiti che il robot deve assolvere.

Questa definizione andava bene per i primi robot manipolatori usati all'interno delle linee di produzione, soprattutto automobilistiche, mentre ora le tipologie di robot sono diventate molto più numerose ed essa risulta un po' riduttiva.

Un'altra definizione più aggiornata viene data da Maja Mataric, professoressa di Robotica all'*University of Southern California*
> #### Un robot è un sistema autonomo, che esiste ed opera nello spazio fisico, che può percepire l'ambiente mediante sensori e che può agire su di esso (e io aggiungo, *modificandolo*) per raggiungere un obbiettivo specificato.

I fattori caratteristici di un robot sono quindi l'autonomia, la percezione e l'azione.


- **autonomia** significa che il robot opera sulla base di un insieme di leggi che gli permettono di svolgere un compito senza l'intervento diretto dell'utente, cioè dell'essere umano che lo ha progettato o lo sta usando. Di solito le leggi sono codificate in un insieme di programmi software (algoritmi), mentre nel caso dei robot meccanici del Settecento, le leggi erano di tipo "meccanico" e corrispondevano ai meccanismi interni, simili a quelli di un cronometro. Spesso si dice che il robot possiede un'**intelligenza**, che però non ha nulla a che fare con l'intelligenza umana, ma è solo un modo sintetico per definite l'insieme di algoritmi che lo comandano.

- **percezione** significa che può misurare, attraverso opportuni sensori, alcune grandezze fisiche che caratterizzano lo stato del robot e/o l'ambiente in cui esso opera, a seconda dell'obbiettivo che viene formulato dall'utente. I sensori possono essere **propriocettivi** o **eterocettivi** (talvolta detti **esterocettivi**); i primi misurano le grandezze interne al robot, i secondi misurano le grandezze dell'ambiente in cui il robot opera

- **azione** significa che, sulla base delle misure e delle regole che ne definiscono l'autonomia, il robot può agire sull'ambiente che lo circonda, modificandolo in modo diretto o indiretto. 

Facciamo qualche esempio.

1. I bracci robotici industriali, come quelli illustrati in figura, sono strutture montate su una base fissa, dove l'unico movimento possibile è quello dei bracci che compongono la cosiddetta "catena cinematica". 

	![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/yXR0yOj.jpg)
	
	![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/BMz3Fbg.jpg)
	
	Essi operano sulla base di un programma detto 'part program', codificato nel computer di bordo, che misura   gli angoli dei motori e, sulla base di queste misure e dell'obbiettivo da raggiungere, fa muovere i bracci per raggiungere il punto desiderato nello spazio. Una volta raggiunto il punto finale, il robot può o meno effettuare la lavorazione prevista.
	
	In questo caso l'azione corrisponde alla lavorazione che modifica l'ambiente in cui il robot opera. Se poi il robot non effettua alcuna lavorazione, ma si è limitato a muovere la catena cinematica, la modifica dell'ambiente è indiretta e corrisponde al fatto che l'ambiente intorno al robot non è più quello di prima in quanto, essendosi il robot mosso, l'ambiente viene percepito in modo diverso.
 
2. I robot mobili, detti anche **rover**, come quelli illustrati in figura, al contrario dei robot industriali, possono muoversi nello spazio in cui si trovano mediante le ruote, ma non possiedono bracci in grado di effettuare lavorazioni o afferrare oggetti.

   ![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/nYfbBZg.jpg)

   ![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/qn4gjf5.jpg)

	
   Anche questi robot operano sulla base di un programma memorizzato da qualche parte (a bordo, oppure "in the cloud" - nella nuvola - come fa HotBlack Robotics). Anch'essi percepiscono l'ambiente circostante mediante sensori. 
	
   Nella figura vediamo che i robot hanno a bordo sensori ad ultrasuoni e piccole telecamere. L'azione modifica l'ambiente nel senso detto prima; cioè l'ambiente "oggettivo" non cambia, ma quello "soggettivo" si è modificato grazie al fatto che il robot si è mosso. 

3. I robot umanoidi, come quelli illustrati sotto, possono muoversi nello spazio utilizzando gambe o ruote, ma in più sono dotati di un paio di braccia capaci di muoversi, afferrare oggetti, spostarli o effettuare semplici lavorazioni.

    ![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/UxCtu2w.jpg)
 	
	
    ![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/97tGCiN.jpg)
	
	Anch'essi operano sulla base di un programma e percepiscono l'ambiente circostante mediante sensori. Hanno la possibilità di agire sull'ambiente e comunicare con gli esseri umani attraverso input e output vocali.

Questi tre esempi ci fanno concludere che la definizione di Mataric è sostanzialmente corretta, perché descrive bene le caratteristiche che un oggetto complesso deve avere per essere definito robot. Il lettore può provare a riflettere se il robot da cucina presentato nel post precedente ricade in questa definizione oppure no. 

# Classificazione dei robot

I robot possono essere classificati secondo diverse tipologie. Ad esempio, a seconda 

 - della struttura meccanica che li contraddistingue
 
 - dell'ambiente in cui operano, 
 
 - dell'uso a cui sono destinati
 
 - ecc.

## Strutture meccaniche

### Robot industriali

Si tratta di strutture meccaniche simili al braccio umano, che, come sappiamo, è composto da un una spalla attaccata al torso, un braccio, un gomito, un polso e una mano. Una struttura meccanica analoga caratterizza questi robot, detti anche *manipolatori robotici*, alla cui estremità è montato un polso e un organo di presa o un attrezzo per effettuare lavorazioni; si usa il termine **punta operativa** per definire genericamente l'estremità del robot includendo anche l'eventuale attrezzo.

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/ivfwZET.jpg)

Di solito sono fissati al pavimento o al soffitto delle linee di produzione, oppure montati su guide mobili che consentono una traslazione di qualche metro.

#### Caratteristiche


- La struttura è molto rigida per garantire la ripetibilità e la precisione dei movimenti.

- Sono provvisti di motori dotati di motoriduttori per erogare una coppia elevata a parità di potenza trasmessa.

- Ciascun motore è provvisto di un sensore angolare (encoder o resolver, più raramente sensori potenziometrici) che ne misura la rotazione; talvolta sono dotati di sensori di visione sulla punta operativa.

- Possono portare masse elevate. Un tempo il rapporto massa sollevata su massa propria era sfavorevole; per sollevare 10 kg un tipico robot pesava 1000 kg, quindi un rapporto 1/100. Ora questo rapporto è migliorato e si trovano robot che pesano 30 kg e portano una massa di 10 kg con uno sbraccio di 1 m.  

- Operano in ambienti ben noti e strutturati dal punto di vista geometrico. Ciò significa che tutti gli elementi necessari per la produzione che si trovano intorno al robot sono noti nelle caratteristiche geometriche e occupano posizioni stabili. Inoltre non sono presenti ostacoli incogniti all'interno dello spazio di lavoro.

- La potenza elettrica viene fornita da sorgenti esterne al robot.

- I movimenti sono quasi sempre ripetitivi e vengono definiti  da programmi caricati in memoria, detti part-program. Quando bisogna variare la sequenze di lavorazione, occorre modificare il programma o caricarne un altro.

- È molto raro che siano dotati di sensori per percepire eventuali ostacoli nell'ambiente di lavoro ed evitarli; e quindi sono molto pericolosi per gli operatori. Per questa ragione devono lavorare all'interno di zone protette da apparecchiature di sicurezza che fermano il robot in caso di necessità, oppure operano in ambienti privi di operatori umani.

Negli ultimi anni sono disponibili sul mercato robot industriali che possono lavorare vicino ad operatori umani senza particolari problemi o pericoli. Sono i cosiddetti "robot collaborativi" o cobots, come quello nella figura seguente

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/Et56r7e.jpg)

Si intuisce che l'operatore può avvicinarsi senza particolari problemi al braccio robotico che sta effettuando delle lavorazioni su una portiera.

Il video seguente illustra le potenzialità dei bracci robotici collaborativi prodotti dalla Universal Robot, un'azienda danese che in pochi anni ha venduto migliaia di esemplari.

[![ ](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/1EYao33.jpg)](http://www.youtube.com/watch?v=Kb9uzqkfoHI)


### Robot umanoidi

Hanno una struttura simile a quella dell'intero corpo umano; sono dotati di un torso, due gambe, due braccia con mani, e una testa. 

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/L40tw0r.jpg)

Possiedono quindi quattro catene cinematiche, due per le braccia, due per le gambe, che partono dal torso, su cui è montata la testa, anch'essa dotata della possibilità di muoversi in orizzontale e in verticale (un movimento che si definisce "pan-tilt"). Sulla testa vengono montati di solito numerosi sensori per l'analisi dell'ambiente circostante, mentre l'unità di comando di solito non è ubicata nella testa, ma nel torso.

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/1HR0TDk.png)

Le mani possono essere semplici, con due o tre dita, o più complesse, in modo da simulare la mano umana.

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/Cs8SwLe.jpg) 
![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/p3OYeIv.jpg)


#### Caratteristiche


- La struttura meccanica dei robot umanoidi è molto più complessa di quella dei robot industriali, perché comprende più catene cinematiche, che devono muoversi in maniera combinata per garantire la stabilità del moto e la manipolabilità degli oggetti.

- Il numero di motori è quindi piuttosto alto. Essi possono essere dotati di motoriduttori oppure no (ad esempio quelli delle mani), spesso la loro collocazione è resa complessa dalla necessità di garantire che il centro di massa rimanga approssimativamente sulla verticale. Alcuni movimenti delle dita delle mani possono essere azionati da fili metallici o altre soluzioni simili ai tendini umani.

- Non è necessario garantire una rigidezza elevata dell'insieme, in quanto non è previsto che vengano compiuti movimenti precisi e ripetibili. Tuttavia questo può comportare un'andatura a scatti, tipica dei robot umanoidi costruiti dai makers.

- Sono dotati di sensori sia interni sia esterni, questi ultimi di solito sono sensori a ultrasuoni e/o telecamere.

- Spesso hanno la possibilità di comunicare con l'utente attraverso suoni o parole e possono anche possedere sistemi di riconoscimento e sintesi vocale.

- Il carico che possono trasportare con le braccia è molto limitato.

- Operano in ambienti scarsamente strutturati e spesso ignoti a priori. Funzionano bene quasi sempre solo su superfici piane.

- Hanno un'autonomia limitata, perché le batterie, se sono collocate a bordo, non devono essere troppo pesanti o ingombranti. I molti casi i robot umanoidi in fase sperimentale sono collegati ad una sorgente di potenza fissa esterna attraverso un "cordone ombelicale".

- I requisiti di sicurezza non sono ancora esattamente definiti, ma è chiaro che i robot umanoidi non devono arrecare danno alle persone o agli ambienti entro cui si operano.


- Poiché questi robot operano a contatto con persone che non sono necessariamente dei tecnici, occorre prevedere delle interfacce uomo-macchina più sofisticate e usabili che non quelle di un robot industriale.

- Esiste un problema di "accettabilità sociale" di questo tipo di robot. Nella nostra cultura, per ragioni che non voglio approfondire qui, un robot con forme "troppo" umane desta preoccupazione o anche rifiuto. Talvolta è opportuno de-umanizzare il robot per farlo chiaramente percepire come una macchina.

Recentemente, la società giapponese SoftBank ha acquistato da Alphabet, holding a cui fanno capo Google Inc. e altre società controllate, l'azienda Boston Dynamics, un leader nel settore dei robot umanoidi e su zampe, come si può vedere nei seguenti video.

[![ ](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/VLVT2Wp.png)](http://www.youtube.com/watch?v=rVlhMGQgDkY)

[![ ](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/OT95zk6.png)](http://www.youtube.com/watch?v=tf7IEVTDjng)

[![ ](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/F2g9fx7.png)](http://www.youtube.com/watch?v=-7xvqQeoA8c)

### Robot biomimetici

Sono quelle strutture robotiche che imitano le soluzioni presenti in natura, soprattutto per quanto riguarda le soluzioni di locomozione e più recentemente anche di sensoristica avanzata.

Alcuni esempi di robot biomimetici sono illustrati nella figura seguente.

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/awnTBDx.png)

Questa categoria di robot non ha al momento prodotto grandi ricadute applicative, in quanto è raro vedere soluzioni basate su queste strutture utilizzate per compiti reali, tranne i robot a zampe, che sembra possano avere interesse in applicazioni civili e militari. 

#### Caratteristiche


- Questi robot copiano le modalità di movimento di uccelli, pesci, insetti o altri animali terresti. Vi sono realizzazioni che imitano cavallette, ghepardi, salamandre, farfalle, colibrì, ecc.; chi li realizza ha lo scopo prevalente di dimostrare che è possibile pensare a soluzioni alternative alla locomozione su ruote o su gambe.

- Possono avere quattro, sei o otto gambe oppure essere totalmente privi di gambe. Possono avere pinne, ali, zampe, o muoversi come i serpenti e i vermi. Alcuni sono di dimensioni minuscole, altri misurano anche qualche metro.

- Salvo qualche eccezione, non possiedono una grande autonomia e spesso sono teleguidati.

- La dotazione di sensori è scarsa o del tutto mancante, ma nelle strutture più adatte agli usi pratici, i sensori sono presenti.

- Non prevedono alcun sistema di sicurezza verso gli utenti, salvo quelli di grandi dimensioni e massa notevole.

- Si possono muovere in ambienti terrestri, marini e aerei.


## Ambienti in cui operano

### Terrestre

Sono quei robot che si muovono sulla superficie terrestre o di altri corpi del sistema solare.

I primi hanno moltissimi usi e sono quasi esclusivamente dotati di due o quattro ruote, talvolta di gambe o zampe.

I secondi, prevalentemente dotati di ruote, sono stati usati per l'esplorazione in situ di altri corpi del sistema solare; ne sono un esempio ben noto i rover Beagle, Spirit, Opportunity e Curiosity che da molti anni percorrono il suolo marziano.

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/curiosity.jpg)

### Marino

Questi robot si muovono sulla superficie del mare o in profondità. I robot sottomarini sono utilizzati per diversi compiti, quali l'ispezione di strutture sommerse, la prospezione dei fondali alla ricerca di relitti, o per altri usi di ricerca e salvaguardia dell'ambiente sottomarino. Possono essere dotati di braccia e si muovono spinti da eliche o idrogetti.

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/Untitled-5_5.jpg)

### Aereo

Vengono anche chiamati **droni** ed hanno un uso militare o civile. Questi ultimi sono prevalentemente dei **quadricotteri**, cioè dotati di quattro eliche a due a due contro-rotanti per assicurare l'equilibrio.

All'inizio venivano utilizzati prevalentemente per scopi ludici, mentre ora svolgono molte altre funzioni: dalle riprese aeree per uso cinematografico o sportivo, al sorvolo di zone investite da catastrofi naturali (terremoti, inondazioni, incendi ecc.), dal monitoraggio ambientale, all'uso in agricoltura per stimare lo stato delle colture, dalla consegna di pacchi o generi di prima necessità, all'ispezione di aree remote. 

![](/assets/imgs/2017-06-15-Definizioni_robot_rt.md/Q450-quadcopter-kopen.jpg)

## Utilizzo

I robot possono essere classificati anche in relazione all'uso a cui sono destinati.

Ne posso elencare molti e sicuramente ne dimentico altrettanti. I principali sono 

- Robot industriali (settore della **Robotica Industriale**): 
	
	è il settore tecnologicamente più maturo e con una storia più lunga; come abbiamo visto, si tratta prevalentemente di manipolatori industriali utilizzati all'interno di linee di produzione. Recentemente molte aziende di robotica stanno sviluppando piattaforme mobili da utilizzare come trasporto tra le celle di lavorazione, sia all'interno di magazzini e aree logistiche  

- Robot di servizio (settore della **Robotica di Servizio**):
	
	è il settore che negli ultimi anni sta avendo una sviluppo tumultuoso e che rappresenta un grosso mercato futuro. Si possono individuare alcuni sottosettori

	- Robot per esplorazione. Si tratta di robot mobili progettati per l'esplorazione di altri corpi del Sistema Solare, di aree sottomarine o con condizioni estreme (interno di vulcani, zone artiche o antartiche, ecc.). 

	- Robot per usi logistici. Sono utilizzati per il trasporto di merci all'interno di depositi o magazzini, per la pulizia di grandi aree industriali e altro. Si tratta il più delle volte di robot a ruote, privi di organi di presa, anche se in futuro si pensa di integrarli con piccoli bracci per manipolazione. 

	- Robot per telepresenza. Permettono di accedere ad eventi lontani da parte di utenti che possono così partecipare senza essere fisicamente in loco. Sono simili a soluzioni di teleconferenza, solo che qui la videocamera è montata su una base mobile, libera di muoversi a richiesta dell'utente. 

	- Robot per sorveglianza, monitoraggio, sicurezza e prevenzione. Il settore ha un interesse notevole, ed è orientato sia alla sicurezza di grandi aree "critiche", come aeroporti, eventi sportivi, sia al monitoraggio di dell'inquinamento in aree abitate o colpite da disastri naturali   
 
	- Robot medici. Rappresentano un settore anch'esso molto interessante e in forte espansione e includono robot chirurgici, robot per la riabilitazione motoria, protesi robotiche, supporto a pazienti colpiti da malattie degenerative o neurologiche. 

	- Robot per supporto alle vendite. Alcuni grandi magazzini ed alberghi stanno sperimentando robot mobili che svolgono funzioni di assistenza al cliente, come l'indicazione degli scaffali di prodotti specifici o il recapito di colazione o pranzo direttamente in camera attraverso fattorini robotici.
 
- Robot per usi domestici. 
 
	- Robot di pulizia. Il primo esempio di robot di servizio è stato proprio un robot mobile per la pulizia  autonoma all'interno di un comune appartamento; avrete senz'altro capito che mi riferisco a Roomba, venduto in miglia di esemplari e imitato da molti. Da questo primo esempio di robot di servizio ne sono seguiti molti altri per la pulizia di grandi spazi pubblici, di piscine ecc. 
 
	- Assistenza ad anziani soli. Con l'invecchiamento della popolazione negli stati tecnologicamente più avanzati, i robot sono pensati per accompagnare e sostenere nella vita di tutti i giorni gli anziani soli o altri soggetti che altrimenti potrebbero essere destinati a condurre gli ultimi anni della loro vita lontani dal loro ambiente domestico.

	- Robot per intrattenimento e gioco. Di solito si tratta di piccoli robot con ruote o zampe o cingoli che presentano un aspetto simpatico e rassicurante e interagiscono con segnali sonori con gli utenti, che possono essere bambini o adulti. Sembra che ci sia in futuro uno spazio per giochi basati su piccoli robot fisici integrati in ambienti di realtà aumentata.


# Conclusione

Le tipologie e gli utilizzi dei robot sono limitate solo dalla fantasia dei progettisti. L'intelligenza artificiale, lo sviluppo del learning basato sui big data, l'uso della cloud, la ricerca su nuovi materiali, i  futuri computer basati su [dispositivi neuromorfi](http://www.treccani.it/enciclopedia/dispositivi-neuromorfi_%28Dizionario-di-Medicina%29/), tutto questo spingerà la robotica verso strade che è difficile immaginare ora.

Su tutte le attività connesse alla robotica grava però una paura ... la paura che l'automazione in generale, e i robot in particolare, possano far crescere la disoccupazione in molte fasce di attività, ed escludere da una vita attiva vasti settori della società.  



