---
layout: post
title:  Matrici e vettori - parte 3
subtitle: Le basi matematiche della cinematica dei robot
date: 2017-09-06 00:00:00
author: Basilio Bona
categories: Teorica
---
$$
\def\i{\boldsymbol{i}}
\def\j{\boldsymbol{j}}
\def\k{\boldsymbol{k}}
\def\a{\boldsymbol{a}}
\def\b{\boldsymbol{b}}
\def\f{\boldsymbol{f}}
\def\v{\boldsymbol{v}}
\def\omvet{\boldsymbol{\omega}}
\def\tauvet{\boldsymbol{\tau}}
\def\calR{\mathcal{R}}
$$

Come promesso nell'ultimo post prima delle vacanze estive, vi parlerò dei **vettori fisici** e delle due diverse tipologie di questi: i **vettori polari** e i **vettori assiali**.

Cosa intendo per **vettori fisici**? Sono quei vettori che rappresentano matematicamente le grandezze fisiche che possono tornare utili alla rappresentazione della cinematica e della dinamica dei robot. 

Ci sono molti tipi di grandezze fisiche; alcune non sono rappresentabili come vettori. Ad esempio, la temperatura è una grandezza fisica **scalare** perché non ha una direzione e un verso, ma solo un'intensità. Altre invece sono dotate di intensità, direzione e verso; in robotica se ne utilizzano relativamente poche:

 1. velocità lineari, che indichiamo con il simbolo $\v$
 2. forze lineari, che indichiamo con il simbolo $\f$
 3. velocità angolari, che indichiamo con il simbolo $\omvet$
 4. forze angolari, dette anche coppie o momenti , che indichiamo con il simbolo $\tauvet$

Le velocità lineari sono le derivate delle coordinate di posizione (vettori geometrici) dei punti materiali che ci interessano, mentre le velocità angolari sono le derivate delle coordinate angolari dei sistemi di riferimento che ci interessano. Parleremo diffusamente delle coordinate angolari in un post