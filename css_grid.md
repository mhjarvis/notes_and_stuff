<h1 align=center>---CSS Grid---</h1>

## Links

1. https://css-tricks.com/snippets/css/complete-guide-grid/
2. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout
3. https://learncssgrid.com/
4. https://codingfantasy.com/games/css-grid-attack/play

## Enable Grid
To create a grid container you can use either ```display: grid``` or ```display: inline-grid```. All direct <em>children</em> of that element become <em>grid items</em>.


### Column/Rows Declaration
Columns can be declared using ```grid-template-columns``` and rows can be created with ```grid-template-rows```. <em>Grid tracks</em> are the space between any two lines on the grid while <em>grid lines</em> are invisible boundaries seperating table cells. Columns and grids can be defined by a space-seperated list of values using ```%```, ```px```, and ```fr```, among others. These values can be mixed if needed.

    .container {
        display: grid;
        grid-template-columns: 70%, 30%;
    }

A simpler method can be used by using the ```repeat``` function.

    .container {
        display: grid;
        grid-template-columns: repeat(4, 25%);
        grid-template-rows: repeat(4, 1fr);             //fractional units split page into 4 equal parts.
    }                                                   //fr will always allocate all the free space

The ```auto``` value automatically sets the size of the columns to the size of the container or the size of the contents of the elements in the column.

    .container {
        display: grid;
        grid-template-columns: auto auto;               //will split page into 2 parts to fit screen
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

