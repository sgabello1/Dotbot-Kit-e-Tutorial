## HB Cloud Tutorial - Speech Bot ##

Un'applicazione cloud interessante e molto divertente è far parlare il vostro robot! 
Tecnicamente si chiama TTS - [text to speech](https://en.wikipedia.org/wiki/Speech_synthesis), o *sintesi vocale*. I sistemi TextToSpeech (letteralmente da testo a voce) consistono appunto nel convertire un testo e riprodurlo da un sintetizzatore vocale tramite un computer. Ovviamente le applicazioni nella robotica sono tantissime, e quello che faremo è gettare le basi per costruire un assistente robotico con cui potrete dialogare!

Iniziamo quindi a far "parlare" il computer tramite ROS. Apriamo la Web App "Speech Rec", che trovate su [http://www.hotblackrobotics.com/cloud/webgui/speech](http://www.hotblackrobotics.com/cloud/webgui/speech) oppure nella tendina "Apps". Questa Web App l'abbiamo già vista in precedenza quando usavamo il controllo vocale. Prima con questa Web App potevamo impartire ordini al robot tramite la nostra voce, ora invece usiamo il sintetizzatore vocale per ottenere una risposta o un feedback. In questa Web App abbiamo un modulo in javascript in grado di sintetizzare la voce umana. Premendo sul tasto "Bot" il computer ci accoglierà con un caloroso "Eccomi!". Da questo momento vedrete nella sezione "Console ROS" la creazione di un nuovo topic ```/<nome_del_vostro_robot>/to_speech ```


![](https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/speech%20bot/WEB%20APP.png)

Ora basterà scrivere un nodo ROS che pubblica sul nodo ```/<nome_del_vostro_robot>/to_speech ``` una stringa e il vostro computer parlerà! Lo schema concettuale di funzionamento è come in figura.

![](https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/speech%20bot/TextToSpeech.jpg)
Schema di funzionamento - da ROS alla Web App in Javascript

Il nodo ROS è un semplice publisher di stringhe in tempi diversi. Una volta pubblicate tutte le stringhe terminiamo il nodo in modo da lasciare tutti i processi puliti con ``` rospy.signal_shutdown("spegniti") ``` .

```
import dotbot_ros
import sys
import os
from std_msgs.msg import String
import rospy
from time import sleep

class Node(dotbot_ros.DotbotNode):
    node_name = 'speech_bot_pub'
    
    def setup(self):
        self.pub_position = dotbot_ros.Publisher('/listener', String)
        self.msg = String()
        self.msg.data = "ciao " 
        sleep(0.5)
        self.pub_position.publish(self.msg)
        print 'pub' 
        
        self.msg.data = "mi chiamo chat bot "
        sleep(1)
        self.pub_position.publish(self.msg)
        print 'pub' 

        self.msg.data = "sono un'applicazione di intelligenza artificiale "
        sleep(1)
        self.pub_position.publish(self.msg)
        sleep(0.5)
        print 'pub' 

        sys.stdout.flush()
        rospy.signal_shutdown("spegniti")
```


