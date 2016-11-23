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
