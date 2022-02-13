<h1 align=center>Links</h1>
https://developer.mozilla.org/en-US/docs/Web/HTML/Element

https://htmlreference.io/

<h1 align=center>Text Elements</h1>

## Block Elements
Block elements structure the main parts of the page, dividing content into comprehensive parts. These include:

    <p></p>                             //paragraphs
    <li></li>                           //lists (ordered, unordered, description - name/value pairs)
    <h1></h1>                           //headings
    <article></article>                 //articles
    <section></section>                 //sections
    <blockquote></blockquote>           //citations - these will be indented to some degree

## Inline Elements
Inline elements differentiate part of a text, giving a particular function. These include:

    <a></a>                     //links
    <em></em>                   //emphasized words
    <strong></strong>           //important words

## Noteworthy Elements

#### Span Element

    <span></span>               //wrapper used to group text mostly for styling purposes

#### Paragraph with Line Breaks
    <p>
        />                 //line breaks
        />
    <p>

#### Description List
    
    <dl>                            //description list element
        <dt>Term</dt>               //specify the term
        <dd>Definition<dd>          //definition of the term
    </dl>
    
## Attributes
Attributes are part of all HTML elements. They usually come in name/value pairs such as '''name="value"'''. 

#### Images

    <img
        src="images/dog.jpg"                //URL or file location of the image
        alt="dog jumping"                   //alternative text for when the image is unable to display
        width="200"                         //width
        height="100"                        //height
    />                                      //self-closing tag
    
#### Links
Inline elements written in the '''<a>''' tag. The destination of the link is set with the '''href''' attribute (hypertext-reference). Destinations include anchor targets (for navigating within the page), relative URLs (navigate within the same website), and absolute URLs (navigatae to another website).

    <a href="google.com"                //basic setup
       rel="noopener"                   //specify relationship between current/linked document
       target="_blank"                  //specify where to open the link (in this case, new window)
       >Google</a>

    
    
    
    
    
    
    
    












    
    
    
    
