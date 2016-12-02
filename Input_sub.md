## Implementiamo un subscriber con un interruttore ##
Ora utilizziamo un po' di più l'hardware! Configuriamo un pin di input per dare il segnale ad un led per accendersi. Il codice a questo punto è molto semplice. Importiamo un messaggio nuovo che è Input. Questo è il messaggio che pubblicherà l'interruttore quando verrà premuto. Quindi abbiam un subscriber che rimane in ascolto, e ogni volta che l'interruttore viene premuto il subscriber richiamerà la funzione `on_input`. Dentro questa funzione in fine c'è un publisher che farà accendere il led.

```
import dotbot_ros
from geometry_msgs.msg import Vector3
from dotbot_msgs.msg import Input, Led
import sys

class Node(dotbot_ros.DotbotNode):
    node_name = 'input_node'
    def setup(self):
        self.cnt = 0
        dotbot_ros.Subscriber('input', Input, self.on_input)
        self.led_pub = dotbot_ros.Publisher('led', Led)
        print 'Joy Node Started'

    def on_input(self, msg):
        if msg.input1 == False:
            self.cnt += 1
            led_msg = Led()
            led_msg.led1 = self.cnt % 2 == 1
            led_msg.led2 = (self.cnt/2) % 2 == 1
            led_msg.led3 = (self.cnt/4) % 2 == 1
            self.led_pub.publish(led_msg)
            print "pressed"
            sys.stdout.flush()
```
