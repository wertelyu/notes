# html 5

<h1 style="font-size: 60px;">Heading 1</h1>

## <p></p>

The `<p></p>` - A paragraph always starts on a new line, and browsers automatically add some `white space (a margin)` before and after a paragraph.

`white space == margin`

## <hr />

The `<hr />` - element is used to separate content (`------`)
The `<hr>` tag is an empty tag, which means that it `has no end tag`. 

## <br />

The HTML `<br />` element defines a line break.
The `<br>` tag is an empty tag, which means that it `has no end tag`.

## <pre></pre>

The HTML `<pre>` element defines preformatted text.

```html
    <pre style="font-size: 20px; color: seagreen;">
      My Bonnie lies over the ocean.

      My Bonnie lies over the sea.

      My Bonnie liesover the ocean. 

      Oh, bring back my Bonnie to me.
    </pre>
```
## style

The HTML `style` attribute has the following syntax:

`<tagname style="property:value;">`

## background-color

The CSS `background-color` property defines the background color for an HTML element.

`<body style="background-color:powderblue;">`

## color

The CSS `color` property defines the text color for an HTML element:

`<h1 style="color:blue;">This is a heading</h1>`
`<p style="color:red;">This is a paragraph.</p>`

## font-family

The CSS `font-family` property defines the font to be used for an HTML element:

`<h1 style="font-family:verdana;">This is a heading</h1>`
`<p style="font-family:courier;">This is a paragraph.</p>`

## font-size

The CSS `font-size` property defines the text size for an HTML element: 

`<h1 style="font-size:300%;">This is a heading</h1>`
`<p style="font-size:160%;">This is a paragraph.</p>`

## text Alignment

The CSS `text-align` property defines the horizontal text alignment for an HTML element:

`<h1 style="text-align:center;">Centered Heading</h1>`
`<p style="text-align:center;">Centered paragraph.</p>`

## HTML Formatting Elements


    <b> - Bold text
    <strong> - Important text
    <i> - Italic text
    <em> - Emphasized text
    <mark> - Marked text
    <small> - Smaller text
    <del> - Deleted text
    <ins> - Inserted text
    <sub> - Subscript text
    <sup> - Superscript text

## blockquote

The HTML `<blockquote>` element defines a section that is quoted from another source.
```html
    <p>Here is a quote from WWF's website:</p>
    <blockquote cite="http://www.worldwildlife.org/who/index.html">
        For 50 years, WWF has been protecting the future of nature.
        The world's leading conservation organization,
        WWF works in 100 countries and is supported by
        1.2 million members in the United States and
        close to 5 million globally.
    </blockquote>
```

## abbr

The HTML `<abbr>` tag defines an abbreviation or an acronym, like "HTML", "CSS", "Mr.", "Dr.", "ASAP", "ATM".

`<p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>`

    <abbr>  Defines an abbreviation or acronym
    <address>   Defines contact information for the author/owner of a document
    <bdo>   Defines the text direction
    <blockquote>    Defines a section that is quoted from another source
    <cite>  Defines the title of a work
    <q>     Defines a short inline quotation 

## comment tag

`<!-- Write your comments here -->`

## Color Names

Tomato
Orange
DodgerBLue
MediumSeaGreen
Gray
SlateBlue
Violet
LightGray

