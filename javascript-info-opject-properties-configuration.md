# ====== PROPERTY FLAGS AND DESCRIPTORS ======

Objects can do much more than store properties in the simple 'key: value' pair. 

## Property Flags
Object properties, besidees a value, have three special attributes ("flags"):
- writable - if ```true```, the value can be changed.
- enumerable - if ```true```, it will be listed in loops.
- configurable - if ```true```, the property can be deletd and these attributes can be modified.

During object creation, all of these values are ```true```. The syntax is ```Object.getOwnPropertyDescriptor(obj, prop);``` where ```obj``` is the object in which to look for the property and ```prop``` is the name or symbol of the property whose description is to be retrieved.

    let user = { name: "Markus" };
    let desc = Object.getOwnPropertyescriptor(user, 'name');

    console.log(desc);     
    
The above will print the following:
    
        {value: 'Markus', writable: true, enumerable: true, configurable: true}
            configurable: true
            enumerable: true
            value: "Markus"
            writable: true
            [[Prototype]]: Object

Flags can be changed with ```Object.defineProperty(obj, propertyName, descriptor)``` where the descriptor is the property descriptor object to apply. 

### Non-writable
Changing the non-writable property to false prevents changing values, unless they apply their own ```defineProperty``` to overide it.

    let user = { name: "John" };
    Object.defineProperty(user, "name", { writable: false });

    user.name = "Pete";                 // Error: Cannot assign to read only property 'name'

### Non-enumerable


<h1 align=center>PROPERTY GETTERS AND SETTERS</h1>
