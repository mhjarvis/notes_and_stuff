<h1 align=center>---CSS Media Queries---</h1>

## Links

1. https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Media_queries
2. https://css-tricks.com/a-complete-guide-to-css-media-queries/

## Media Queries
 CSS Media Query allows for creating different layouts based on the size of the viewport. The basic media query syntax is as follows:

    @media(feature: value) {
        /* CSS rules */
    }

Media features are aspects of the device that the media (website) is being viewed on. 

## Width Feature
The width feature allows for the setting of the viewport width based on an evaluation. The following CSS will take place if the viewport breaks 900px.

    @media(min-width: 900px) {
        body {
            background: red;
            font-size: 25px;
        }
    }

    /* Medium Screens */
    @media (min-width: 600px) and (max-width:900px) {
    .container {
        }
    }

    /* Large Screens */
    @media (min-width:901px) {
    .container {
        }
    }

Complex media queries can be built using the ```and``` keyword to bound CSS rules between a range using ```min-width``` and ```max-width```.