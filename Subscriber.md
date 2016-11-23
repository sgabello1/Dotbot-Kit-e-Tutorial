## Le classi e le "magie" di Python ##
Ora riscriviamo il publisher ma con delle finezze in più che ci aiuteranno nella comprensione dell'esempio successivo.
Il codice diventerà così:

```

#!/usr/bin/env python

import rospy
from dotbot_msgs.msg import Led

def pari(num):
    return num % 2 == 0

class Node():
    def __init__(self):
        self.led_pub = rospy.Publisher('led', Led, queue_size=10)
        
        rospy.init_node('led_cnt_classe')
        
        rate = rospy.Rate(1)
        
        self.cnt = 0
        
        while not rospy.is_shutdown():
            self.cnt += 1
            msg = Led()
            msg.led1 = pari(self.cnt)
            self.led_pub.publish(msg)
            rate.sleep()
        msg = Led()
        self.led_pub.publish(msg)

if __name__ == '__main__':
    try:
        ne = Node()
    except rospy.ROSInterruptException:
        pass

```

Cosa cambia? Beh un bel po' di cose! Innanzitutto compare il nome "class" ovvero classe. Nessun problema una classe è simile ad una funzione, o meglio è un struttura dati che può avere funzioni e dati. In questo caso infatti abbiamo una funzione dentro la classe di inizializzazione '__init(self)__' che richiama un'altra funzione all'esterno della classe che abbiamo definito noi come "pari(num)". I caratteri *underscore* ovvero '_' 

## Implementiamo un Subscriber ##
Una volta capito come è implementato un Publisher possiamo scrivere un semplice codice per implementare invece un subscriber!
Questo esempio è molto più fine: implementeremo un publisher che pubblica appunto il valore di un Led, poi un subscriber che legge il messaggio sul topic /led e lo ripubblica su un altro topic /repub_led invertendo i led il primo con il terzo. 

Il codice è

```

#!/usr/bin/env python

import rospy
from dotbot_msgs.msg import Led

class Node():
    def __init__(self):
        self.led_pub = rospy.Publisher('led', Led, queue_size=10)
        self.led_re_pub = rospy.Publisher('repub_led', Led, queue_size=10)
        self.input_sub = rospy.Subscriber('led', Led, self.on_input)
        
        rospy.init_node('sub_input_repub')
        
        rate = rospy.Rate(20)
        cnt = 0
        while not rospy.is_shutdown():
            led_msg1 = Led()
            led_msg1.led1 = (cnt % 2) == 0
            cnt += 1
            self.led_pub.publish(led_msg1)
            rate.sleep()
        rospy.spin()
        
    def on_input(self, input_msg):
        led_msg2 = Led()
        led_msg2.led3 =  input_msg.led1
        
        self.led_re_pub.publish(led_msg2)

if __name__ == '__main__':
    try:
        ne = Node()
    except rospy.ROSInterruptException:
        pass

```

Notiamo subito l'utilizzo della classe Node(). Poi dichiariamo i 2 publisher e il subscriber. Il subsciber è analogo al publisher per quanto riguarda i primi due campi **led**, ovvero il nome del topic su cui dovrà leggere, e **Led**, il tipo di messaggio che dovrà leggere. Il terzo campo invece è una funzione dichiarata in seguito che ha la caratteristica di essere chiamata **solo** tutte le volte che qualcuno pubblica un messaggio nel topic. Non funziona in modo procedurale ma ogni volta che arriva un messaggio nel topic /led viene richiamata la funzione "on_input", la quale a sua volta ripubblicherà un altro messaggio Led.

```
        self.led_pub = rospy.Publisher('led', Led, queue_size=10)
        self.led_re_pub = rospy.Publisher('repub_led', Led, queue_size=10)
        self.input_sub = rospy.Subscriber('led', Led, self.on_input)

```

