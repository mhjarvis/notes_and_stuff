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
    
   
    
