## Il fondamento della piattaforma di Cloud Robotics: Robotics Operating System ##

La base tecnologica su cui si basa la piattaforma di cloud robotics è [ROS (Robotic Operating System)] (http://wiki.ros.org/it). ROS è un framework software open source che permette lo sviluppo e la programmazione di robot. Fornisce le stesse funzioni di un sistema operativo come: astrazione dell'hardware, controllo dei dispositivi tramite driver, comunicazione tra processi, gestione delle applicazioni e altre funzioni di uso comune. Si presta particolarmente bene alle nostre esigenze legate all'internet delle cose poichè è un **sistema distribuito**, il che significa che diversi programmi sono distribuiti su robot differenti e comunicano tutti tramite la piattaforma.

Inoltre è particolarmente interessante perchè è utilizzato da tutti i principali sviluppatori software al mondo (sia accademici che industriali) come ad esempio Google, Stanford, ETH, MIT ecc.. Tant'è che è diventato lo *standard de fact0*.
Di conseguenza ha un enorme community molto competente pronta a risolvere problemi e bachi ad ogni momento e lo sviluppo di codice open source rende la comunità molto attiva.

Iniziamo a vedere come funziona!

Un’applicazione ROS è una rete di processi che scambiano dati in una rete di comunicazione composta da macchine diverse (gli oggetti dell'Internet dell cose o i robot).

Nodo: un singolo processo (programma in esecuzione) all’interno della rete ROS
Messaggio: struttura dati con cui usata per lo scambio di informazioni
Topic: canale all’interno del quale due o più nodi si scambiano messaggi

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/grapROS.png)

