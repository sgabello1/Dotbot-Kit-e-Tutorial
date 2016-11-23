## Implementiamo un subscriber con un interruttore ##
Ora utilizziamo un po' di più l'hardware! Configuriamo un pin di input per dare il segnale ad un led per accendersi. Il codice a questo punto è molto semplice. Importiamo un messaggio nuovo che è Input. Questo è il messaggio che pubblicherà l'interruttore quando verrà premuto. Quindi abbiam un subscriber che rimane in ascolto, e ogni volta che l'interruttore viene premuto il subscriber richiamerà la funzione `on_input`. Dentro questa funzione in fine c'è un publisher che farà accendere il led.

```
#!/usr/bin/env python

import rospy
from dotbot_msgs.msg import Led, Input

class Node():
    def __init__(self):
        self.led_pub = rospy.Publisher('/led', Led, queue_size=10)
        self.input_sub = rospy.Subscriber('input', Input, self.on_input)
        
        rospy.init_node('sub_input')
        
        rospy.spin()
        
    def on_input(self, input_msg):
        led_msg = Led()
        led_msg.led1 = not input_msg.input1
        
        self.led_pub.publish(led_msg)

if __name__ == '__main__':
    try:
        ne = Node()
    except rospy.ROSInterruptException:
        pass
```
