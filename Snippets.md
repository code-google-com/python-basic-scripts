# **API: How can a user exit an operation during computation?** #

To test in Scripts, whether key-stroke interruption with "ESC" works or not

URL Source: http://mayamel.tiddlyspot.com/


# **Code snippet** #

```
import maya.OpenMaya as om
def someOperation(i):
    print i

def doCompute(someFunc, loopRange):
    """
    Parameters:
    someFunc : A callable function object, taking a single arg for the current
        loop number.
    loopRange : int : How many loops to perform.
    """
    computation = om.MComputation()
    computation.beginComputation()
    for i in range(loopRange):
        someFunc(i)
        if computation.isInterruptRequested():
            print "Operation cancled by user."
            break
    computation.endComputation()

doCompute(someOperation, 10000)
```


# **How can I find the referenced scenes filename by selecting a node?** #

Get reference name from selected object

URL Source: http://mayamel.tiddlyspot.com/


# **Code snippet** #

```
string $sel[] = `ls -sl`;
referenceQuery -f $sel[0];
```