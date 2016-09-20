# PyEvent - Python 3.5.2 Event-System

Python event system using the Nodejs 'EventEmitter' pattern

## Usage

````python
from Events import EventEmitter


class MyEventEmitter(EventEmitter):
  def __init__(self):
    # Important step to initialize EventEmitters 'member' variables and
    # automatic event-caching.
    super().__init__(True) 
  
  def EmittingMethod(self, arg):
    self.emit('emit1', arg)

instance = MyEventEmitter()

instance.EmittingMethod("FirstEmit")

# We can actually bind to an event even if it was emitted already.
# This is possible because this module supports event-caching.
# To turn automatic caching off just add: 'super().__init__(False)' in your classes '__init__' Method.
instance.on("FirstEmit", lambda x: print(x))

instance.remove_all_listeners()
instance.EmittingMethod("FirstEmit")
````
prints out:
````
FirstEmit
````
