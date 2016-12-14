## Come collegare un robot comprato da Tiger (Spider Robot) in piattaforma cloud !! ##

Qui vi spiegherò come modificare un robot comprato da Tiger e collegarlo in piattaforma! Nel mio caso ho comprato uno Spider Robot per ben 7 Euro!:)

![](https://pbs.twimg.com/media/CWmEXs7WUAABSLl.jpg)

Oltre questo avrete anche bisogno di:
* un power bank per cellulare da 5 Volt io ho usato [questo](http://www.dx.com/p/cylinder-shaped-external-6000mah-emergency-power-battery-charger-for-iphone-cell-phone-silver-206652#.WFFUEh9ifCI) ma potete usare anche un power bank da 9 volt
* un ponte ad H. Io ho usato [questo] (http://eud.dx.com/product/hg7881-two-channel-motor-driver-board-dark-blue-2-5-12v-2-pcs-844407060) ma anche in questo caso potete scegliere quello che volete. Qualcuno li costruisce anche a mano mettendo insieme 4 transistor!
* un Raspberry PI 3
* cavetti con connettori femmina-femmina
* fascette da idraulico
* un pezzo di cartone ;) 

E otterrete SpiderBot in cloud!

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/tut/SpiderBotCloud2.jpeg)

Una volta montato lo Spider Bot come dalle istruzioni di Tiger, prendete un pezzo di materiale rigido  (io ho usato un cartone) e ne ritagliate un rettangolo per farci stare il Raspberry. Poi tagliate la parte inferiore in modo da creare una linguetta centrale che andrete a far passare dentro l'appiglio di plastica del robot. Lo ripiegate dentro e lo fissate, io ho usato una spillatrice. 

Poi come si vede in figura fissate il ponte ad H (hg7881) con una fascetta sul davanti del robot.  

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/tut/Cartone.jpeg) 

Effettuate i collegamenti. Il filo rosso (+) lo inserite nel mammut del Motor A di destra nel ponte ad H e il nero (terra) nel mammut di sinistra. Con un cacciavite chiudete i mammut per far bene contatto. A questo punto prendete dei cavetti femmina-femmina e, due di questi (il mio rosso e marrone) li usate come alimentazione del ponte ad H e altri due li mettete nei pin di controllo del Motor A.

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/tut/ponteH.jpeg)
