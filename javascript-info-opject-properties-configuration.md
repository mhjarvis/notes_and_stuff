<h1 align=center>PROPERTY FLAGS AND DESCRIPTORS</h1>

Objects can do much more than store properties via the ```key: value``` pair. 

## Property Flags
Object properties, besides a value, have three special attributes ("flags"):
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

Flags can be changed with ```Object.defineProperty(obj, propertyName, descriptor)``` where the descriptor is the property descriptor object to apply, as in:

    Object.defineProperty(user, 'name', { value: 'Scott' });        // changes 'name' variable

### Non-writable
Changing the non-writable property to false prevents changing values, unless they apply their own ```defineProperty``` to overide it.

    let user = { name: "Markus" };
    Object.defineProperty(user, "name", { writable: false });

Will print the following:

    {value: 'Markus', writable: false, enumerable: true, configurable: true}

    user.name = "Scott";         // will not change user.name (will show error only in 'strict' mode)

### Non-enumerable
Normally, a built-in ```toString``` for objectsis non-enumerable. It will not show up in a ```for...in``` loop, unless we add one of our own.

    let user = { 
        name: 'Markus',
        toString() {
            return this.name;
        }
    };

    for(let key in user) console.log(key);          // name
                                                    // toString

We can set ```enumerable:false``` to prevent this functionality:

    Object.defineProperty(user, 'toString', { enumerable: false });
    
    for(let key in user) console.log(key);         // name

Non-enumerable properties are also excluded from ```Object.keys```.

### **Non-configurable**
A non-configurable property cannot be deleted, nor its attributes modified. Some pre-defined objects already meet this. 

    console.log(Object.getOwnPropertyDescriptor(Math, 'PI'))

Prints out:

    {value: 3.141592653589793, writable: false, enumerable: false, configurable: false}

You are also unable to change this value to make it writable again.

    Object.defineProperty(Math, 'PI', { writable: true })       // Error, no change

Thus, when making a property non-configurable, there is no changing it back. It prevents changes of property flags and its deletion, while allowing one to change its value. Thus, we can make a property 'forever sealed' by doing the following:

    let user = { 
        name: 'Markus',
    };

    Object.defineProperty(user, 'name', {
        writable: false,
        configurable: false
    })

    user.name = 'Scott';                                        // does not work
    delete user.name;                                           // does not work
    Object.defineProperty(user, 'name', { value: 'Scott' })     // does not work

### ```Object.defineProperties(obj, descriptors)```
Using ```Object.defineProperties(obj, descriptors)``` allows us to define many properties at once.

    let user = { 
        name: 'Markus',
    };

    Object.defineProperties(user, {
        name: { value: 'Scott', writable: false },
        surname: { value: 'Smith', writable: false }
    })

    console.log(Object.getOwnPropertyDescriptor(user, 'name'))

Prints: 

    {value: 'Scott', writable: false, enumerable: true, configurable: true} 

### ```Object.getOwnPropertyDescriptors```
The ```Object.getOwnPropertyDescriptors``` allows us to get all property descriptors at once.

console.log(Object.getOwnPropertyDescriptors(user))

Prints: 

    {name: {…}, surname: {…}}
        name: {value: 'Scott', writable: false, enumerable: true, configurable: true}
        surname: {value: 'Smith', writable: false, enumerable: false, configurable: false}
        [[Prototype]]: Object

<h1 align=center>PROPERTY GETTERS AND SETTERS</h1>
