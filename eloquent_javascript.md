<h1 align=center>Links</h1>

1. https://javascript.info/
2. https://eloquentjavascript.net

## Things to Remember
1. Always start by writing something that's correct and easy to understand. If it's too slow, you can measure afterward and improve it if necessary.

<h1 align=center>Values, Types, and Operators</h1>

## The "script" Tag

    <script src="/path/to/script.js"></script>                 //absolute path
    <script src="script.js"></script>                          //relative path
    
The Javascript file is run whenever it is encountered in your HTML. If the path is included in the header, add the '''defer''' value to the path. Otherwise, your Javascript will be run before the other nodes (in the HTML file) are created, causing errors.

    <script src="sscript.js" defer></script>

## Special Numbers
There are three special values: '''Infinity''', '''-Infinity''', and '''NaN''' (not a number). Examples:

    console.log(0 / 0);                 //NaN
    console.log(Infinity + 1);          //Infinity
    
## Strings
Newlines can be included without escaping a character only when the string is quoted with backticks (`)(also called template literals). Otherwise use backslashes to escape characters (\). 
    
    `half of 100 is ${100 / 2}`             //the template literal is converted to a string and added - "half of 100 is 50"

## Unary Operators
Operators can come as words such as ```console.log(typeof "x")```. These are unary because they take only one operator (as opposed to binary (e.g. 2 - 3)).

## Boolean Values
Strings can be compared using binary operators resulting in boolean values.

    console.log("Apple" < "Banana");                //true
    console.log("Itchy" != "Scratchy");             //true

Some notes about string order:
- uppercase letters are always 'less' than lowercase ones ("Z" < "a")
- nonalphabetic characters (!, -, etc) are also included in this ordering

The only value in JavaScript that is not equal to itself is NaN.

    console.log(NaN == NaN);                //false
    
## Logical Operators
Three logical operators are supported: and (&&), or (||), and not (!). The conditional operator is the only such type in JavaScript and is a ternary operator as in:

    console.log(true ? 1 : 2);              //1
    
The value on the left of the question mark picks which of the other two values will come out. If true, it chooses the middle value and if false, the last value.

## Empty Values
```null``` and ```undefined``` denote the absence of a meaningful value. These are values but carry no information.

## Automatic Type Conversion
JavaScript uses 'type coercion' to convert values when needed. In instances where you do not want any type conversion to happen, use ```===``` and ```!==```.

    "" == false;                //true
    "" === false;               //false
    
<h1 align=center>Program Structure</h1>

## Bindings
Bindings can be created using ```let```, ```const```, or ```var```. ```var``` is rarely used due to some confusing properties. ```const``` will point to the same value for as long as it exists.

## Binding Names
Binding names can include numbers, dollar signs ($), or underscores, but no other punctuation or special characters. They also cannot start with a number.

## Syntax - If, Else If, Else
A basic if, else if, else statement:

    let num = Number(prompt("Pick a number"));
    
    if(num < 10) {
      console.log("Small");
    } else if(num < 100) {
      console.log("Medium");
    } else {
      console.log("Large");
    }

## Syntax - While and Do Loops
A basic while loop:

    let number = 0;                 
    while(number < 12) {
      console.log(number);
      number = number + 2;
    }

A basic do loop:

    let yourName;
    do {
      yourName = prompt("Who are you?");
    } while(!yourName);
    
    console.log(yourName);

## Syntax - For Loop
A basic for loop:

    for(let number = 0; number < 12; number++) {
      console.log(number);
    }
    
## Breaking Out Of A Loop
The special statement ```break``` immediately jumps out of the enclosing loop. The ```continue``` keyword causes control to jump out of the body and moves on to the loops next iteration.

## Syntax = Switch
A basic switch statement:

    switch(prompt("What is the weather like?")) {
      case "rainy":
        console.log("Remember to bring an umbrella.");
        break;
      case "sunny":
        console.log("Dress lightly.");
        break;
      case "cloudy":
        console.log("Go outside.");
        break;
      default:
        console.log("Unknown weather type!");
        break;
    }
    
<h1 align=center>Functions</h1>

## Defining A Function

    const square = function(x) {
      return x * x;
    };
    console.log(square(12));                //144

## Bindings and Scopes
A binding defined outside of a function (or block), the scope is the whole program (global). If created within a function, they will be considered local.

    let x = 10;
    if(true) {
      let y = 20;
      var z = 30;
      console.log(x + y + z);                //60
    }
    console.log(y);                         //error, y is not defined
    console.log(x + z);                     //40 (visible due to 'var')
    
## Function Declaration (Notation)
A shorter way to create function bindings. These are easier to write and do not require a semicolon after the function.

    function square(x) {
      return x * x;
    }

**Function declarations do no abide by the top-to-bottom flow of control.** These are moved to the top of their scope and may provide additional flexibility.

## Arrow Functions
The primary purpose of these functions was to write functions expressions in a less verbose way.

    const power = (base, exponent) => {
      let result = 1;
      for(let count = 0; count < exponent; count++) {
        result *= base;
      }
      return result;
    };

If there is only one parameter name, the parentheses can be omited. Shortened versions:

    const square1 = x => x * x;

## Optional Arguments
Calling a function with multiple parameters is usually not an issue, for example:

    function square(x) { return x * x; }
    console.log(square(4, true, 'dog'));                //16
    
The additional arguments are simply ignored. In the case where you supply too few arguments to a function, the missing arguments get assigned the value of ```undefined```. It is possible to assign default values to functions as well.

    function power(base, exponent = 2) {
      let result = 1;
      for (let count = 0; count < exponent; count ++) {
        result *= base;
      }
      return result;
    }
    console.log(power(4));              //16
    console.log(power(2, 6));           //64

## Closure

    function multiplier(factor) {
      return number => number * factor;
    }
    
    let twice = multiplier(2);
    console.log(twice(5));              //10
    
## Recursion
Recursion is usually more inefficient than looping, however, some problems are easier to solve with recursion. These usually require exploring or processing several 'branches', each of which might branch out again into even more bran

    function power(base, exponent) {
      if(exponent == 0) {
        return 1;
      } else {
        return base * power(base, exponent - 1);
      }
    }
    
    console.log(power(2, 3));               //8
    
<h1 align=center>Data Structures: Objects and Arrays</h1>

## Data Sets
Basic creation and access of arrays:

    let listOfNumbers = [1, 2, 3];
    console.log(listOfNumbers[2];           //2
    console.log(listOfNumbers.length);      //3 (can also use listOfNumbers["length"];
    
## Methods
The '''push''' and '''pop''' methods allow us to add and subtract elements from an array.

    let sequence = [1, 2, 3];
    sequence.push(4);                   //[1, 2, 3, 4];
    sequence.pop();                     //4 (new array is [1, 2, 3])
    
## Objects
Basic object construction and access.

    let day1 = {
      squirrel: false;,                 //properties seperated by commas
      events: ["work", "eat", "sleep"]
    };
    console.log(day1.squirrel);         //false
    console.log(day1.wolf);             //undefined

The binary '''in''' operator, when applied to a string and an objects, tells whether that object has a property with that name.

    console.log("dog" in day1);         //false












