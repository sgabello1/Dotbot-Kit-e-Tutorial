## Iniziamo a programmare! ##
Ok, abbiamo visto la parte teorica e ora è il momento di buttarsi nel vivo della programmazione! Questo tutorial spiega **una volta che il robot è configurato correttamente** (altrimenti seguite [**il tutorial di configurazione del kit minimale**](http://www.hotblackrobotics.com/forum/support/6))  come programmarlo.

##  Connettete il robot


##  L'IDE di sviluppo
Andate su http://www.hotblackrobotics.com/cloud/sketch/ e troverete due sezioni: una "Programs", sono i vostri programmi e "Examples" sono gli esempi che trovate già in piattaforma. Questi potete visualizzarli col tasto "View" e clonarli nella vostra sezione "Programs" così che possiate modificarli ed utilizzarli. Notate che per clonarli premete sul tasto "Clone" e su questo c'è il numero di volte che è stato clonato. Questo per dare una specie di indice di popolarità sui programmi più clonati, e quindi più apprezzati :) vedremo dopo che, se volete, anche i vostri programmi possono essere condivisi agli altri utenti in piattaforma e più volte il vostro programma sarà clonato più significa che avete fatto un ottimo lavoro!

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/programs.PNG)

Quindi per iniziare col primo esempio clonate "**led_cn**t" dalla sezione examples a vedrete che comparirà in programs. Premete a questo punto sul pulsante "edit" e vedrete che potete visualizzare il codice. 

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/esempio_led.PNG)

In alto a destra avete questi pulsanti molto utili:

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/pulsanti_edit.PNG)

* run: esegue il codice sul robot connesso (ricordatevi sempre però prima di premere questo pulsante di salvare! - pulsante successivo)
* save: salva le modifiche del codice
* shell: apre una shell e ti dice cosa sta succedendo, importante anche in caso di debug
* download: vi permette di scaricare il codice
* edit info: vi permette di cambiare nome del programma, aggiungere una breve descrizione al programma es "questo codice fa accendere un led" e se volete rendere pubblico il vostro codice. Rendere pubblico significa che altri utenti lo possono visualizzare e poi clonare nella proprio profilo 

Ora (salvate per sicurezza col tasto save) ed eseguite il codice "led_cnt" con il tasto esegui. Si aprirà la shell che vi comunicherà che il nodo è in esecuzione "node running".
A questo punto per verificare che il programma effettivamente sta funzionando, ritornate nella finestra "ROS". Andate nella sezione "Topics List" e premete il pulsante "echo" nel topic "/hotbot/led" (ovvviamente hotbot è il robot di default se nel vostro caso avete un altro nome sarà diverso - ad es. dotbot ecc). Si aprirà sotto una finestra che visualizza i messaggi in tempo reale che stanno passando nel topic, in questo caso è un messaggio composto da tre campi  "led1", "led2" e "led" perchè vogliamo con un messaggio solo controllare i 3 led del robot. Vederete che il campo del led1 cambia continuamente alternando true/false facendo così accenderlo e spegnerlo.

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/led_topic.PNG)
