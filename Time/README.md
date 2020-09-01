**1. use (hour * 60 + minute) to get integer value and then do the comparison**

**2. use "{:02d}:{02d}".format(time//60, time%60) to handle "00:00" case, since we need two zeros when it's 0**
