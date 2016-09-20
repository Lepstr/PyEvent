# PyEvent - Python 3.5.2 Event-System

Python event system using the Nodejs 'EventEmitter' pattern

<b>NOTE:</b> This module is probably not downward compatible with < 3.2

The Next step with this module is to actually provide a default serialization process for single events,
so you could send them to another user over the network or provide a couple of default startup events in a file.

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
instance.EmittingMethod("SecEmit")
````
prints out:
````
FirstEmit
````

## Module Feature Pipeline
- [x] Implementation of **on** and **emit**
- [x] **EventCollection** class to easily access the currently bound events
- [x] Implementation of Event-Caching
- [ ] Implementation of default Serialization via. BinaryFormatter
- [ ] Little Performance optimizations

## License

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated
documentation files (the "Software"), to deal in the Software without restriction,
including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies
or substantial portions of the Software.

<b>THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING
BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NON INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.</b>