[color names](https://www.w3schools.com/colors/colors_names.asp)

`<h1 style="background-color:DodgerBlue;">Hello World</h1>`
`<p style="background-color:Tomato;">Lorem ipsum...</p>`

`<h1 style="color:Tomato;">Hello World</h1>`
`<p style="color:DodgerBlue;">Lorem ipsum...</p>`
`<p style="color:MediumSeaGreen;">Ut wisi enim...</p>`

## Border Color

`<h1 style="border:2px solid Tomato;">Hello World</h1>`
`<h1 style="border:2px solid DodgerBlue;">Hello World</h1>`
`<h1 style="border:2px solid Violet;">Hello World</h1>` 

## color values

In HTML, colors can also be specified using `RGB` values, `HEX` values, `HSL` values, `RGBA` values, and `HSLA` values.

`<h1 style="background-color:rgb(255, 99, 71);">...</h1>`
`<h1 style="background-color:#ff6347;">...</h1>`
`<h1 style="background-color:hsl(9, 100%, 64%);">...</h1>`

`<h1 style="background-color:rgba(255, 99, 71, 0.5);">...</h1>`
`<h1 style="background-color:hsla(9, 100%, 64%, 0.5);">...</h1>` 

rgb(red, green, blue)
rgb(0, 0, 255)

`opacity` - непрозрачность

rgba(red, green, blue, alpha) - alph == opacity
rgba(255, 99, 71, 0.4)

## CSS

`CSS` stands for Cascading Style Sheets.

    Use the HTML style attribute for inline styling
    Use the HTML <style> element to define internal CSS
    Use the HTML <link> element to refer to an external CSS file
    Use the HTML <head> element to store <style> and <link> elements
    Use the CSS color property for text colors
    Use the CSS font-family property for text fonts
    Use the CSS font-size property for text sizes
    Use the CSS border property for borders
    Use the CSS padding property for space inside the border
    Use the CSS margin property for space outside the border

CSS can be added to HTML documents in 3 ways:

    Inline - by using the style attribute inside HTML elements
        <h1 style="color:blue;">A Blue Heading</h1>
    Internal - by using a <style> element in the <head> section
        <!DOCTYPE html>
        <html>
        <head>
        <style>
        body {background-color: powderblue;}
        h1   {color: blue;}
        p    {color: red;}
        </style>
        </head>
        <body 
          <h1>This is a heading</h1>
          <p>This is a paragraph.</p 
        </body>
        </html> 
    External - by using a <link> element to link to an external CSS file
        <!DOCTYPE html>
        <html>
        <head>
          <link rel="stylesheet" href="styles.css">
        </head>
        <body>

        <h1>This is a heading</h1>
        <p>This is a paragraph.</p>

        </body>
        </html> 
---
    <style>
      h1 {
      color: blue;
      font-family: verdana;
      font-size: 300%;
      }
      p {
      color: red;
      font-family: courier;
      font-size: 160%;
      }
    </style>

    p {
        border: 2px solid powderblue;
      }

    p {
      border: 2px solid powderblue;
      margin: 50px;
      padding: 30px;
     }

## HTML Links

`A link does not have to be text. A link can be an image or any other HTML element!`


<a href="url">link text</a>

## HTML Links - The target Attribute

The `target` attribute specifies where to open the linked document.

The `target` attribute can have one of the following values:

    _self - Default. Opens the document in the same window/tab as it was clicked
    _blank - Opens the document in a new window or tab
    _parent - Opens the document in the parent frame
    _top - Opens the document in the full body of the window

HTML Links - Use an Image as a Link

To use an `image` as a link, just put the `<img>` tag inside the `<a>` tag:

     <a href="https://google.com">
       <img src="smiley.gif" alt="HTML tutorial" style="width:42px;height:42px;">
     </a> 

Link to an Email Address

     <a href="mailto:someone@example.com">Send email</a> 

Button as a Link

     <button onclick="document.location='https://google.com'">HTML Tutorial</button> 

Link Titles

     <a href="https://www.w3schools.com/html/" title="Go to W3Schools HTML section">Visit our HTML Tutorial</a> 

Summary
    
    Use the <a> element to define a link
    Use the href attribute to define the link address
    Use the target attribute to define where to open the linked document
    Use the <img> element (inside <a>) to use an image as a link
    Use the mailto: scheme inside the href attribute to create a link that opens the user's email program

## images

    Use the HTML <img> element to define an image
    Use the HTML src attribute to define the URL of the image
    Use the HTML alt attribute to define an alternate text for an image, if it cannot be displayed
    Use the HTML width and height attributes or the CSS width and height properties to define the size of the image
    Use the CSS float property to let the image float to the left or to the right

## HTML image tags

Tag         Description
<img>       Defines an image
<map>       Defines an image map
<area>      Defines a clickable area inside an image map
<picture>   Defines a container for multiple image resources

The HTML `<map>` tag defines an image `map`. An image `map` is an image with c`lickable areas`. The areas are defined with one or more `<area>` tags. 

## Background Image on a HTML element

     <p style="background-image: url('img_girl.jpg');"> 

To avoid the background image from `repeating` itself, set the `background-repeat` property to `no-repeat`.

 <style>
 body {
  background-image: url('example_img_girl.jpg');
  background-repeat: no-repeat;
 }
 </style>

If you want the background image to cover the entire element, you can set the background-size property to cover.

Also, to make sure the entire element is always covered, set the background-attachment property to fixed:

This way, the background image will cover the entire element, with no stretching (the image will keep its original proportions):

     <style>
     body {
      background-image: url('img_girl.jpg');
      background-repeat: no-repeat;
      background-attachment: fixed;
      background-size: cover;
    }
    </style> 

## picture

The HTML `<picture>` element allows you to display different pictures for different devices or screen sizes.

     <picture>
     <source media="(min-width: 650px)" srcset="img_food.jpg">
     <source media="(min-width: 465px)" srcset="img_car.jpg">
     <img src="img_girl.jpg">
     </picture> 

## favicon

A `favicon` is a small image displayed next to the page title in the browser tab.

    <!DOCTYPE html>
    <html>
    <head>
      <title>My Page Title</title>
      <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
    </head>

## tables

A `table` in HTML consists of table cells (`ячейки`) inside rows and columns.
    
     <table>
        <tr>
            <th>Company</th>
            <th>Contact</th>
            <th>Country</th>
        </tr>
        <tr>
            <td>Alfreds Futterkiste</td>
            <td>Maria Anders</td>
            <td>Germany</td>
        </tr>
        <tr>
            <td>Centro comercial Moctezuma</td>
            <td>Francisco Chang</td>
            <td>Mexico</td>
        </tr>
    </table>

Each table `cell` is defined by a `<td>` and a `</td>` tag.

`td` stands for table data.

Everything between `<td>` and `</td>` are the content of the table cell.

Each table `row` starts with a `<tr>` and ends with a `</tr>` tag.

`tr` stands for table row.

Sometimes you want your `cells` to be table `header` cells. In those cases use the `<th>` tag instead of the `<td>` tag:

     <table>
        <tr>
            <th>Person 1</th>
            <th>Person 2</th>
            <th>Person 3</th>
        </tr>
        <tr>
            <td>Emil</td>
            <td>Tobias</td>
            <td>Linus</td>
        </tr>
        <tr>
            <td>16</td>
            <td>14</td>
            <td>10</td>
        </tr>
    </table> 

By default, the text in `<th>` elements are `bold` and `centered`, but you can change that with `CSS`. 

## html table tags

Tag         Description

<table>     Defines a table
<th>        Defines a header cell in a table
<tr>        Defines a row in a table
<td>        Defines a cell in a table
<caption>   Defines a table caption (`заголовок`)
<colgroup>  Specifies a group of one or more columns in a table for formatting
<col>       Specifies column properties for each column within a <colgroup> el
<thead>     Groups the header content in a table
<tbody>     Groups the body content in a table
<tfoot>     Groups the footer (нижний колонтитул) content in a table

## HTML Table Borders

To add a `border`, use the `CSS` border property on table, `th`, and `td` elements: --> double borders

    table, th, td {
        border: 1px solid black;
    }

Collapsed Table Borders

To avoid having double borders like in the example above, set the CSS `border-collapse` property to `collapse`.

     table, th, td {
        border: 1px solid black;
        border-collapse: collapse;
    }



    <style>
      table,
      th,
      td {
        border: 1px solid white;
        border-collapse: collapse;
      }
      th,
      td {
        background-color: #96d4d4;
      }
    </style>

With the `border-radius` property, the borders get rounded corners:

     table, th, td {
        border: 1px solid black;
        border-radius: 10px;
    }

Dotted Table Borders

With the `border-style` property, you can set the appearance of the border.

     th, td {
        border-style: dotted;
    }

Border Color

With the `border-color` property, you can set the color of the border.

     th, td {
        border-color: #96D4D4;
    }

## HTML Table Sizes

HTML tables can have different sizes for each column, row or the entire table.

Use the style attribute with the `width` or `height` properties to specify the size of a table, row or column.

To set the `width` of a table, add the style attribute to the `<table>` element:

    <table style="width:100%">

To set the size of a specific `column`, add the style attribute on a `<th>` or `<td>` element:

    <th style="width:70%">Firstname</th>

    <tr style="height:200px">

## HTML Table Headers

Vertical Table Headers

     <table>
        <tr>
            <th>Firstname</th>
            <td>Jill</td>
            <td>Eve</td>
         </tr>
         <tr>
            <th>Lastname</th>
            <td>Smith</td>
            <td>Jackson</td>
        </tr>
        <tr>
            <th>Age</th>
            <td>94</td>
            <td>50</td>
        </tr>
    </table>

Align (`выровнять`) Table Headers

    th {
        text-align: left;
    }

Header for Multiple Columns

To do this, use the `colspan` attribute on the `<th>` element:

    <table>
      <tr>
        <th colspan="2">Name</th>
        <th>Age</th>
      </tr>
    </table>

Table Caption (`заголовок`)

    <table style="width:100%">
      <caption>Monthly savings</caption>

## HTML Table - Zebra Stripes

To style every other table row element, use the `:nth-child(even)` selector like this:

     tr:nth-child(even) {
      background-color: #D6EEEE;
    }

> Note: If you use `(odd)` instead of `(even)`, the styling will occur on row 1,3,5 etc. instead of 2,4,6 etc.

HTML Table - Vertical Zebra Stripes

    td:nth-child(even), th:nth-child(even) {
      background-color: #D6EEEE;
    } 


    tr:nth-child(even) {
      background-color: rgba(150, 212, 212, 0.4);
    }

    th:nth-child(even),td:nth-child(even) {
      background-color: rgba(150, 212, 212, 0.4);
    } 

## Hoverable Table

Use the `:hover` selector on tr to highlight table rows on `mouse over`:

     tr:hover {background-color: #D6EEEE;} --> highlight the table rows

     td:hover {background-color: #D6EEEE;} --> highlight the table cells

## HTML Lists

Unordered HTML List

An unordered list starts with the `<ul>` tag. Each list item starts with the `<li>` tag.

     <ul>
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ul> 

Ordered HTML List

An ordered list starts with the `<ol>` tag. Each list item starts with the `<li>` tag.

     <ol>
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ol> 

Unordered HTML List - Choose List Item Marker

The CSS `list-style-type` property is used to define the style of the list item marker. It can have one of the following values:

    Value   Description
    disc    Sets the list item marker to a bullet (default)
    circle  Sets the list item marker to a circle
    square  Sets the list item marker to a square
    none    The list items will not be marked

    <ul style="list-style-type:disc;">

Horizontal List with CSS

    <!DOCTYPE html>
    <html lang="en-US">
      <head>
        <style>
          ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
            overflow: hidden;
            background-color: #333333;
          }

          li {
            float: left;
          }

          li a {
            display: block;
            color: white;
            text-align: center;
            padding: 16px;
            text-decoration: none;
          }

          li a:hover {
            background-color: #111111;
          }
        </style>
      </head>
      <body>
        <ul>
          <li><a href="#home">Home</a></li>
          <li><a href="#news">News</a></li>
          <li><a href="#contact">Contact</a></li>
          <li><a href="#about">About</a></li>
        </ul>
      </body>
    </html>

Ordered HTML List - The Type Attribute

    Type        Description
    type="1"    The list items will be numbered with numbers (default)
    type="A"    The list items will be numbered with uppercase letters
    type="a"    The list items will be numbered with lowercase letters
    type="I"    The list items will be numbered with uppercase roman numbers
    type="i"    The list items will be numbered with lowercase roman numbers

     <ol type="1">
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
     </ol> 

Control List Counting

    <ol start="50">

## Block-level Elements

Two commonly used block elements are: `<p>` and `<div>`.

The `<p>` element defines a paragraph in an HTML document.

The `<div>` element defines a division or a section in an HTML document.

    <address>
    <article>
    <aside>
    <blockquote>
    <canvas>
    <dd>
    <div>
    <dl>
    <dt>
    <fieldset>
    <figcaption>
    <figure>
    <footer>
    <form>
    <h1>-<h6>
    <header>
    <hr>
    <li>
    <main>
    <nav>
    <noscript>
    <ol>
    <p>
    <pre>
    <section>
    <table>
    <tfoot>
    <ul>
    <video>

## Inline Elements

An inline element does not start on a `new line`.

An inline element only takes up as much width as necessary.
    
    <a>
    <abbr>
    <acronym>
    <b>
    <bdo>
    <big>
    <br>
    <button>
    <cite>
    <code>
    <dfn>
    <em>
    <i>
    <img>
    <input>
    <kbd>
    <label>
    <map>
    <object>
    <output>
    <q>
    <samp>
    <script>
    <select>
    <small>
    <span>
    <strong>
    <sub>
    <sup>
    <textarea>
    <time>
    <tt>
    <var>

> Note: An inline element `cannot` contain a block-level element!

## The <div> Element

The `<div>` element is often used as a container for other HTML elements.

The `<div>` element has no required attributes, but `style`, `class` and `id` are common.

When used together with CSS, the `<div>` element can be used to style blocks of content:

    <div style="background-color:black;color:white;padding:20px;">

## The <span> Element

The `<span>` element is an inline container used to mark up a part of a text, or a part of a document.

The `<span>` element has no required attributes, but `style`, `class` and `id` are common.

    <p>My mother has <span style="color:blue;font-weight:bold;">blue</span> eyes and my father has <span style="color:darkolivegreen;font-weight:bold;">dark green</span> eyes.</p>

## HTML class Attribute

The HTML `class` attribute is used to specify a class for an HTML element.

The `class` attribute is often used to point to a class name in a style sheet. It can also be used by a `JavaScript` to access and manipulate elements with the specific class name.

> `Tip:` The class attribute can be used on any HTML element.

> `Note:` The class name is case sensitive!

## Multiple Classes

To define multiple classes, separate the class names with a `space`, e.g. `<div class="city main">`. The element will be styled according to all the classes specified.

Different Elements Can Share Same Class

## HTML id Attribute

The HTML `id` attribute is used to specify a `unique id` for an HTML element.
You cannot have more than one element with the same id in an HTML document.

> Note: The id name is case sensitive!

> Note: The id name must contain at least one character, cannot start with a number, and must not contain whitespaces (spaces, tabs, etc.).

A `class` name can be used by `multiple` HTML elements, while an `id` name must only be used by `one` HTML element within the page.

## HTML Iframes

An HTML `iframe` is used to display a web page within a web page.

     <iframe src="url" title="description"></iframe> 

Iframe - Set Height and Width

     <iframe src="demo_iframe.htm" height="200" width="300" title="Iframe Example"></iframe> 

Iframe - Remove the Border

     <iframe src="demo_iframe.htm" style="border:none;" title="Iframe Example"></iframe> 

Iframe - Target for a Link

    <iframe src="demo_iframe.htm" name="iframe_a" title="Iframe Example"></iframe>

    <p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p> 

## The HTML <noscript> Tag

The HTML `<noscript>` tag defines an alternate content to be displayed to users that have disabled scripts in their browser or have a browser that doesn't support scripts.

## HTML - The Head Element

The HTML <head> element is a container for the following elements: <title>, <style>, <meta>, <link>, <script>, and <base></style>.

Setting The Viewport

The viewport is the user's visible area of a web page.
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

The `<base>` element specifies the base URL and/or target for all relative URLs in a page.

## HTML Responsive Web Design

Responsive web design is about creating web pages that look good on all devices!

A responsive web design will automatically adjust for different screen sizes and viewports.

Setting The Viewport

     <meta name="viewport" content="width=device-width, initial-scale=1.0"> 

## html entities

Result  Description                         Entity  Entity Number 
        non-breaking space                  &nbsp;  &#160;  
<       less than                           &lt;    &#60;   
>       greater than                        &gt;    &#62;   
&       ampersand                           &amp;   &#38;   
"       double quotation mark               &quot;  &#34;   
'       single quotation mark (apostrophe)  &apos;  &#39;

[entities](https://www.w3schools.com/html/html_entities.asp)

😀   &#128512;   
😁   &#128513;   
😂   &#128514;   
😃   &#128515;   
😄   &#128516;   
😅   &#128517;
<p>&#128512;</p>

## HTML Uniform Resource Locators

    scheme://prefix.domain:port/path/filename 

    scheme - defines the type of Internet service (most common is http or https)
    prefix - defines a domain prefix (default for http is www)
    domain - defines the Internet domain name (like w3schools.com)
    port   - defines the port number at the host (default for http is 80)
    path   - defines a path at the server (If omitted: the root directory of the site)
    filename - defines the name of a document or resource

## comon url schemes

    Scheme  Short for                           Used for
    http    HyperText Transfer Protocol         Common web pages. Not encrypted
    https   Secure HyperText Transfer Protocol  Secure web pages. Encrypted
    ftp     File Transfer Protocol              Downloading or uploading files
    file                                        A file on your computer

## URL Encoding

URLs can only be sent over the Internet using the `ASCII` character-set. If a URL contains characters outside the ASCII set, the URL has to be `converted`.

URL encoding converts `non-ASCII` characters into a format that can be transmitted over the Internet.

URL encoding replaces `non-ASCII` characters with a `"%"` followed by hexadecimal digits.

URLs cannot contain `spaces`. URL encoding normally replaces a space with a plus `(+)` sign, or `%20`.

## HTML Versus XHTML

XHTML is a stricter, more XML-based version of HTML.
(более строгая версия HTML)

Browsers ignore errors in HTML pages, and try to display the website even if it has some errors in the markup. So `XHTML` comes with a much stricter error handling.

## The Most Important Differences from HTML
    
    <!DOCTYPE> is mandatory
    The xmlns attribute in <html> is mandatory
    <html>, <head>, <title>, and <body> are mandatory
    Elements must always be properly nested
    Elements must always be closed
    Elements must always be in lowercase
    Attribute names must always be in lowercase
    Attribute values must always be quoted
    Attribute minimization is forbidden

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
      <title>Title of document</title>
    </head>
    <body>

## HTML Forms

An HTML form is used to collect `user input`. The user input is most often sent to a server for processing. 

### The <input> Element

An `<input>` element can be displayed in many ways, depending on the type attribute.

Type                    Description
<input type="text">     Displays a single-line text input field
<input type="radio">    Displays a radio button (for selecting one of many choices)
<input type="checkbox">     Displays a checkbox (for selecting zero or more of many choices)
<input type="submit">   Displays a submit button (for submitting the form)
<input type="button">   Displays a clickable button

The `<input type="text">` defines a single-line input field for text input.

```html
 <form>
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname">
</form> 
```
> Note: The form itself is not visible. Also note that the default width of an input field is 20 characters.

### The <label> Element

The `<label>` tag defines a label for many form elements.

The `for` attribute of the `<label>` tag should be equal to the `id` attribute of the <input> element to bind them together. 

### Radio Buttons

```html
<form>
  <input type="radio" id="html" name="fav_language" value="HTML">
  <label for="html">HTML</label><br>
  <input type="radio" id="css" name="fav_language" value="CSS">
  <label for="css">CSS</label><br>
  <input type="radio" id="javascript" name="fav_language" value="JavaScript">
  <label for="javascript">JavaScript</label>
</form>
```

### Checkboxes

```html
 <form>
  <input type="checkbox" id="vehicle1" name="vehicle1" value="Bike">
  <label for="vehicle1"> I have a bike</label><br>
  <input type="checkbox" id="vehicle2" name="vehicle2" value="Car">
  <label for="vehicle2"> I have a car</label><br>
  <input type="checkbox" id="vehicle3" name="vehicle3" value="Boat">
  <label for="vehicle3"> I have a boat</label>
</form> 
```

### The Submit Button

The `<input type="submit">` defines a button for submitting the form data to a form-handler.

The form-handler is specified in the form's `action` attribute.

> Tip: Always use POST if the form data contains sensitive or personal information!

> NEVER use `GET` to send `sensitive` data! (the submitted form data is visible in the URL!)

Notes on GET:

    Appends the form data to the URL, in name/value pairs
    NEVER use GET to send sensitive data! (the submitted form data is visible in the URL!)
    The length of a URL is limited (2048 characters)
    Useful for form submissions where a user wants to bookmark the result
    GET is good for non-secure data, like query strings in Google

Notes on POST:

    Appends the form data inside the body of the HTTP request (the submitted form data is not shown in the URL)
    POST has no size limitations, and can be used to send large amounts of data.
    Form submissions with POST cannot be bookmarked

### The Autocomplete Attribute

The `autocomplete` attribute specifies whether a form should have autocomplete on or off.

```html
<form action="/action_page.php" autocomplete="on"> 
```

## The HTML <form> Elements

    <input>
    <label>
    <select>
    <textarea>
    <button>
    <fieldset>
    <legend>
    <datalist>
    <output>
    <option>
    <optgroup>

### The <select> Element

The `<select>` element defines a drop-down list.

```html
<label for="cars">Choose a car:</label>
<select id="cars" name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select> 
```

Allow Multiple Selections:

Use the `multiple` attribute to allow the user to select more than one value:

```html
<label for="cars">Choose a car:</label>
<select id="cars" name="cars" size="4" multiple>
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select> 
```

### The <button> Element

The `<button>` element defines a clickable button.

```html
<button type="button" onclick="alert('Hello World!')">Click Me!</button> 
```

### HTML Input Types

    <input type="button">
    <input type="checkbox">
    <input type="color">
    <input type="date">
    <input type="datetime-local">
    <input type="email">
    <input type="file">
    <input type="hidden">
    <input type="image">
    <input type="month">
    <input type="number">
    <input type="password">
    <input type="radio">
    <input type="range">
    <input type="reset">
    <input type="search">
    <input type="submit">
    <input type="tel">
    <input type="text">
    <input type="time">
    <input type="url">
    <input type="week">

> Tip: The default value of the type attribute is "text".

The `<input type="hidden">` defines a hidden input field (not visible to a user).

## HTML Video

The HTML `<video>` element is used to show a video on a web page.

The `controls` attribute adds video controls, like play, pause, and volume.

```html
<video width="320" height="240" controls>
```

