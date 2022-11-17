---
layout: post
published: true
title: How to break the loop with esc in maya
---

```html
<script src="https://gist.github.com/ki68/de9a2cfb3e4415be01594fffad4c518d.js"></script>
```

```python
import time
import maya.cmds as mc

# https://forums.cgsociety.org/t/python-killing-a-script-with-esc/1564682/3
def work():
    mc.progressWindow(isInterruptable=1) # create window   
    mc.refresh() # view update
    for i in list(range(20)):
        print (i)
        time.sleep(1) # time delay
        if (mc.progressWindow(q=1,isCancelled=1)==1): # esc key
            mc.progressWindow(endProgress=1) # close window 
            return # or break
```            
