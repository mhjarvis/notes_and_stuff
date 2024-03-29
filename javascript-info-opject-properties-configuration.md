<h1 align=center>PROPERTY FLAGS AND DESCRIPTORS</h1>

Objects can do much more than store properties via the ```key: value``` pair. 

# Property Flags
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

## ```writable``` flag
Changing the non-writable property to false prevents changing values, unless they apply their own ```defineProperty``` to overide it.

    let user = { name: "Markus" };
    Object.defineProperty(user, "name", { writable: false });

Will print the following:

    {value: 'Markus', writable: false, enumerable: true, configurable: true}

    user.name = "Scott";         // will not change user.name (will show error only in 'strict' mode)

## ```enumerable``` flag
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

## ```configurable``` flag
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

## ```Object.defineProperties(obj, descriptors)```
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

## ```Object.getOwnPropertyDescriptors```
The ```Object.getOwnPropertyDescriptors``` allows us to get all property descriptors at once.

console.log(Object.getOwnPropertyDescriptors(user))

Prints: 

    {name: {…}, surname: {…}}
        name: {value: 'Scott', writable: false, enumerable: true, configurable: true}
        surname: {value: 'Smith', writable: false, enumerable: false, configurable: false}
        [[Prototype]]: Object

<h1 align=center>PROPERTY GETTERS AND SETTERS</h1>

Objects have two kinds of properties: data properties and accessor properties. These accessor properties are functions that execute upon getting/setting a value.

## Getters and Setters
Getter and setter properties are represented by methods: ```get``` and ```set```.

    let obj = {
        get propName() {
            // getter - code executed on getting obj.propName (read)
        }
        s
        set propName() {
            // setter - code executed on setting obj.propName = value (asigned)
        }
    }

We can use a getter and setter as follows:

    let person = {
        name: "Markus",
        lastName: "Smith",

        get fullName() {
            return `${this.name} ${this.lastName}`;
        }
        set fullName() {
            [this.name, this.lastName] = value.split(" ");
        }
    }

    console.log(person.fullName);               // Markus Smith
    user.fullName = "Alice Cooper"              // uses setter to set the fullName variable


The ```get``` property 'reads' the name from the Object, hence, we are unable to assign a value to the ```fullName``` property without the setter value present. 

## Accessor descriptors
Accessor descriptors have no ```value``` or ```writable``` descriptors, but have the following:
- ```get``` - a function with no args, works when property is read.
- ```set``` - a function with one arg, called when the property is set.
- ```enumerable``` - same as for data properties.
- ```configurable``` - same as for data properties.


    let user = {
        name: "John",
        surname: "Smith"
    };

    Object.defineProperty(user, 'fullName', {
        get() {
            return `${this.name} ${this.surname}`;
        },

        set(value) {
            [this.name, this.surname] = value.split(" ");
        }
    });

    console.log(user.fullName);                 // John Smith

    for(let key in user) console.log(key);      // name, surname

## Smart getters/setters
Getters/setters can also be used as wrappers of values, for example:

    let user = {
        get name() {
            return this._name;
        },

        set name(value) {
            if (value.length < 4) {
                alert("Name is too short, need at least 4 characters");
                return;
            }
            this._name = value;
        }
    };

    user.name = "Pete";
    alert(user.name); // Pete

    user.name = ""; // Name is too short...

## Using getters/setters
One way of using getters/setters is when when end up changing or adding to objects. For example, taking the ```age``` variable and keeping it usable (since we have old code using it) after we add the new ```birthday``` variable:

    function User(name, birthday) {
        this.name = name;
        this.birthday = birthday;

        // age is calculated from the current date and birthday
        Object.defineProperty(this, "age", {
            get() {
                let todayYear = new Date().getFullYear();
                return todayYear - this.birthday.getFullYear();
            }
        });
    }

    let john = new User("John", new Date(1992, 6, 1));

    alert( john.birthday ); // birthday is available
    alert( john.age );      // ...as well as the age

## Why use getters/setters?
1. https://stackoverflow.com/questions/42342623/why-use-getters-and-setters-in-javascript