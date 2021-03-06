## Tutorial hardware - Come costruire il robot Dotbot ##


Qui di seguito un breve tutorial su come assemblare il robot Dotbot. In questo tutorial ci dedichiamo ad assemblare i pezzi del robot e stampare i pezzi necessari. **Un grazie speciale a Michele Maffucci da cui ho preso gran parte (o quasi tutto) per questo tutorial!** Vedi gli altri tutorial per la configurazione e la programmazione dei dotbot.

Iniziamo a stampare con una stampante 3D i seguenti file STL:
* 2 X [db-ball_caster.stl] (https://github.com/sgabello1/Dotbot-Kit-e-Tutorial/blob/master/db-ball_caster.stl)
* 1 X [db-bottom.stl] (https://github.com/sgabello1/Dotbot-Kit-e-Tutorial/blob/master/db-bottom.stl)
* 1 X [db-breadboard.stl](https://github.com/sgabello1/Dotbot-Kit-e-Tutorial/blob/master/db-breadboard.stl)
* 1 X [db-supports.stl] (https://github.com/sgabello1/Dotbot-Kit-e-Tutorial/blob/master/db-supports.stl ) [ **il file è unico ma i supporti da stampare sono 4**]
* 1 X [db-top.stl] (https://github.com/sgabello1/Dotbot-Kit-e-Tutorial/blob/master/db-top.stl)
* 8 x [db-rect.stl] (https://github.com/sgabello1/Dotbot-Kit-e-Tutorial/blob/master/v04-db-dist-25-mm.stl)

## La lista dei componenti ##
*  4 giunti 25 mm x 3mm
*  30 viti M3 da 10 mm (oppure 5 mm)
*  4 viti M3 da 30 mm
*  10 bulloni M3
*  2 biglie di vetro
*  2 motorini CC e  2 ruote [link per acquistarli] (http://eud.dx.com/product/3-7-2v-dual-axis-tt-gear-motor-65mm-blue-rubber-wheel-for-smart-car-844443000)
*  1 scheda driver motori [link per acquistarli] ( http://eud.dx.com/product/hg7881-two-channel-motor-driver-board-dark-blue-2-5-12v-2-pcs-844407060)
*  1 batteria power bank [link per acquistarli] (https://www.amazon.it/RAVPower-Caricabatterie-Tecnologia-Universale-Smartphone/dp/B00YA01MC6/ref=sr_1_22?ie=UTF8&qid=1479834997&sr=8-22&keywords=batteria+esterna) 
*  1 breadboard da 400 fori
*  1 una batteria alcalina da 9 Volt (opzionale - per alimentare i motori in parallelo al Raspberry)

Il kit smontato e con tutti i suoi componenti sarà più o meno così:

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/KitTable.jpeg)

Iniziamo a montare!

## 1 - Montaggio dei motori

(dal blog di Michele Maffucci)


![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-10.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-11.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-12.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-13.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-14.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-15.jpg)

## 2 - Montaggio delle ruote ominidirezionali realizzate con delle biglie di vetro##

Qui potete montare i giunti esagonali come consiglia il blog di Michele Maffucci oppure sostinuirli con i giunti a forma di parallelepipedo (db-rect.stl). Se prendete questa strada otterrete una cosa così:

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/giuntiPrinted.jpeg)

Altrimenti comunque il montaggio non cambia se sostituite al giunto stampato quello esagonale!

![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-16.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-17.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-17.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-18.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-19.jpg)


## 3 - Montaggio batterie - Inserimento driver motori - Inserimento giunti stampati in 3d per secondo livello##

Smontate temporaneamente le ruote per facilitare il montaggio semplicemente tirandole.

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/DriverEbatterie.jpeg)

Ora inserite i fili di comando dei motori. Sono due per motore, tenendo conto che i pin del driver (c'è scritto comunque sopra) sono disposti cosi: 
* pin 1 e 2 - controllo motore 1 
* pin 3 e 4 - ground e alimentazione
* pin 5 e 6 - controllo motore 2


## 4 - Fissaggio breadboard ##

(dal blog di Michele Maffucci)

![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-23.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-24.jpg)
![] (http://www.maffucci.it/wp-content/uploads/2016/03/DotBot-25.jpg)

# 5 - Secondo livello ##

Ok ora inseriamo il Raspberry sopra i propri supporti.

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/7.jpeg)
![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/9.jpeg)
![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/10.jpeg)

# 6 -Montate il tutto e fate i collegamenti ##

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/15.jpeg)

Il raspberry ha i pin configurati così:

![]  (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/RP2_Pinout.png )

Nel nostro caso abbiamo i pin 3,5 per gli input e 4,6 Power e Ground per alimentare la breadboard. I pin 7,11,12 per i LED e 15,16 motore 1 23,24 motore 2.
