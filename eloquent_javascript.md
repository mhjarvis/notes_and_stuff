<h1 align=center>Links</h1>

1. https://javascript.info/

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










