# Pywhatkit: WhatApp automation and much more!!
The pywhatkit module is generally used for various automations onw of which I use the most is whatsapp automation. Though it is not an officially recognised method and there is no guarantee for a user's privacy, I personally have found no harm in using it.

![pywhatkit](/assets/pywhat.png)
## How is it useful??
Well, sometimes I have to message multiple people whose contacts I donot have saved in my phone. In that case, instead of saving the contacts and then sending them the messages, I can directly use pywhatkit to send them these messages.

## Let's begin...
Open the terminal or type the code below in a Jupyter Notebook cell to install the module.

``` python
#for terminal
pip install pywhatkit pynput
# for notebook cell
!pip install pywhatkit pynput
```
After the module is installed, we are ready to use it 

Let's handle the imports
``` python
import pywhatkit as pk
from datetime import datetime
from pynput.keyboard import Key, Controller
from time import sleep
```
Now initialize the required methods

```python
keyboard = Controller()
timeobj=datetime.now()
mint=int(timeobj.minute)
hr=int(timeobj.hour)
```

## 'sendwhatmsg' method
``` python
pywhatkit.sendwhatmsg(number_to_text, message, hour, min, time_to_wait)

```
This method has various arguements out of which I use only the ones mentioned above.
The hour, min arguements are used to specify the time at which the message needs to be sent. The time_to_wait arguement is used to wait for the whatsapp web page to load and then send the message. The close_tab arguement by default is false for this method, however there's another method where it can be set to true. That means if you are calling the sendwhatmsg method more than once, it will open up a new tab in the browser each time. We can handle this by closing the tab using pynput library.
for egs:

```python

num1='+91XXXXXXXXXX'
message="Hey How are you"
message2="Myself Naman this side"
pk.sendwhatmsg(num, message,hr,mint,15)
# Now close the tab
keyboard.press(Key.ctrl)
keyboard.press('w')

```

The method shows output like 
```python
In 'X' Seconds WhatsApp will open and after "time_to_wait" Seconds Message will be Delivered!

```

The method waits for a random time before opening the browser.
This wait can be cut short/ignored by using the sendwhatmsg_instantly mthod. It has an arguement to close the tab automatically.

For egs:
```python
pk.sendwhatmsg_instantly(num, message,15,tab_close=True)
pk.sendwhatmsg_instantly(num, message2,15,tab_close=True)

```

### Messaging multiple people
This can be easily done by saving the numbers of the peoplein an array and using for loop to traverse it and send messages.

```python

nums=['+91XXXXXXX','+91XXXXXXX','+91XXXXXXX','+91XXXXXXX','+91XXXXXXX',]
mint+=1
for num in nums:
    
    pywhatkit.sendwhatmsg(num, message,hr,mint,15)
    mint+=1
    pywhatkit.sendwhatmsg(num, message2,hr,mint,15)
    keyboard.press(Key.ctrl)
    keyboard.press('w')
    mint+=1
    ## For sending instant message
    # pywhatkit.sendwhatmsg_instantly(num, message,15,tab_close=True)
    # pywhatkit.sendwhatmsg_instantly(num, message2,15,tab_close=True)
    # keyboard.press(Key.ctrl)
    # keyboard.press('w')
    


    sleep(3)
    
```
## Complete Code
```python

import pywhatkit as pk
from datetime import datetime
from pynput.keyboard import Key, Controller
from time import sleep
keyboard = Controller()
timeobj=datetime.now()
mint=int(timeobj.minute)
hr=int(timeobj.hour)
nums=['+91XXXXXXX','+91XXXXXXX','+91XXXXXXX','+91XXXXXXX','+91XXXXXXX',]
mint+=1
for num in nums:
    
    pywhatkit.sendwhatmsg(num, message,hr,mint,15)
    mint+=1
    pywhatkit.sendwhatmsg(num, message2,hr,mint,15)
    keyboard.press(Key.ctrl)
    keyboard.press('w')
    mint+=1
    ## For sending instant message
    # pywhatkit.sendwhatmsg_instantly(num, message,15,tab_close=True)
    # pywhatkit.sendwhatmsg_instantly(num, message2,15,tab_close=True)
    # keyboard.press(Key.ctrl)
    # keyboard.press('w')
    


    sleep(3)
    
```
