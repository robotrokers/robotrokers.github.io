---
layout: post
title:  "Emabot: trasformare una macchina radiocomandata in un robot"
date:   2017-06-26
date:   2017-06-26
author: Emanuele Paiano
categories: Makers
---


Introduzione
============

Con l’evoluzione delle varie board di sviluppo e dei sistemi embedded, oggi è estremamente facile assemblare piccoli robot programmabili. E’ possibile tirar su delle piattaforme hardware che ci consentono di sperimentare diversi tipi di algoritmi per la robotica, come la navigazione o il semplice controllo remoto. Se consideriamo i costi contenuti dei vari componenti in commercio, ci rendiamo conto che il progetto diventa ancora più realizzabile e alla portata di molte tasche.

Intuitivamente, possiamo paragonare un semplice robot mobile ad un piccolo computer dotato di sensori e attuatori: i primi sono dispositivi di input in grado di percepire lo stato dell’ambiente, mentre i secondi possiamo considerarli dei dispositivi di output che modificano tale stato (compresa la posizione del robot), in base a delle istruzioni contenute in memoria.

![image](/img/01.jpg)

Prendendo spunto da una mia esperienza personale, in questa serie di articoli vedremo come realizzarne uno, equipaggiato con:

-   sensori ultrasuoni per riconoscere gli ostacoli,

-   webcam USB dotata di servomotori,

-   altoparlante per permettergli di parlare pronunciando delle frasi preimpostate.

Il telaio può essere recuperato da una vecchia macchina radiocomandata oppure è possibile acquistarne uno già pronto. Il nostro robot avrà in tutto 4 ruote e due motorini: due posteriori per la trazione e due anteriori per lo sterzo, il quale viene gestito da un singolo motorino. La board di riferimento è Raspberry Pi accompagnata da Arduino Nano per una gestione più efficiente dei motori.

Il controllo remoto, consiste in un server tcp che gestisce i singoli comandi ricevuti da uno smartphone o pc (su cui gira il client), mentre per il flusso della webcam si farà uso di un server http per lo streaming video.

All’eventuale domanda sul perchè non ci si limita ad Arduino, la risposta metterebbe in evidenza tutti i vantaggi di avere installato Linux in un robot: Raspbian lo rende scalabile e flessibile, permettendo di aggiungere o implementare diverse funzionalità aggiuntive, tra cui:

-   far parlare il robot installando espeak, noto sintetizzatore vocale per linux;

-   configurare un server vpn e fare in modo che il robot venga gestito fuori dalla nostra rete locale;

-   implementare un piccolo sistema di sorveglianza remota direttamente nel robot, con notifica email per eventuali movimenti sospetti (rendendolo un \<\<robot da guardia\>\>).

-   possiamo scegliere, tra i linguaggi supportati da raspberry, quello che ci fa più comodo per scrivere il server;

-   fare quasi tutto quello che si può fare con un raspberry (immaginate di dare un comando vocale al robot per riprodurre un mp3 in memoria).

Implementare tali caratteristiche con un microcontrollore, appare molto più complesso. Il prezzo da pagare si riversa sui consumi energetici che saranno decisamente maggiori.

![image](/img/02.jpg)

Una prima versione: un Raspberry con le ruote
---------------------------------------------

Il primo passo è quello di assemblare un \<\<Raspberry dotato di ruote e webcam\>\>. Per ora ignoriamo servomotori e sensori, che saranno aggiunti successivamente.

La lista del materiale occorrente prevede:

-   Un Raspberry A+, ma andrebbe bene qualunque versione, tenendo conto però, che le versioni B e B+ hanno consumi energetici più elevati (600mAh contro 1500-3000mAh);

-   Un dongle Wifi per connettere il raspi ad una rete wireless o per impostarlo come access point. Tale componente non è necessario se usiamo Raspberry Pi 3 (ha la wifi integrata);

-   Un hub usb con almeno 3 porte: una per connettere la cam, un’altra per l’adattatore wifi e una di riserva. Tale componente è indispensabile se usiamo il Raspberry A+, in quanto quest’ultimo dispone di una sola porta usb;

-   Un Arduino Nano, comandato da Raspberry, si occuperà di gestire il modulo motori ed eventuali attuatori aggiuntivi (luci e servomotori per la webcam).

