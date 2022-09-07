<h1 align=center>PROPERTY FLAGS AND DESCRIPTORS</h1>

Objects can do much more than store properties in the simple 'key: value' pair. 

## Property Flags
Object properties, besidees a value, have three special attributes ("flags"):
- writable - if ```true```, the value can be changed.
- enumerable - if ```true```, it will be listed in loops.
- configurable - if ```true```, the property can be deletd and these attributes can be modified.

During object creation, all of these values are ```true```. 