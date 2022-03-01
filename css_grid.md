<h1 align=center>---CSS Grid---</h1>

## Links

1. https://css-tricks.com/snippets/css/complete-guide-grid/
2. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout
3. https://learncssgrid.com/
4. https://codingfantasy.com/games/css-grid-attack/play
5. https://cssgridgarden.com/
6. https://rachelandrew.co.uk/archives/2015/02/04/css-grid-layout-creating-complex-grids/
7. https://gridbyexample.com/examples/ 

## Enable Grid
To create a grid container you can use either ```display: grid``` or ```display: inline-grid```. All direct <em>children</em> of that element become <em>grid items</em>.


### Column/Rows Declaration
Columns can be declared using ```grid-template-columns``` and rows can be created with ```grid-template-rows```. <em>Grid tracks</em> are the space between any two lines on the grid while <em>grid lines</em> are invisible boundaries seperating table cells. Columns and grids can be defined by a space-seperated list of values using ```%```, ```px```, and ```fr```, among others. These values can be mixed if needed.

    .container {
        display: grid;
        grid-template-columns: 70%, 30%;
    }

#### Repeat Function
A simpler method can be used by using the ```repeat``` function.

    .container {
        display: grid;
        grid-template-columns: repeat(4, 25%);
        grid-template-rows: repeat(4, 1fr);             //fractional units split page into 4 equal parts.
    }                                                   //fr will always allocate all the free space

#### Auto
The ```auto``` value automatically sets the size of the columns to the size of the container or the size of the contents of the elements in the column.

    .container {
        display: grid;
        grid-template-columns: auto auto;               //will split page into 2 parts to fit screen
    }

#### Min-Content / Max-Content
Special keywords such as ```min-content``` can be used to indicate the intrinsic minimum width of the content. If there is a sentence, wrap everything and width will be based on the longest word. ```max-content``` provides the opposite, representing the intrinsic maximum width of the content. Text will not wrap even if it causes overflow.

#### MinMax Function
The ```minmax(min, max)``` function sets the minimum and maximum value for what the length is able to do. This is useful in combination with relative units, allowing a column to only shrink to a certain point.

    #field {
        display: grid;
        grid-template-columns: minmax(max-content, 200px) minmax(min-content, auto);
        grid-template-rows: 1fr 1fr;
    }

#### Auto-Fit / Auto-Fill
Both the ```auto-fit``` and ```auto-fill``` keywords tell the browser to handle the column sizing and element wrapping for us. Auto-fill columns are defined using the ```repeat()``` function. 

    .container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    }

```auto-fill``` <strong><em>FILLS</em></strong> the row with as many columns as it can fit. ```auto-fit``` <strong><em>FITS</em></strong> the <strong><em>CURRENTLY AVAILABLE</em></strong> columns into the space by expanding them so that they take up any available space. 

#### Grid-Template Shorthand
Syntax for ```grid-template``` is ```grid-template: <rows> / <columns>``` when just using columns/rows. To add areas use ```grid-template: <areas> <rows> / <columns>```.

    .container {
        display: grid;
        grid-template: 100px 150px / repeat(3, 1fr);                //row1 row2 / columns 1-3
    }

    .container {
        display: grid;
        grid-template: "a a b" 50px                                 //area row
                       "a a b" 100px / 1fr 2fr 1fr;                 //area row / columns
    }

    #item1 {
        grid-area: a;
    }

### Grid Gaps
The ```column-gap``` property sets the size of the gap between grid columns while the ```row-gap``` property sesets the size of the gap between grid rows.

    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(3, 100px);
        column-gap: 10px;
        row-gap: 5%;
    }

The ```gap: <row-gap> / <column-gap>``` property is a shorthand version of ```coulumn-gap``` and ```row-gap```. 

    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(3, 1fr);
        gap: 30px 10px;                                 //<row-gap> <column-gap>
    }

### Grid Start/End
The ```grid-column-start``` property specifies a grid item's start position within the grid column. The ```grid-column-end``` property specifies a grid item's end position within the grid column. The same principle applies tow rows with ```grid-row-start``` and ```grid-row-end```.

    .container {
        display: grid;
        grid-template-columns: repeat(6
        , 1fr);
        grid-template-rows: repeat(6, 2fr);
        gap: 10px;
    }

    #item {
        grid-column-start: 3;
        grid-column-end: 5;
    }

    #item2 {
        grid-row-start: 3;
        grid-row-start: 5
    }
    
Both properties can be combined using ```span <number>``` on the ```grid-column-start``` element. Note that, theh starting position is not defined, only how many columns the element spans is defined.

    #item {
        grid-column-start: span 2;                  //span two grid columns
    }

Shorthand versions of these properties come as ```grid-column``` and ```grid-row```. ```span``` can also be used within these properties.

    #item {
        grid-column: 1 / 4;
        grid-row: 1 / span 2;
    }

### Grid Area
The ```grid-template-areas``` property allow us to define a grid template by referencing the names of the grid areas which are specified with the ```grid-area``` property. Repeating the name of a grid area causes the content to span those cells. The following are common values used in the ```grid-template-areas``` property:

    <grid-area-name>            //name of a grid area specified with grid-area (e.g. a, b, area1, area2, etc.)
    .                           //a period signifies an empty grid cell
    none                        //no grid areas are defined
    