-   Un modulo L298N che permette di gestire i motori di marcia e sterzo, oltre che ad alimentare Arduino;

-   Un convertitore di livello per far comunicare Raspberry e Arduino. Raspberry lavora a 3.3 V, mentre Arduino a 5. Se non si converte tale voltaggio, si rischia di danneggiare seriamente il Raspi. Come alternativa, i più esperti potranno far uso di un partitore di tensione;

-   Batteria ricaricabile da 9-12 Volt e 2500mAh. Per i test iniziali, è possibile utilizzare un alimentatore universale per notebook impostato a 12 Volt;

-   Un DC Step-Down per ridurre i 12 Volt in ingresso in 5 Volt per Raspberry. Come alternativa, i più esperti potranno realizzare un regolatore di tensione apposito, utilizzando un LM7805. Ovviamente tutte le masse (GND) andranno collegate tra loro altrimenti non funzionerà nulla.

*ALTERNATIVA*

-   Una batteria lipo da 7,4V per Arduino / Motori e un Powerbank da 5V per Raspberry, ricordando di collegare la massa (GND) del Raspberry a quella di Arduino.

Per avere un’idea del funzionamento generale del del robot, basta fare riferimento al seguente schema:

![image](/img/03.jpg)

la webcam è collegata ad una porta USB di Raspberry, Arduino al GPIO del raspi e i motori al modulo L298N che a sua volta sarà collegato ad Arduino. Il motivo per cui non si collega il modulo direttamente al GPIO, è dovuto al fatto che Raspberry non è un sistema realtime (a meno che non si faccia uso di schede aggiuntive): ciò lo rende instabile di fronte a task che devono essere eseguiti e terminati in intervalli di tempo limitati. Infatti, può succedere che il sistema operativo dia maggiore priorità a processi che non riguardano la gestione dei motori, causando una risposta ritardata ai comandi ricevuti (per esempio, il robot potrebbe sterzare in ritardo). Arduino fa da tramite riducendo le operazioni da eseguire, quindi raspberry dovrà limitarsi ad inviare i comandi sulla porta seriale, al resto ci pensa il microcontrollore. Delegando la gestione degli attuatori, si risolve il problema dell’instabilità, dovuta all’impiego di un sistema che non sia realtime. Altre alternative (già pronte) sono le schede HAT, fatte appositamente per permettere a Raspberry di supportare Servo e Motori CC senza problemi, purtroppo tali schede non sono a disposizione dell’autore. Andiamo a vedere nel dettaglio come saranno effettuati i collegamenti di Arduino al modulo L298N.

Collegamento motori
-------------------

La prima componente da assemblare è la parte relativa ad Arduino e i Motori CC, seguito dalla realizzazione di un semplice sketch. Prima di procedere, diamo un’occhiata alle caratteristiche del modulo motori.

![image](/img/04.jpg)

### Il modulo L298N

Il modulo L298N (figura sopra), detto anche H-Bridge, è un modulo utilizzabile per la gestione dei motori a corrente continua. Esso è composto da un ingresso a 12 Volt, due uscite a 3 V per i motori, e un’uscita a 5 Volt per alimentare la scheda di controllo. Purtroppo, quest’ultima, non può essere utilizzata per alimentare Raspberry (l’amperaggio fornito è insufficiente) ma va benissimo per Arduino. Tuttavia, non sarà utilizzata per le fasi di test, infatti ad Arduino collegheremo solo la massa (GND) ma non l’alimentazione, in quanto il microcontrollore sarà alimentato dalla stessa porta USB del PC. Gli ingressi per la gestione dei motorini sono:

