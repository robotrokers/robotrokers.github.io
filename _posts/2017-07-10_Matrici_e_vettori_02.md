---
layout: post
title:  Matrici e vettori - parte 2
subtitle: Le basi matematiche della cinematica dei robot
date: 2017-07-20 00:00:00
author: Basilio Bona
categories: Teorica
---
$$
\def\i{\boldsymbol{i}}
\def\j{\boldsymbol{j}}
\def\k{\boldsymbol{k}}
\def\a{\boldsymbol{a}}
\def\b{\boldsymbol{b}}
\def\v{\boldsymbol{v}}
\def\calR{\mathcal{R}}
$$

Nel post precedente ho introdotto i vettori "**geometrici**", cioè quei vettori che contengono le coordinate di un punto geometrico rispetto ad un sistema di riferimento assegnato. 

Notiamo che usare la freccia come simbolo per caratterizzare questo tipo di vettori non è particolarmente corretto, perché un punto è un punto, mentre la freccia/vettore ha una direzione, un verso, che va dalla coda in A  alla punta in B e un lunghezza, detta anche **modulo** o **norma del vettore**

![](http://i.imgur.com/p82KHaj.png) 

In questo esempio la direzione è circa 45 gradi rispetto all'orizzontale mentre la lunghezza dipende dalla scala adottata per l'unità di misura. La scala è implicitamente assegnata dalla lunghezza dei vettori unitari $\i,\j,\k$ che compongono il sistema di riferimento utilizzato. 

Nel caso della figura, se il sistema di riferimento è quello mostrato,

![](http://i.imgur.com/EGfEXyr.png)

allora il vettore $\v_{AB}$  è 

$$
\v_{AB}= \left( \begin{array}{l} 1 \\ 1 \end{array}  \right)
$$

ed ha una lunghezza pari a $\sqrt{2}\approx 1,41$.

Torniamo a quanto detto prima, cioè che una freccia non è un punto. Eppure usiamo i vettori geometrici, che sono delle frecce, per rappresentare dei punti.

Le cose tornano se ci immaginiamo che il vettore geometrico rappresenti lo **spostamento** (in inglese, *displacement*) necessario per andare dall'origine del riferimento al punto geometrico considerato.

Allora nel caso del vettore che rappresenta la basilica di Superga rispetto al riferimento in Piazza Castello a Torino, possiamo dire che è necessario spostarsi di circa 6,286 km verso est e di circa 1,122 km verso nord per un cammino totale la cui lunghezza è (teorema di Pitagora)
$$
L=\sqrt{6.286^2+1.122^2}\approx 6.381 \text{ km}
$$

E ricordate che l'unità di misura chilometri si indica con **km** e non con **Km**.

Il calcolo è stato fatto considerando solo il piano orizzontale; se non trascuriamo la terza dimensione, poiché Piazza Castello si trova a 239 m sul livello del mare, mentre la Basilica di Superga a 672 m s.l.m, abbiamo uno scarto di 433 m. Il vettore $\v$ visto nel precedente post diventa allora tridimensionale:
$$
\v= \left( \begin{array}{c} 6286 \\ 1122 \\ 433 \end{array}  \right) \text{m}
$$

Se vogliamo trovare il vettore che rappresenta il punto geometrico $S$ non più rispetto a Piazza Castello $O$, ma rispetto al Politecnico $P$, dobbiamo calcolare la somma vettoriale
$$
\v_{PO}+\v_{OS}=\v_{PS}
$$
e quindi conoscere $\v_{PO}$.

Ma non basta; gli assi del riferimento in $P$, che indichiamo con $\calR_P$, per una qualche ragione che non conosciamo, sono stati orientati in modo diverso da quelli del riferimento in $O$, che indichiamo con $\calR_O$. In particolare $\calR_P$ è ruotato di 90 gradi in senso antiorario rispetto a  $\calR_O$. O viceversa $\calR_O$ è ruotato di 90 gradi in senso orario rispetto a  $\calR_P$

Quindi dobbiamo uniformare le rappresentazioni: o la somma va calcolata rispetto a $\calR_P$ oppure rispetto a $\calR_O$. Diamo la rappresentazione di $\v_{PO}$ nel sistema di riferimento $\calR_P$; essa vale

$$
[{\v_{PO}}]_{\calR_P}= \left( \begin{array}{c} 627 \\ -1365 \end{array}  \right)
$$

dove il segno "$-$" nella seconda componente del vettore sta ad indicare che dobbiamo muoverci  lungo l'asse $\j$ in direzione opposta a quella scelta come positiva, cioè verso in direzione est invece che ovest.

Se invece vogliamo calcolare la rappresentazione del vettore $\v_{PO}$ nel sistema di riferimento $\calR_O$; essa vale

$$
[{\v_{PO}}]_{\calR_O}= \left( \begin{array}{c} 1365 \\ 627 \end{array}  \right)
$$

Il vettore somma sarà dunque calcolato in $\calR_O$ (ricordandosi i risultati del post precedente) come
$$
\v_{PO}+\v_{OS}= \left( \begin{array}{c} 1365 \\ 627 \end{array}  \right)+
 \left( \begin{array}{c} 6286 \\ 1122 \end{array}  \right)=
  \left( \begin{array}{c} 7651 \\ 1749 \end{array}  \right)\text{ m}
$$

# Conclusioni

 - I **vettori geometrici**, cioè i vettori che rappresentano punti nello spazio, sono rappresentabili da frecce solo se li pensiamo come spostamenti dall'origine del riferimento al punto stesso.

 - La scelta del sistema di riferimento incide sulla rappresentazione del vettore: se cambia il riferimento, cambia la rappresentazione, compreso il suo modulo.
 
 - I vettori si sommano con la solita regola: ogni componente del vettore somma è la somma delle corrispondenti componenti dei vettori addendi
 
 $$
\a+\b=
\left( \begin{array}{c} a_1\\ a_2 \\ a_3\end{array}  \right)+
\left( \begin{array}{c} b_1\\ b_2 \\ b_3\end{array}  \right)=
\left( \begin{array}{c} a_1+b_1\\ a_2+b_2 \\ a_3+b_3\end{array}  \right)
 $$

 -  Il modulo $|\cdot|$ (o la norma $\|\cdot\|$ ) di un vettore si ottiene applicando il Teorema di Pitagora
 
 $$
 |{\a}|=\|\a\|=\sqrt{a_1^2+a_2^2+a_3^2}
 $$

	ma non bisogna sbagliare, infatti

 $$
 |{\a+\b}|=\|\a+\b\|=\sqrt{(a_1+b_1)^2+(a_2+b_2)^2+(a_3+b_3)^2}
 $$

	e non

$$
\sqrt{a_1^2+b_1^2+a_2^2+b_2^2+a_3^2+b_3^2} \qquad\text{orrore !!!}
$$

 - Se i vettori addendi sono rappresentati in più sistemi di riferimento, diversi per orientazione, bisogna ricondurli tutti allo stesso riferimento ... come? Attraverso un'operazione di rotazione, come spiegherò in un futuro post.

Adesso un commento finale: che relazione c'è tra quanto illustrato fino ad ora e la **cinematica** di un robot?

Per analogia, la Basilica di Superga è la punta operativa (TCP) di un robot, il riferimento Politecnico è il riferimento alla base del robot e Piazza Castello è un riferimento su un qualunque braccio intermedio.

Insomma, per calcolare la cinematica diretta di un robot occorre fissare tanti riferimenti quanti sono i bracci mobili, più uno sulla base fissa, e calcolare la posizione del TCP rispetto alla base fissa, sommando i vari vettori che rappresentano lo spostamento da un riferimento al successivo.

Bene, ho finito. Nel prossimo post che potrebbe apparire dopo le vacanze estive, parlerò dei **vettori fisici** e delle due diverse tipologie di questi: i **vettori polari** e i **vettori assiali**.

A presto.
