## Implementiamo un subscriber con un interruttore ##

```
#!/usr/bin/env python

import rospy
from dotbot_msgs.msg import Led, Input

class Node():
    def __init__(self):
        self.led_pub = rospy.Publisher('/white/led', Led, queue_size=10)
        self.input_sub = rospy.Subscriber('input', Input, self.on_input)
        
        rospy.init_node('sub_input')
        
        rospy.spin()
        
    def on_input(self, input_msg):
        led_msg = Led()
        led_msg.led1 = not input_msg.input1
        led_msg.led2 = not input_msg.input1
        led_msg.led3 = not input_msg.input2
        self.led_pub.publish(led_msg)

if __name__ == '__main__':
    try:
        ne = Node()
    except rospy.ROSInterruptException:
        pass
```
