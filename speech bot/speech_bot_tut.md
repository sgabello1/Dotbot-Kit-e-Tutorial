## HB Cloud Tutorial - Speech Bot ##

Un'applicazione cloud interessante e molto divertente è far parlare il vostro robot! 
Tecnicamente si chiama TTS - [text to speech](https://en.wikipedia.org/wiki/Speech_synthesis), o *sintesi vocale*. I sistemi TextToSpeech (letteralmente da testo a voce) consistono appunto nel convertire un testo e riprodurlo da un sintetizzatore vocale tramite un computer. Ovviamente le applicazioni nella robotica sono tantissime, e quello che faremo è gettare le basi per costruire un assistente robotico con cui potrete dialogare!

Iniziamo quindi a far "parlare" il computer tramite ROS. Tramite la Web App, che trovate qui [http://www.hotblackrobotics.com/cloud/webgui/speech](http://www.hotblackrobotics.com/cloud/webgui/speech) oppure nella tendina "Apps", abbiamo un modulo in javascript in grado di sintetizzare la voce umana. Premendo sul tasto "Bot" il computer ci accoglierà con un caloroso "Eccomi!". Da questo momento vedrete nella sezione "Console ROS" la creazione di un nuovo topic ```/<nome_del_vostro_robot>/to_speech ```


![](https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/speech%20bot/TextToSpeech.jpg)
