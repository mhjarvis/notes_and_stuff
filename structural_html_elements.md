<h1 align=center>Sectioning Content</h1>

## ```<section></section>```
- organize content into logical sections
- can be nested like ```div```'s
- sections should be topical; organize content based on the material being presented
- sections should flow linearly

## ```<article></article>```
- used to group content that can stand on its own, such as blog posts
- used anywhere you would use a section element, if the content is independent and reusable
- an article element can include other article elements, as would be the case with a blog post including comments.

## ```<aside></aside>```
- used to group content that does not belong in the normal flow of your document
- examples: reference information, author information, advertising space, calendar of events, 'a side bar'

## ```<nav></nav>```
- used to group a set of links (e.g. menu)
- if the content is primarily links, put it in a nav element

## ```<address></address>```
- not included in ```section``` elements, but is used to provide contact information for either the document or a specific article
- intended for providing contact information (e.g. email, url, phone number, address, etc.)

###  ```<header></header> && <footer></footer>```
- header and footer should be included in their respective positions

<h1 align=center>Planning a Page Layout</h1>

An example of using symantic elements:

    <body>
        <header>
            <title>
                title
            </title>
            <nav>
                nav element
                nav element
                nav element
            </nav>
        </header>
        <section>
            <section>
                <section>
                    section content
                </section>
                <section>
                    <article>
                        article content
                    </article>
                    <article>
                        article content
                    </article>
                    <article>
                        article content
                    </article>
                </section>
            </section>
            <aside>
                <section>
                    section content
                </section>
                <section>
                    <article>
                        article contentf
                    </article>
                    <article>
                        article content
                    </article>
                </section>
            </aside>
        </section>
        <footer>
            <address>
                address content
            </address>
        </footer>
    </body>    

<h1 align=center>Sectioning Roots</h1>

Sectioning roots are HTML elements which have their own outline that does not contribute to the outline of the rest of the document (for example, the ```body``` element). 

## ```<blockquote></blockquote>```
- used when you need to include a long quotation in a document
- includes quotation, header text, paragraphs, and embedded content
- includes ```cite``` element, which is not displayed (normally)

    <blockquote cite="www.apress.com">
        <h1>Quotation...</h1>
        <p>This is a quotation</p>
    </blockquote>

## ```<details></details>```
- allows you to create collapsible sections of content
- can include ```summary``` element which contains content that is displayed when collapsed
- without a ```summary``` will display 'Details'
- collapsed is the default view, use ```open``` to display content when page is loaded

    <details open>
        <summary>This is the collapsed text</summary>
        <h1>Details</h1>
        <p>These are collapsable details</p>
    </details>

## ```<figure></figure>```
- used to group content that is self-contained and can be logically moved to a different location
- allows the use of a caption within the content
- can be used to group text (code listing) along with a caption
- include ```figcaption``` element to add caption

    <figure>
        <h1>Figure</h1>
        <img src="HTML5Badge.png" alt="HTML5" />
        <figcaption>Official HTML5 Logo</figcaption>
    </figure>

<h1 align=center>Grouping Elements</h1>

Grouping elements are used primarily for semantic purposes and do not affect the outline.

## ```<p></p>```
- defines a paragraph
- overused, should be reserved for a portion of a document that contains a single thought or idea

## ```<hr />```
- renders a horizontal line or, a thematic break
- usually placed between paragraphs when there is a change of topic

## ```<pre></pre>```
- content placed inside ```pre``` elements will be rendered just like it is entered, including white space
- use it to include content that is already formatted (e.g. code elements, poetry)

## ```<main></main>```
- used to indicate that its contents present the primary purpose or topic of the document
- cannot be inside an article, aaside, footer, header, or nav elements (due to it representing the main theme or the core of the document)
- limited to one ```main``` element per document
- content should be unique and not shared by other documents
- should not have an article, aside, or nav element inside, usually

## ```<div></div>```
- used for all other grouping reasons
- used to apply styles to all fo its child elements

<h1 align=center>Listing Elements</h1>

Listing elements comprise those used for listing contents, such as bulleted lists. These are not necessarily just single items. Any time you have a list of things, even if the "things" are large blocks of content, you should consider creating them inside one of these list elements.

## ```<li></li> && <ol></ol>```
- the type of list used should be picked based on semantics
- ordered list includes the ```start``` attribute which lets you pick the number to start with
- the ```reversed keyward reverses the order of numbers

The ```type``` attribute specifies what type of numbering to use:
    1           // use numbers (default)
    A           // use uppercase letters (e.g. A, B, C, D)
    a           // use lowercase letters
    I           // use Roman numerals with uppercase letters (e.g. I, II, III, IV)
    i           // use lowercase roman numerals

- letters and roman numerals do not support negative numbers and will convert to negative integers

## ```<dl></dl>``` (discription list)
- used to define a list of terms (one-to-one mapping)
- implemented using name/value pairs - ```dt></dt>``` for term elements and ```<dd></dd>``` for description elements
- can also be use dto list groups of things with a group header

    <dl>
        <dt>Term1</dt>
        <dd>Definition</dd>
        <dt>Term2</dt>
        <dd>Definition</dd>
    </dl>

<h1 align=center>Inline Frames</h1>

- the ```iframe``` lement is used to embed another web page within the current document

    <iframe src="http://www.apress.com" width="100%" height="400">
        <p>Your browser does not support iframes</p>    
    </iframe>
