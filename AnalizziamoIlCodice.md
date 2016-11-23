## Analizziamo il codice del primo esempio ##
Analizziamo il codice di **led_cnt**. Le parti evidenziate sono da trascurare perchè non sono importanti!

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/codice_led.png) 

Se volete copiarlo qui:
```
#!/usr/bin/env python

import rospy
from dotbot_msgs.msg import Led

def talker():
        pub = rospy.Publisher('led', Led, queue_size=10)
        rospy.init_node('blinker_node')
        rate = rospy.Rate(20)
        cnt = 0
        while not rospy.is_shutdown():
            led_msg = Led()
            led_msg.led1 = (cnt % 2) == 0
            cnt += 1
            pub.publish(led_msg)
            rate.sleep()
        
if __name__ == '__main__':
    try:
        talker()
    except rospy.ROSInterruptException:
        pass
```
Iniziamo ad analizzare alcune righe di codice.
Questa prima riga significa che alcune librerie di Python devono essere aggiunte, ovvero il messaggio di tipo **Led** deve esssere importato nel codice.
```
from dotbot_msgs.msg import Led
```
Poi dichiariamo una funzione **talker**, dove all'interno c'è un **Publisher**. Il publisher è dichiarato con una variabile in questo caso di nome **pub** = rospy.Publisher('led', Led, queue_size=10) con tre campi: **led** che è il nome del topic ROS in cui manderà il messaggio, **Led** è il tipo di messaggio che abbiamo importato in precedenza, **queue_size** è la lunghezza del buffer nel topic - in altre parole meno tecniche è il numero di messaggi che possono "accodarsi" nel topic prima che vengano buttati, in questo caso se pubblichiamo velocemente 10 messaggi e nessuno li legge i messaggi dall undicesimo in poi verranno buttati.

```
def talker():
        pub = rospy.Publisher('led', Led, queue_size=10)

```
Qui viene inizializzato il nome del nodo che sarà eseguito. Questo lo vedrete in esecuzione nella finestra ROS in "Node List" come appunto "/hotbot/bliker_node".
```
        rospy.init_node('blinker_node')
```
Poi c'è un delay per far si che il led si accenda e si spenga alla frequenza scelta da noi. Rate(20) è un ritardo corrispondente alla frequenza di 20Hz, quindi 1/20 = 0,05 secondi. 
```
        rate = rospy.Rate(20)
```
Qui c'è un ciclo while infinito. All'interno del while il campo **led1** del messaggio **Led**  viene continuamente riempito di valori alternanti tra 0 e 1. Questi valori cambiano continuamente tramite la srtinga  = (cnt % 2). La variabile cnt con cnt += 1  è incrementata ogni ciclo ed è calcolato il resto della divisione per 2 con l'operatore %2. Il messaggio è inizializzato con == 0. Il messaggio è pubblicato con la funzione pub.publish(led_msg) e infine viene ritardato del tempo scelto in precedenza.
```
while not rospy.is_shutdown():
            led_msg = Led()
            led_msg.led1 = (cnt % 2) == 0
            cnt += 1
            pub.publish(led_msg)
            rate.sleep()
```            