The ```grid-area``` property gives an item a name so that it can be referenced by a template created with the grid-template-areas property. This property can be used as shorthand for ```grid-row-start``` + ```grid-column-start``` + ```grid-row-end``` + ```grid-column-end```. Common values usin the the ```grid-area``` property: 

    <name>                              //name of your choosing

    <row-start> / <column-start>
    <row-end> / <column-end>            //can be numbers or named lines

An example is as follows: 

    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(4, 50px);
        grid-template-areas: "header header header"
            "nav content content"
            "nav content content"
            "footer footer footer";
    }

    #header {
        grid-area: header;
    }

    #nav {
        grid-area: nav;
    }

    #content {
        grid-area: content;
    }

    #footer {
        grid-area: footer;
    }

Another example:

    .container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(4, 50px);
    }

    #item {
        grid-area: 1 / 1 / 5 / 3;
    }

### Grid-Auto-Flow
The ```grid-auto-flow``` property controls how the auto-placement algorithm works, specifying exactly how auto-placed items get flowed into the grid. 

    grid-auto-flow: row;                //tells the auto-placement algo to fill in each row in turn, adding
                                        //rows as necessary (default)
    grid-auto-flow: column;             //tells the auto-placement algo to fill in each column in turn,
                                        //adding new columns as necessary
    grid-auto-flow: dense;              //tells the auto-placement algorithm to attempt to fill in holes
                                        //earlier in the grid if smaller items come up later

### Grid-Auto-Rows and Grid-Auto-Columns
The ```grid-auto-rows``` and ```grid-auto-columns``` properties give control over the size of implicit tracks (those items placed outside the explicit grid or when items overflow the defined cells). They accept the same values as when using ```grid-template``` except for the ```repeat()``` function.

    .container {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 100px 100px;
        grid-auto-columns: 200px;                       //items will have a 200px width if overflow
        grid-auto-rows: 150px;                          //items will have 150px height if overflow
    }

When an item is not explicitly sized with ```grid-template``` but contains the ```grid-auto``` template, implicit grid tracks are created to hold it.

### Justify-Items, Align-Items and Place-Items
```justify-items``` aligns items along the inline (row) axis while ```align-items``` aligns items along the bblock (column) axis. ```place-items``` gives the ability to set both in the form of ```place-items: <align-items> <justify-items>```. Values include:

    justify-items: start;               //align items to be flush with the start edge of their cell
    justify-items: end;                 //aligns items to be flush with the end edge of their cell
    justify-items: center;              //aligns items in the center of their cell
    justify-items: stretch;             //fills the whole width of the cell (default)
    align-items: start;                 //aligns items to be flush with the start edge of their cell
    align-items: end;                   //aligns items to be flush with the end edge of their cell
    align-items: center;                //aligns items in the center of their cell
    align-items: stretch;               //fills the whole height of the cell (default)

### Justify-Self and Align-Self
The ```justify-self``` and ```align-self``` properties have the same properties as justify-items and align-items but their values apply to the content inside a single grid item. The ```place-self``` property can combine both.

    : start;                //aligns items to be flush with the start edge of their cell
    : end;                  //aligns items to be flush with the end edge of their cell
    : center;               //aligns items in the center of their cell
    : stretch;              //fills the whole width of the cell (default)

### Justify-Content 
These properties allow for setting the alignment of the grid within the grid container. ```justify-content``` aligns the grid along the inline (row) axis. The ```align-content``` property aligns the grid along the block (columns) axies. The following values apply to both properties:

    : start;            //aligns the grid to be flush with the start edge of the grid container
    : end;              //aligns the grid to the flush with the end edge of the grid container
    : center;           //aligns the grid in the center of the grid container
    : stretch;          //resizes the grid items to allow the grid to fill the full width
    : space-around;     //places an even amount of space between each grid item with
                        //half-sized spaces on the far ends
    : space-between;    //places an even amount of space between each grid item, no space at far ends
    : space-evenly;     //places an even amount of space between each grid item, including far ends












<h1 align=center>---Quick Reference---</h1>

#### Parent Elements
    display:                         grid, inline-grid;

##### Columns / Rows
    grid-template-columns:           %, px, fr, em;
    grid-template-rows:              %, px, fr, em;
        : repeat(2, 50%);
        : auto;                         //auto sets size to the container or contents
        : min-content;                  //minimum width of content (biggest word)
        : max-content;                  //maximum width of conent (full sentence)
        : min-max(min, max);            //sets minimum and maximum width/height
        : repeat(auto-fill, 100px);     //fills the row with as many columns as it can
        : repeat(auto-fit, 100px);      //fits the current columns into the space by expanding
                                        //them to take up any available space

    grid-remplate:                  <rows> / <columms> or <areas> <rows> / <columns>


##### Gaps
    column-gap:                      %, px, fr, em;
    row-gap:                         %, px, fr, em;
    gap:                             <row-gap> <column-gap> (shorthand)

##### Grid-Template-Areas
    grid-template-areas:            "a b" "a b"; . (empty grid cell); none (none);

----------------------------------------------------------------------------------------------------
#### Child Elements

##### Columns / Rows
    grid-column-start:               1, 2, 3, span #;
    grid-column-end:                 1, 2, 3, span #;
    grid-row-start:                  1, 2, 3, span #;
    grid-row-end:                    1, 2, 3, span #;
    grid-column:                     <start> / <end>;
    grid-row:                        <start> / <end>;

##### Grid-Area
    grid-area:                      a; row-start/column-start/row-end/column-end (e.g. 1/3/1/5);