-   Enable Motor A (ENA): E’ l’ingresso utilizzato per impostare il PWM del motore A, quindi anche la sua velocità. Se messo in corto con il pin superiore (5V+), la velocità rimarrà constante (al valore massimo). Diversamente, possiamo regolare gli impulsi da Arduino e farla variare (sfruttando il [Duty Cycle](https://it.wikipedia.org/wiki/Duty_cycle));

-   Enable Motor B (ENB): vale lo stesso discorso di ENA, ma per il motore B.

-   Gli ingressi IN1 e IN2 funzionano come mostrato in Tabella sotto. Lo stesso discorso vale per IN3 e IN4, solo che viene gestito il motore B.

| Azione motore A    |     IN1     |  IN2 |
|----------|:-------------:|------:|
| fermo |  low | low |
| ruota in senso orario |    high   |   low |
| ruota in senso antiorario | low |    high |
    

![image](/img/05.jpg)

### Montaggio e sketch

I collegamenti da effettuare tra i pin di Arduino e quelli del H-Bridge sono descritti nella tabella seguente

| PIN ARDUINO    |      PIN H-BRIDGE |
|----------|------:|
| GND | GND |
| D9 | ENA |
| D3 | ENB |
| D7 | IN1 |
| D6 | IN2 |
| D5 | IN3 |
| D4 | IN4 |

Nell'immagine sopra, possiamo vedere lo schema completo. Il motore cc utilizzato è il Mabuchi FA130 a 3V (spesso presente nei giocattoli elettrici, come trenini e macchine da pista polistil), ma il modulo ne supporta anche altri tipi. Montato il circuito, possiamo pensare all’implementazione dello sketch di Arduino.

Le funzioni che utilizzeremo sono *analogWrite()* per impostare il valore di ENA e quello di ENB, mentre *digitalWrite()* lo utilizzeremo per inviare i valori *HIGH* e *LOW* agli altri pin.

Il codice seguente è lo sketch da caricare in Arduino.

    /*
     * Car Arduino simple sketch
     * 2015 - Emanuele Paiano
     */     
     /* Primo motore */
     const int enA = 9;
     const int in1 = 7;
     const int in2 = 6;

     /* Secondo motore */
     const int enB = 5;
     const int in3 = 7;
     const int in4 = 4;
     
     /* Massimo valore PWM motorino di Marcia*/
     const int kMaxPwm=200;

    /* valore PWM Sterzo */
    const int kWheelPwm=150;

    /* SpeedVal Max. Massimo valore delle "marce" */
    const int kMaxSpeed=5;

    /* SpeedVal attuale (in gergo marcia) */
    int currentSpeed=4;

    void setup() {
      /* Uscite Modulo L298N */
      pinMode(enA, OUTPUT);
      pinMode(enB, OUTPUT);
      pinMode(in1, OUTPUT);
      pinMode(in2, OUTPUT);
      pinMode(in3, OUTPUT);
      pinMode(in4, OUTPUT);

     /* Inizializzo la comunicazione seriale usb a 9600 bit/sec */
      Serial.begin(9600);

     /* Svuoto il buffer della seriale */
      Serial.flush();
    }


    void loop() {
      if (Serial.available())
       {
        /* Leggi byte porta seriale */
        char c = Serial.read();
        switch(c)
        {
                 /* se ho letto una 'A' vado avanti */
          case 'A':
                    forward();
                    Serial.println("FORWARD OK");
                    break;
              /* se ho letto una 'a' vado in retromarcia */
         case 'a':
                    reverse();
                    Serial.println("REVERSE OK");
                    break;
             /* se ho letto una 's' mi fermo */
         case 's':
                    stopMotorA();
                    Serial.println("STOP OK");
                    break;
                    
        /* se ho letto una 'L' giro a Destra */
         case 'L':
                    turnRight();
                    Serial.println("RIGHT OK");
                    break;
                    
          /* se ho letto una 'l' giro a sinistra */
         case 'l':
                    turnLeft();
                    Serial.println("LEFT OK");
                    break;
                    
         /* se ho letto una 'S' raddrizzo lo sterzo */
         case 'S':
                    straight();
                    Serial.println("STRAIGHT OK");
                    break;

         /* se ho letto un '+' aumento velocità */
         case '+':
                    currentSpeed++;
                    currentSpeed=constrain(currentSpeed, 1, kMaxSpeed);
                    Serial.println(currentSpeed);
                    break;
         /* se ho letto un '-' riduco velocità */
         case '-':
                    currentSpeed--;
                    currentSpeed=constrain(currentSpeed, 1, kMaxSpeed);
                    Serial.println(currentSpeed);
                    break;
                 }
           }
    }

    /* Avanti */
    void forward() {
       stopMotorA();
       digitalWrite(in1, HIGH);
       digitalWrite(in2, LOW);
       analogWrite(enA, getSpeedVal(currentSpeed));
      }

    /* recupera corretto valore di velocità */
    int getSpeedVal(int value)
    {
      int val=0, mult=kMaxPwm/kMaxSpeed;
      value=constrain(value, 0, kMaxSpeed);
      val=value*mult;
      val=constrain(val, 0, kMaxPwm);
      return val;
     }

    /* inverti marcia */ 
    void reverse() {
        stopMotorA();
        digitalWrite(in2, HIGH);
        digitalWrite(in1, LOW);
        analogWrite(enA, getSpeedVal(currentSpeed));
    }

    /* Ferma motore di marcia */
    void stopMotorA() {
       digitalWrite(in1, LOW);
       digitalWrite(in2, LOW);
       analogWrite(enA, 0);
    }

    /* Sterzo a destra */
    void turnRight() {
         straight();
         delay(100);
         analogWrite(enB, kWheelPwm);
         digitalWrite(in3, HIGH);
         digitalWrite(in4, LOW);
    }

    /* sterzo a sinistra */
    void turnLeft() {
      straight();
      delay(100);
      analogWrite(enB, kWheelPwm);
      digitalWrite(in3, LOW);
      digitalWrite(in4, HIGH);
    }

    /* raddrizza sterzo */
    void straight() {
       digitalWrite(in3, LOW);
       digitalWrite(in4, LOW);
       analogWrite(enB, 0);
    } 

Il funzionamento del programma è relativamente semplice: i comandi sono semplici caratteri ricevuti sulla porta seriale e, in base al byte ricevuto, viene richiamata una funzione corrispondente ad un’azione da eseguire (*forward, reverse, turnLeft, turnRight, stop e straight*). I comandi possono essere riassunti nella seguente tabella:


| COMANDO    |      AZIONE |
|----------|------:|
| A | avanti |
| a | indietro |
| L | sterzo destra |
| l | sterzo sinistra |
| s | stop |
| S | raddrizza sterzo |
| + | aumenta velocità |
| - | riduci velocità |


I possibili livelli di velocità variano da 1 a 5. Si è preferito usare questi valori fittizzi (anzicchè quelli compresi tra 0 a 255), per semplificare l’aumento e la riduzione della velocità utilizzando i caratteri ’+’ e ’-’. Il livello iniziale è 4, in quanto se c’è scarsa trazione, il robot non si muove. Inoltre, per allungarne la vita, si è preferito impostare a 200 il limite massimo del pwm di marcia e a 150 quello dello sterzo: valori più alti sono inutili, data la struttura della nostra macchina (dare troppa potenza al motorino dello sterzo potrebbe essere dannoso).

Per verificare se abbiamo fatto tutto correttamente, possiamo collegare Arduino alla porta usb del PC, alimentiamo il modulo (tramite alimentatore o batterie) e proviamo ad inviare i caratteri con il monitor seriale dell’ide di Arduino, impostando la velocità a 9600bps. Se i motorini girano, e il modulo risponde correttamente ai comandi, allora possiamo passare alla tappa successiva: il collegamento del Raspberry.

Collegare il Raspberry
----------------------

Per collegare il Raspberry, abbiamo bisogno di un convertitore dei livelli di tensione (schema successivo, in alto a destra), in particolare sul pin di ricezione del raspi (UART\_RXD). L’elenco dei Pin è visibile sotto.

![image](/img/06.jpeg)

Il collegamento da realizzare è di tipo UART: consiste nel collegare il Pin TX di Arduino al Pin UART\_RXD di Raspberry, e il pin UART\_TXD al pin RX di Arduino come mostrato in figura sotto, facendo riferimento ai pin specificati nella tabella successiva. Il metodo è molto simile a quello della costruzione di un cavo null modem, ma le controparti hanno livelli di tensione differenti (Arduino lavora a 5V, mentre Raspberry a 3,3).

![image](/img/07.jpg)


| PIN ARDUINO  | CONVERTER HV | CONVERTER LV | PIN RASPI |
|----------|:------:|:------:|------:|
| TX | RXI | RXO | UART_RXD |
| RX | TXO | TXI | UART_TXD |
| GND | GND | GND | GND |
| 5V | HV | LV | 3,3V |


Collegato il raspberry, non resta che collegare anche il pin vin di Arduino al pin 5V del modulo L298N (staccate arduino dalla usb del pc), come mostrato nello schema successivo. Per alimentare raspberry, possiamo usare un alimentatore da smartphone (purchè sia a 5V), almeno per le fasi di test. Successivamente, si farà uso di un modulo dc step down: si prenderà parte della tensione globale del sistema, e la si ridurrà a 5 V per Raspberry. In questo modo, avremo due diramazioni a partire dalla sorgente a 12V: una a 5V per Raspberry e l’altra a 12 per alimentare il modulo motori (insieme al microcontrollore). L’importante è che fate arrivare almeno 9V (meglio 12) e 2400mAh in ingresso.

![image](/img/08.jpg)

Prima configurazione e test del collegamento
--------------------------------------------

Dopo aver configurato Raspbian, ci limiteremo a testare i motorini da Raspbian. Forse, non tutti sanno che sulla linea seriale *UART*, di default c’è un attivo un processo getty che permette il login: dobbiamo disattivarlo o il nostro circuito avrà dei malfunzionamenti. Per fare ciò apriamo il file /etc/inittab e troviamo la stringa

    T0:23:respawn:/sbin/getty -L ttyAMA0 115200 vt100

possiamo disattivarla aggiungendo il carattere \# per commentarla

    #T0:23:respawn:/sbin/getty -L ttyAMA0 115200 vt100

e salviamo il file. Inoltre, quando raspbian si avvia, tutte le informazioni vengono inviate sulla porta seriale, in quanto tale parametro viene passato al boot. Per disattivarlo, apriamo il file /boot/cmdline.txt e troviamo la riga simile a questa

~~~~ {breaklines="true" showstringspaces="false"}
dwc_otg.lpm_enable=0 console=ttyAMA0,115200 kgdboc=ttyAMA0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
~~~~

e rimuoviamo tutti i riferimenti a ttyAMA0, nel nostro caso la riga diventa

~~~~ {breaklines="true" showstringspaces="false"}
dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
~~~~

salviamo il file e riavviamo raspberry. Ovviamente tali impostazioni possono variare da una versione all’altra di raspbian, ma spesso sono simili. Ora si lancia minicom sulla porta */dev/ttyAMA0* con una velocità a 9600bps:

    minicom -b 9600 -o -D /dev/ttyAMA0

digitando i comandi, possiamo inviare i caratteri e vedere i motorini funzionare.

Riepilogo e conclusioni 
------------------------

Siamo partiti dal collegare i motori al modulo L298N. Abbiamo realizzato uno sketch per Arduino che riceve caratteri ascii e genera segnali high e low da mandare al modulo motori, per poi interfacciare tutto con raspberry in modo da ricevere i comandi da minicom.

A questo punto, possiamo pensare alla parte applicativa: l’idea è quella di scrivere un insieme di librerie e classi in un linguaggio che, agendo sul file /dev/ttyAMA0, gestisca i servo della cam e i motori di marcia. Si potrebbe pensare di scrivere una classe per ogni sensore e attuatore, in modo tale da arrivare a programmare il robot in stile oop, arrivando anche ad implementare un server tcp in qualunque linguaggio. L’obiettivo finale di questo progetto, è quello di arrivare a ricevere i caratteri ascii direttamente da un client remoto.

I comandi saranno inviati da un’apposita app Android, configurata per pilotare il robot via wlan. Su Google Play alcune sono gratuite e con supporto streaming da cam: una app che fa a caso nostro, può essere [WIFI TCP/UDP Controller](https://play.google.com/store/apps/details?id=udpcontroller.nomal&hl=it).

 LINKS e SORGENTI
------------------------
[Repository](https://github.com/emanuelepaiano/emabot/)

[Versione PDF](https://github.com/emanuelepaiano/emabot/blob/master/Emabot_ITA_part%201.pdf)


Licenza
=======

L’autore declina ogni responsabilità relativa alle eventuali conseguenze (hardware danneggiato o altro) delle informazioni contenute nel presente articolo. E’ consentita la stampa, diffusione e riproduzione del testo integrale, purchè venga citato l’autore. I sorgenti del progetto sono coperti dai termini della licenza GNU-GPL3.