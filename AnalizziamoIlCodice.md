## Analizziamo il codice del primo esempio ##
Analizziamo il codice di **led_cnt**. Le parti evidenziate sono da trascurare perchè non sono importanti!

![] (https://raw.githubusercontent.com/sgabello1/Dotbot-Kit-e-Tutorial/master/codice_led.png) 

Iniziamo ad analizzare alcune righe di codice.
Questa prima riga significa che alcune librerie di Python devono essere aggiunte, ovvero **rospy**. Poi invece molto importante è la seconda riga che indica che il messaggio di tipo **Led** deve esssere importato nel codice.
```
import rospy
from dotbot_msgs.msg import Led
```
