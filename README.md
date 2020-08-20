Microsoft 70-480 Exam Study Guide
=============================

Programming in HTML5 with JavaScript and CSS3
-----------------------------------------------------------

### Table of Contents

**[Intro](#intro)**

**[CSS](#css)**  

 - **[Standard Selectors](#standard-selectors)**
 - **[Pseudo Classes](#pseudo-classes)**
 - **[Pseudo Elements](#pseudo-elements)**
 - **[Precedence](#precedence)**
 - **[Specificity](#specificity)**
 - **[Link Pseudo Class Selectors](#link-pseudo-class-selectors)**
 - **[jQuery Selectors](#jquery-selectors)**
 - **[Positioning](#positioning)**
 - **[Fonts](#fonts)**
 - **[Properties](#properties)**
 - **[Animations](#animations)**
 - **[Flexbox](#flexbox)**
 - **[Grid Display](#grid-display)**
 - **[Regions](#regions)**
 - **[Exclusions](#exclusions)**
 - **[2D Tranforms](#2d-transforms)**
 - **[3D Transforms](#3d-transforms)**

**[HTML](#html)**  

 - **[Basic Layout](#basic-layout)**
 - **[Semantic Elements](#semantic-elements)**
 - **[Form Validation](#form-validation)**
 - **[App Cache](#app-cache)**
 - **[SVG](#svg)**
 - **[Video](#video)**
 - **[Audio](#audio)**
 - **[colgroup](#colgroup)**

**[JavaScript](#javascript)**

 - **[AJAX](#ajax)**
 - **[Serialization and Forms](#serialization-and-forms)**
 - **[RegEx and Validation](#regex-and-validation)**
 - **[Async with jQuery](#async-with-jquery)**
 - **[Web Workers](#web-workers)**
 - **[Web Messaging](#web-messaging)**
 - **[Web Sockets](#web-sockets)**
 - **[Web Storage](#web-storage)**
 - **[Prototype Inheritance](#prototype-inheritance)**
 - **[Functions](#functions)**
 - **[Arrays](#arrays)**
 - **[Geo-location API](#geo-location-api)**
 - **[DOM Manipulation](#dom-manipulation)**
 - **[Canvas](#canvas)**
 - **[Drag and Drop](#drag-and-drop)**

### Intro

Books

 - [JavaScript: The Good Parts by Douglas Crockford](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742)
 - [Training Guide Programming in HTML5 with JavaScript and CSS3 by Glenn Johnson](http://www.amazon.com/Training-Guide-Programming-JavaScript-Microsoft/dp/0735674388)

Resources

 - [Mozilla Developer Network](https://developer.mozilla.org)
 - [CSS Tricks](http://css-tricks.com/)

### CSS 

#### Standard Selectors

    button //element
    #someId
    .someClass
    * //universal selector, avoid
    table td //descendent
    div > p //child
    div + h1 //subsequent adjacent sibling
    div ~ h1 //subsequent sibling
    a[href] //attribute
    a[href='http://localhost'] //equals
    a[href*='localhost'] //contains
    a[href^='https'] //starts with
    a[href$='.png'] //ends with
    a[data-bind~='css'] //contains - space separated

#### Pseudo Classes

    :link
    :visited
    :active
    :hover
    :focus
    :checked
    :lang(language) 
    :not(selector)
    :first-child
    :last-child
    :nth-child(an+b) 
    :nth-last-child(an+b)
    :only-child
    :only-of-type
    :first-of-type
    :last-of-type
    :target //ID at end of URL - e.g. 'http://a.com/index.html#test'
    
    //examples
    p:lang(en) {}
    div p:nth-child(3n+2) {}

#### Pseudo Elements

    ::first-line
    ::first-letter
    ::before //can set content
    ::after //can set content
    
    //examples
    #myParagraph::after {
    	color: #FFF;
    	content: 'test content';
    }
    #myParagraph::first-letter {
    	font-weight: bold;
    }


#### Precedence

 1. browser - lowest precedence
 2. user
 3. author
 4. author !important
 5. user !important - highest precedence

#### Specificity

a is most significant, followed by b, then c

 - a = # of id selectors
 - b = # of class, attribute, and pseudo class selectors
 - c = # of element selectors


#### Link Pseudo Class Selectors

Order is important

 1. `a:link` and/or `a:visited`
 2. `a:hover`
 3. `a:active` - when clicked

#### jQuery Selectors

    :contains('blah') //matches elements containing the specified text
    :header //h1, h2, etc.
    
    //example
    $("p:contains('blah')")


#### Positioning

 - fixed - positioned relative to view-port, taken out of flow
 - absolute - positioned relative to nearest positioned (non-static) ancestor, taken out of flow
 - relative - normal flow, then offset by `top` and `left`
 - static - default, normal flow

#### Fonts


    @font-face {
    	font-family: "Some Name";
    	src: local("Arial"),
    	     url("YourCustomFont.ttf");
    	font-weight: bold;
    }
    p {
    	font-family: "Some Name", Serif;
    }

#### Properties

The `initial` and `inherit` values have been left off intentionally. The first value listed is the default.  
    
    /* determines how far background extends */
    background-clip: border-box | padding-box | content-box; 
    background-repeat: repeat | repeat-x | repeat-y | no-repeat;
    border: 1px solid black;
    border-radius: <top-left> <top-right> <bottom-right> <bottom-left>; //or just one
    border-style: none | solid | dotted | dashed | double | groove | ridge | inset | outset;
    box-sizing: content-box | padding-box | border-box;
    clip-path: url(blah.svg#test1) | polygon() | rect() | circle() | ellipse();
    columns: <min-column-width> <max-number-of-columns>; //column-count and column-width
    font-weight: normal | bold | bolder | lighter | 100 | 200 | ... | 900 ;
    font-style: normal | italic | oblique;
    letter-spacing: normal | <length>;
    opacity: <decimal in range 0 to 1>;
    overflow: visible | hidden | scroll | auto; /* auto adds scroll bars if needed */
    padding: <all> | <top&bottom> <left&right> | <top> <right> <bottom> <left>;
    text-align: left | right | center | justify;
    text-indent: <size>; /* first text in element */
    text-shadow: <x-offset> <y-offset> <blur-radius> <color>;


Axis for x, y offsets

    (0, 0)
        ----------- +x
        |
        |
        |
        +
        y

Some properties such as `color` inherit by default. For other properties you can force inheritance by using the `inherit` value.


#### Animations

    .classToAminate {
		    /* <name> <duration> <delay> <# of times> <fill mode> */
	    animation: Your-Animation 5s 1s infinite backwards;
    }
    @keyframes Your-Animation {
	      0% { opacity: 0.1; } /* can use 'from' instead of '0%' */
	     50% { opacity: 0.2; }
	    100% { opacity: 0.8; } /* can use 'to' instead of '100%' */
    }

#### Flexbox

Supported by all latest browsers

    .container {
	    display: flex; /* or inline-flex */
	    flex-direction: row | row-reverse | column | column-reverse;
	    flex-wrap: nowrap | wrap | wrap-reverse;
	    justify-content: flex-start | flex-end | center | space-between | space-around;
	    /* for cross-axis */
	    align-items: flex-start | flex-end | center | stretch | baseline;
	    /* like justify-content for cross-axis, only applies when wrapping */
	    align-content: flex-start | flex-end | center | space-between | space-around;
    }
    .item {
	    order: <integer>; /* default 0 */
	    flex-grow: <number>; /* default 0 */
	    flex-shrink: <number>; /* default 1 */
	    flex-basis: main-size | <length>; /* size before distributing space according to flex factors */
	    flex: <flex-grow> <flex-shrink> <flex-basis>;
	    /* overrides container align-items setting */
	    align-self: auto | flex-start | flex-end | center | baseline | stretch;
    }

Interactive demo that allows you to see how modifying properties affect the layout:
[http://demo.agektmr.com/flexbox](http://demo.agektmr.com/flexbox)
    
#### Grid Display
Only supported by IE currently, use -ms- prefix for IE 10.

    display: ms-grid; /* IE 10 */
    display: grid; /* or inline-grid */
    /* column 1 = 100px wide, 2 = 2%, 3 = remaining space */
    grid-columns: 100px 2% 1fr; 
    grid-rows: auto 10px auto 10px auto; /* auto means content will determine size */
    .header, .footer {
	    grid-column-span: 3;
    }
    .header {
	    grid-row: 1;
    }
    .footer {
	    grid-row: 5;
    }	    
    .main {
	    grid-column: 3;
	    grid-row: 3;
    }

#### Regions

Only supported with iframe sources in IE, use -ms- prefix. Chrome and Firefox don't support.

    <div class="text">
	    Blah blah blah...
    </div>
    <div class="containers"></div>
    <div class="containers"></div>

    .text {
	    flow-into: text-flow; /* text-flow is an arbitrary name */
    }
    .containers {
	    flow-from: text-flow;
    }

#### Exclusions

    wrap-flow: auto | clear | both | end | start;
	    
#### 2D Transforms

Use relative position on parent, absolute on child. Set child width to 100%.

    transform:
	    translate(x, y) /* e.g. translate(200px, 150px) */
	    rotate(angle) /* e.g. rotate(30deg) */
	    scale(sx, sy); /* e.g. scale(1.5, 2.2) */
	    
#### 3D Transforms

Use relative position on parent, absolute on child. Set child width to 100%.

    perspective: 1000px; /* enables 3d space for children */

    /* child styles */
    transform-style: preserve-3d;
    transform: 
	    perspective(500px) /* gives depth */
	    rotateX(10px)
	    rotatey(10px)
	    rotateZ(10px)
	    translateZ(10px)
	    scaleZ(10);

#### Media Queries

    <link rel="stylesheet" media="screen and (min-width: 700px)" href="a.css"/>
    @media screen {}
    @media print {}
    /* all is implied, not necessary */
    @media all and (max-width: 699px) and (min-width: 520px), (max-width: 200px) {}


### HTML

#### Basic Layout

    <!DOCTYPE html>
	    <html>
    <head>
	    <meta charset="utf-8" />
	    <title>A Title</title>
	    <link href="css/style.css" rel="stylesheet" />
	    <script src="js/test.js"></script>
    </head>
    <body>
	    <header>
		    <h1>Header</h1>
		    <nav>
			    <ul>
				    ...
			    </ul>
		    </nav>
	    </header>
	    <section>
		    <article>
			    <header>
				    <h1>...</h1>
				    <h2>...</h2>
			    </header>
			    <p>...</p>
		    </article>
	    </section>
	    <aside>...</aside>
	    <footer>...</footer>
    </body>
    </html>

#### Semantic Elements

 - section
 - nav
 - article - self contained
 - aside - loosely related, could be removed
 - header
 - footer
 - figure
	 - figcaption
 - details - just the summary is displayed unless clicked
	 - summary
 - strong
 - em
 - abbr - set title attribute
 - address - contact info for the author of a document
 - blockquote, q - use cite within for the name of the 
 - code, samp - use `white-space: pre` to preserve white space
 - pre
 - var
 - wbr - suggested breaking point
 - dfn
 - dl - description list
 - dt, dd - term, description- don't nest
 - caption - table caption - first element in table

#### Form Validation

Name must be specified on the element for validation to work

 - type - email, date, number, range, color, search, tel, url
 - required
 - min, max, step
 - autofocus, placeholder
 - pattern - must match entire value - regex


#### App Cache

Including in html:

    <html manifest="example.appcache">...</html>

The cache is cleared if the manifest changes, including a date is a good option. Example cache manifest file:

    CACHE MANIFEST
    # 11/16/2014 
    CACHE:
	    img/logo.jpg
    NETWORK:
	    *
    FALLBACK:
	    index.aspx staticIndex.html
	    images/ backup/notFoundImage.jpg

#### SVG

Scalable Vector Graphics. SVG example:

    <svg width="500" height="300" xmlns="...">
	    <path ... />
	    <circle ... />
	    <polygon ... />
	    <rect ... />
	    <text ... />
    </svg>
    <!-- viewBox="minX minY x y" controls what portion of the image is displayed -->
    <svg width="100%" height="100%" viewBox="0 10 15 15">...</svg>

Usage:

    <image src="test.svg" />

#### Video

    <video controls="controls" height="500">
	    <source src="..." type="..." />
	    <source src="..." type="..." />
    </video>

Attributes: autoplay, controls, height, loop, muted, poster, preload, src, width

Formats

 - .ogv - not IE, iPhone, or Android
 - .webm - not iPhone
 - .mp4 - not Firefox or Opera


#### Audio

    <audio id="test" controls="controls">
	    <source src="..." type="..." />
	    <source src="..." type="..." />
    </audio >

Attributes: autoplay, controls, loop, preload, src

Formats

 - .oga/.ogg
 - .mp3,
 - .mp4/.mp4a/.aac
 - .wav

Using ogg and acc should give full browser support.

#### colgroup


    <table>
      <colgroup span="3">
	      <col width="15px" />
	      <col width="15px" />
	      <col class="col3" />
      </colgroup>
      <colgroup span="1"></colgroup>
      <tr>
        <td>Column A</td>
        <td>Column B</td>
        <td>Column C</td>
        <td>Column D</td>
      </tr>
    </table>



### JavaScript

#### AJAX

    $.ajax({
	    url: 'url',
	    type: 'POST',
	    data: formData,
	    async: true, //default is true
	    cache: true, //default is true
	    complete: someFunc, //called after success and error
	    //error, password, success, username
    }).done(function(data) {...}).fail(func).always(func);

Without jQuery

    var request = new XMLHttpRequest();
    request.onload = function test() {
	    console.log(this.responseText);
    };
    request.open("get", "yourService", true /* async */);

Events: progress, load, error, abort, readystatechange
Properties: responseText, responseXML, response, readyState, status

readyState:

 - 0 - READYSTATE_UNINITIALIZED
 - 1 - READYSTATE_LOADING
 - 2 - READYSTATE_LOADED - sent
 - 3 - READYSTATE_INTERACTIVE - some data received, still receiving
 - 4 - READYSTATE_COMPLETE


    
#### Serialization and Forms

    $("form").serialize() //to URL encoded string
    $("form").serializeArray() //to array of name value pairs
    $.parseXML("string") //XML string to XML document that can be passed to jQuery to parse
    JSON.parse(str)
    JSON.stringify(obj)
    $.parseJSON(str)
    encodeURI(str) //encodes string for use as a URL
    encodeURIComponent(str) //encodes string for use in part of a URL
    $.toJSON(data) //removed from jQuery in 1.9
    JSON.stringify($("form").serializeArray()) //string [{"name":,"value":}] for POSTing


#### RegEx and Validation

Regex

    var str = "test";
    var re = /[a-z]+/; //or new RegExp("[a-z]+") to be dynamic
    var array = re.exec(str);
    var newStr = str.replace(re, "blah"); //access groups created with () by $1, $2, ... in the replacement string
    re.test(str);
    
Handy validation functions

    typeOf(x)
    isNaN(x)
    parseFloat(x)
    isFinite(x)


#### Async with jQuery

Promises created from a $.Deferred() object

Deferred methods

 - resolve
 - resolveWith
 - notify
 - notifyWith
 - reject
 - rejectWith
 - promise

Promise methods

 - always
 - done
 - fail
 - pipe
 - progress
 - state
 - then


#### Web Workers

Non blocking, can't access DOM

    var worker = new Worker("myWorker.js");
    worker.onmessage = function(e) {
	    console.log(e.data);
    }
    worker.onerror = function(e) {
	    console.log(e.data);
    }
    worker.postMessage("blah");
    worker.terminate(); //force kills without cleanup
    //worker itself can call close()

Web worker timeouts and intervals

    var timeoutId = setTimeout(func, delay /*ms*/);
    clearTimeout(timeoutId);
    
    var intervalId = setInterval(func, delay); //runs repeatedly
    clearInterval(intervalId);

#### Web Messaging

Communication with other tabs, windows, and frames.

    window.postMessage("message", "http://test.com");
    window.addEventListener("message", messageHandler, false /*capture*/);
    function messageHandler(e) {
	    if (e.origin == "http://a.com") {
		    //use e.data
	    }
    }


#### Web Sockets

TCP based, full-duplex continuous connection.

Functions: send, close, onclose, onerror, onmessage, onopen, porotocol, readystate, url, binaryType, bufferedAmount

    var webSocket = new WebSocket(url);
    
    function sendMessage() {
	    if (webSocket.readyState !== WebSocket.OPEN) { return; }
	    webSocket.send("test");
    }
    
    webSocket.onmessage = function(e) {
	    // use e.data
    }
    
    webSocket.close();
    
Libraries

 - SignalR - ASP.Net
 - Socket.IO - Node.js


#### Web Storage 

localStorage and sessionStorage

    localStorage["test"]; //same as localStorage.getItem("test")
    localStorage["test"] = foo; //same as localStorage.setItem("test", foo);
    localStorage.removeItem("test");
    localStorage.clear();

`storage` event fires on any change

    window.addEventListener("storage", storageHandler, false);

storage event object properties

 - key
 - oldValue
 - newValue
 - url
 - storageArea


#### Prototype Inheritance

    var b = Object.create(a); //inherit from a
    
    //same as Object.create()
    function inherit(proto) {
      function F() {}     
      F.prototype = proto 
      return new F()      
    }

    for (var x in b) {
	    if (object.hasOwnProperty(x)) { ... }
    }
    
    someObject.prototype
    someObject.prototype.constructor


#### Functions

    getElementById
    getElementsByTagName
    getElementsByName
    getElementsByClass
    querySelector //first match - CSS selector
    querySelectorAll

    addEventListener(eventName, function, useCapture)
    attachEvent(eventName, function) //older IE & Opera
    removeEventListener(eventName, function, useCapture)
    detachEvent(eventName, function) //older IE & Opera
    e.stopPropogation()
    e.preventDefault()
    var target = event.target || event.srcElement; //srcElement is legacy IE only

    //fire an event
    var event = new Event("test");
    element.dispatchEvent(event);
    element.fireEvent("on"+event.eventType, event); //IE9 and below
    
    //iterate through object properties
    for (var x in object) {
	    if (object.hasOwnProperty(x)) { ... }
    }
    //use for loop for arrays

    //execute function immediately, bind to 'this' 
    func.call(this, arg1, arg2, ...);
    func.apply(this, argArray);
    
    //returns new function that is bound to 'this'
    func.bind(this, arg1, arg2, ...);

    

#### Arrays

    new Array()
    new Array('blah', 'test')
    arr = ['blah', 'test']
    
    .length
    .concat()
    .indexOf()
    .lastIndexOf()
    .join() //blah,test - takes optional separator parameter
    .pop() //removes last item, returns it
    .push() //adds to end, can pass multiple items to add
    .reverse()
    .shift() //removes first item, returns it
    .slice(start, end)
    .sort(func) //func is optional
    .splice(start, numToRemove, itemsToAdd, ...) //returns removed elements
    .toString() //comma separated like join
    .unshift() //adds to beginning, can pass multiple items to add
    .valueOf() //comma separated like join


#### Geo-location API

Use navigator.geolocation object.

    .getCurrentPosition(func(position){}, func(error){}, options);

position 

 - coords
	 - latitude
	 - longitude
	 - altitude
	 - accuracy
	 - altitudeaccuracy
	 - heading
	 - speed
 - timestamp


options

 - enableHighAccuracy
 - timeout - default is none (-1)
 - maximumAge in ms - default is no caching (0)


<!-- fix list/code bug -->

    var watchId = .getWatchPosition(func(position){}, func(error){}, options);
    
    function endWatch() {
	    if (watchId !== 0) {
		    .clearWatch(watchId);
		    watchId = 0;
	    }
    }

 

#### DOM Manipulation 

    parent.removeChild(item) //returns removed node
    element.cloneNode(deep) //deep = whether or not to clone children
    parent.appendChild(newChild) //adds to end of children
    parent.insertBefore(newElement, elementToInsertBefore)
    parent.replaceChild(newChild, oldChild)

    element.style.display = "none";
    element.style.visibility = "hidden"; //still takes up space just not visible
    
    $("#test").show()
    $("#test").hide()

    element.className //space delimited string
    element.classList //.add(), remove(), toggle(), contains()
    
#### Canvas

HTML

    <canvas id="a" width="200" height="150"></canvas>

JavaScript

    var canvas = document.getElementById("a");
    var context = canvas.getContext("2d");
    
    .fillStyle, strokeStyle, lineWidth, lineJoin
    .fillRect(x, y, width, height), strokeRect(...), clearRect(...)
    
    .beginPath()
    .moveTo(x, y)
    .lineTo(x, y)
    //draws clockwise by default
    //radians = (Math.PI/180)*degrees
    .arc(x, y, radius, startAngle, endAngle, anti-clockwise) 
    .arcTo(x1, y1, x2, y2, radius) //x0, y0 are current position draws from current position through arc
    .quadraticCurveTo()
    .bezierCurveTo()
    .closePath()
    .stroke() //or .fill()
    
    .font, textAlign, textBaseline
    context.font = "bold 12px sans-serif";
    context.fillText("test", 150, 200);
    
    var gradient = context.createLinearGradient(x0, y0, x1, y1)
    //.createRadialGradient(x0, y0, r0, x1, y1, r1)
    gradient.addColorStop(0, "black"); //range 0 to 1
    gradient.addColorStop(1, "white");
    context.fillStyle = gradient;
    context.fillRect(0, 0, 200, 100);
    context.save() //restore() - state context, stack

    var image = new Image();
    image.src = "...";
    image.onload = function() {
	    context.drawImage(image, x, y);
    }
    


#### Drag and Drop

Set attribute `draggable` to `true` to allow element to be dragged. In most browsers links, images, and selected text are draggable by default.
    
Use css `cursor: move` to give a visual cue that the element is draggable.    

Drag events

 - dragstart
 - drag //fires while element is being dragged
 - dragenter
 - dragleave
 - dragover
 - drop
 - dragend //fires when operation completes, whether or not it succeeded

    
   <!-- fix-->
    


    function handleDragStart(e) {
	    dragSource = this;
	    e.dataTransfer.effectAllowed = 'move';
	    e.dataTransfer.setData('text/html', this.innerHTML);
    }
    
    function handleDrop(e) {
	    e.stopPropogation();
	    e.preventDefault();
	    if (dragSource !== this) {
		    dragSource.innerHTML = this.innerHTML;
		    this.innerHTML = e.dataTransfer.getData('text/html');
	    }
    }

    
Handle dragging from desktop to browser

    function handleDrop(e) {
	    e.stopPropogation();
	    e.preventDefault();
	    
	    var files = e.dataTransfer.files;
	    for (var i = 0; i < files.length; i++) {
		    //read file objects
	    }
    }
