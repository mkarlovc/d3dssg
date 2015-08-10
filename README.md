# D3.js teachout at DSSG 2015

# Index

* [Fundementals](#fundementals)
  * [HTML](#html)
  * [CSS](#css)
  * [SVG](#svg)
  * [JavaScript](#javascript)
* [Building blocks](#adding-elements)
  * [Adding elements](#adding-elements)
  * [Binding data](#binding-data)
  * [Drawing divs](#drawing-divs)
  * [Using SVG](#using-svg)
  * [Transitions](#transitions)
  * [Binding events](#binding-events)
* [Examples](#examples)
  * [Barchart](#barchart)
  * [Network](#network)
  * [Something different](#community-evolution)
* [Resources](#resources)
 
# Visualizing Data with Web Standards
D3 is a **JavaScript** library that makes visualization easier without introducing a new way of representing an image, but doing transformations using existing standards - namely **HTML**, **CSS** and **SVG**.

# Fundementals
#### HTML
Hypertext Markup Language is used to structure content for web browsers. The simplest HTML page looks like this:
```<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        <h1>Page Title</h1>
        <p>This is a really interesting paragraph.</p>
    </body>
</html>
```
#### CSS
Cascading Style Sheets are used to style the visual presentation of HTML pages. A simple CSS stylesheet looks like this:
```
body {
    background-color: white;
    color: black;
}
```
CSS ZEN Garden illustration of separation of content and style: http://www.csszengarden.com/
#### SVG
SVG is a text-based image format, meaning you can specify what an SVG image should look like by writing simple markup code, sort of like HTML tags. SVG code can be included directly within any HTML document.
```
<svg width="50" height="50">
    <circle cx="25" cy="25" r="22"
     fill="blue" stroke="gray" stroke-width="2"/>
</svg>
```
#### JavaScript
JavaScript is a dynamic scripting language that can instruct the browser to make changes to a page after it has already loaded.
Scripts can be included directly in HTML, between two script tags:
```
<body>
    <script type="text/javascript">
        alert("Hello, world!");
    </script>
</body>
```
or stored in a separate file, and then referenced somewhere the HTML (commonly in the head):
```
<head>
    <title>Page Title</title>
    <script type="text/javascript" src="myscript.js"></script>
</head>
```
#### Fundemental parts
<img src="http://mkarlovc.github.io/d3dssg/img/fundementals.png"/>
#### Empty html page referencing css and js
http://mkarlovc.github.io/d3dssg/simple_HTML_CSS_JS/index.html
```
<html>
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="client.js"></script>
    <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  <body>
    <div id="first_div" class="box">This is first div element </div>
    <div id="second_div" class="box">This is the second div element</div>  
    <svg class="box">
      <circle cx="50" cy="50" r="50" fill="yellow" stroke="black" stroke-width="1"/>
    </svg>  
</body>
</html>
```
#### Style
http://mkarlovc.github.io/d3dssg/simple_HTML_CSS_JS/style.css

```
.box {
  width: 400px;
  height: 100px;
  border: solid black 4px;
  margin: 20px;
  text-align: center;
  font-family: serif;
}

#first_div {
 background-color: #FAB8FF;
}

#second_div {
  background-color: #FF530C;
}

```
#### JavaScript client side interactions
http://mkarlovc.github.io/d3dssg/simple_HTML_CSS_JS/client.js
```
$(document).ready(function(){

  $("#first_div").click(function(e){
    alert("hi first box");
  });

  $("#second_div").click(function(e){
    alert("hi second box");
  });  

});
```
# Adding elements
1. Selects a single element from the **DOM** using CSS selector syntax
2. Created a new **p** element and appended that to the end of our selection
3. Set the text content of that new, empty paragraph to **“New paragraph!**”
```
d3.select("body").append("p").text("New paragraph!");
```
http://mkarlovc.github.io/d3dssg/buildingblocks/2.html
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>D3 Test</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
  </head>
  <body>
    <script type="text/javascript">
      d3.select("body")
        .append("p")
        .text("New paragraph!");
    </script>
  </body>
</html>
```
# Binding data
With D3, we bind our data input values to elements in the DOM. Binding is like “attaching” or associating data to specific elements, so that later you can reference those values to apply mapping rules.

Handling different kinds of data: array of numbers, strings, or objects, JSON (and GeoJSON).

#### Example of using array of numbers
http://mkarlovc.github.io/d3dssg/buildingblocks/3.html:
```
var dataset = [ 5, 10, 15, 20, 25 ];
d3.select("body").selectAll("p")
    .data(dataset)
    .enter()
    .append("p")
    .text("New paragraph!");
```
#### Passing values to functions
http://mkarlovc.github.io/d3dssg/buildingblocks/4.html
```
var dataset = [ 5, 10, 15, 20, 25 ];
d3.select("body").selectAll("p")
    .data(dataset)
    .enter()
    .append("p")
    .text(function(d) { return "Paragraph value "+d; });
```
#### Adding attributes
http://mkarlovc.github.io/d3dssg/buildingblocks/5.html
```
var dataset = [ 5, 10, 15, 20, 25 ];
      d3.select("body").selectAll("p")
        .data(dataset)
        .enter()
        .append("p")
        .text(function(d) { return "Paragraph value "+d; })
        .style("color", "red");
```
# Drawing divs
attr() is used to set an HTML attribute and its value on an element. An HTML attribute is any property/value pair that you could include between an element’s <> brackets.
#### Binding data and drawing divs
http://mkarlovc.github.io/d3dssg/buildingblocks/7.html
```
var dataset = [ 25, 7, 5, 26, 11, 8, 25, 14, 23, 19,
                14, 11, 22, 29, 11, 13, 12, 17, 18, 10,
                24, 18, 25, 9, 3 ];

d3.select("body").selectAll("div")
	 .data(dataset)
	 .enter()
	 .append("div")
	 .attr("class", "bar");
```
#### Controling div height with data
http://mkarlovc.github.io/d3dssg/buildingblocks/8.html
```
// random number generation
var dataset = []; // Initialize empty array
for (var i = 0; i < 25; i++) {	     //Loop 25 times
  var newNumber = Math.random() * 30;  //New random number (0-30)
  dataset = dataset.concat(newNumber); //Add new number to array
}

d3.select("body").selectAll("div")
  .data(dataset)
  .enter()
  .append("div")
  .attr("class", "bar")
  .style("height", function(d) {
    return d*10 + "px";
   });	
```
# Using SVG
Initially create an SVG element - canvas on which your visuals are rendered: 
http://mkarlovc.github.io/d3dssg/buildingblocks/10.html
```
<svg width="500" height="50"></svg>
```
There are a number of visual elements that you can include between those svg tags:
```
<rect x="0" y="0" width="500" height="50"/>
<circle cx="250" cy="25" r="25"/>
<ellipse cx="250" cy="25" rx="100" ry="25"/>
<line x1="0" y1="0" x2="500" y2="50" stroke="black"/>
<text x="250" y="25">Easy-peasy</text>
```
Layering and Drawing Order depends on initialization of objects

SVG object can be transparent and have bumch of other controlable attributes.
#### Binding data and drawing SVG
http://mkarlovc.github.io/d3dssg/buildingblocks/11.html
```
var dataset = [ 5, 10, 15, 20, 25 ];
//Width and height
var w = 500;
var h = 50;

var svg = d3.select("body")
    .append("svg")
    .attr("width", 500)
    .attr("height", 50);

var circles = svg.selectAll("circle")
    .data(dataset)
    .enter()
    .append("circle");

circles.attr("cx", function(d, i) {return (i * 50) + 25;})
   .attr("cy", h/2)
   .attr("r", function(d) {return d;});
```
#### Changing style
http://mkarlovc.github.io/d3dssg/buildingblocks/12.html
```
var dataset = [ 5, 10, 15, 20, 25 ];
//Width and height
var w = 800;
var h = 200;
    
var svg = d3.select("body")
    .append("svg")
    .attr("width", w)
    .attr("height", h);

var circles = svg.selectAll("circle")
    .data(dataset)
    .enter()
    .append("circle");

circles.attr("cx", function(d, i) {return (i * 50) + 100;})
   .attr("cy", h/2)
   .attr("r", function(d) {return d*2;})
   .attr("fill", "yellow")
   .attr("stroke", "orange")
   .attr("fill-opacity","0.7")
   .attr("stroke-width", function(d) {return d/2;});
```
# Transitions
#### Simple position transition
http://mkarlovc.github.io/d3dssg/buildingblocks/13.html
```
 w = 800;
 h = 400;

var svg = d3.select("body")
    .append("svg")
    .attr("width", w)
    .attr("height", h);

var mySquare = svg.append("rect")
    .attr("x",60)
    .attr("y",60)
    .attr("width",60)
    .attr("height",60);

mySquare.transition()
    .attr("x",320)
    .duration(2000);
```
#### Transition using binded data
http://mkarlovc.github.io/d3dssg/buildingblocks/14.html
```
//Width and height
var w = 900;
var h = 300;
var barPadding = 1;

function sortNumber(a,b) {
return a - b;
}

function rnd_nums(from, to, N) {
var dataset_ = [];
for (var i = 0; i < N; i++) {
var newNumber = from + (Math.random() * to);  
dataset_ = dataset_.concat(newNumber); 
}
dataset_ = dataset_.sort(sortNumber)
return dataset_
}

var from = 5;
var to = 60;
var bars = 25;
dataset = rnd_nums(from,to,bars);

//Create SVG element
var svg = d3.select("body")
  .append("svg")
  .attr("width", w)
  .attr("height", h);

svg.selectAll("rect")
   .data(dataset)
   .enter()
   .append("rect")
   .attr("x", function(d, i) { return i * (w / dataset.length); })
   .attr("y", function(d) { return h - (d * 4); })
   .attr("width", w / dataset.length - barPadding)
   .attr("height", function(d) { return d * 4; })
   .attr("fill", function(d) { return "rgb(0, 138, " + (parseInt((d/60) * 225)) + ")"; });

svg.selectAll("text")
  .data(dataset)
  .enter()
  .append("text")
  .text(function(d) { return parseInt(d);}) 
  .attr("text-anchor", "middle")
  .attr("x", function(d, i) {return i * (w / dataset.length) + (w / dataset.length - barPadding) / 2;})
  .attr("y", function(d) { return h - (d * 4) + 14; })
  .attr("font-family", "sans-serif")
  .attr("font-size", "11px")
  .attr("fill", "white");

setInterval(function(){

  nds = rnd_nums(from,to,bars);

  svg.selectAll("rect")
  .data(nds)
  .transition()
  .attr("x", function(d, i) { return i * (w / dataset.length); })
  .attr("y", function(d) { return h - (d * 4); })
  .attr("width", w / dataset.length - barPadding)
  .attr("height", function(d) { return d * 4; })
  .attr("fill", function(d) { return "rgb(0, 138, " + (parseInt((d/60) * 225)) + ")"; });

  svg.selectAll("text")
  .data(nds)
  .transition()
  .text(function(d) { return parseInt(d);})
  .attr("text-anchor", "middle")
  .attr("x", function(d, i) { return i * (w / dataset.length) + (w / dataset.length - barPadding) / 2; })
  .attr("y", function(d) { return h - (d * 4) + 14; });

},500);
```
# Binding events
#### Binding event on SVG element
http://mkarlovc.github.io/d3dssg/buildingblocks/15.html
```
//Width and height
var w = 900;
var h = 300;
var barPadding = 1;

function rnd_nums(from, to, N) {
  var dataset_ = [];
  for (var i = 0; i < N; i++) {
    var newNumber = from + (Math.random() * to);  
    dataset_ = dataset_.concat(newNumber); 
  }
  return dataset_
}

dataset = rnd_nums(5,60,25);

//Create SVG element
var svg = d3.select("body")
.append("svg")
.attr("width", w)
.attr("height", h);

svg.selectAll("rect")
.data(dataset)
.enter()
.append("rect")
.attr("x", function(d, i) { return i * (w / dataset.length); })
.attr("y", function(d) { return h - (d * 4); })
.attr("width", w / dataset.length - barPadding)
.attr("height", function(d) { return d * 4; })
.attr("fill", function(d) { return "rgb(0, 138, " + (parseInt((d/60) * 225)) + ")"; })
.on('click', function(d,i) {
// handle events here
// d - datum
// i - identifier or index
// this - the `<rect>` that was clicked
nds = rnd_nums(5,60,25);
d3.select(this)
 .transition()
 .duration(300)
 .attr("height",nds[i]*4)
 .attr("y", h - (nds[i] * 4))
 .attr("fill", "rgb(0, 138, " + (parseInt((nds[i]/60) * 225)) + ")");
});

var lbls = svg.selectAll("text")
.data(dataset)
.enter()
.append("text")
.text(function(d) { return parseInt(d);})
.attr("text-anchor", "middle")
.attr("x", function(d, i) { return i * (w / dataset.length) + (w / dataset.length - barPadding) / 2;})
.attr("y", function(d) { return h - (d * 4) + 14; })
.attr("font-family", "sans-serif")
.attr("font-size", "11px")
.attr("fill", "white");
```
# Examples
#### Barchart *(adapted from: https://gist.github.com/mbostock/3885304)*
CODE: https://github.com/mkarlovc/d3dssg/blob/master/examples/exp_1_bar.html

DEMO: http://mkarlovc.github.io/d3dssg/examples/exp_1_bar.html

#### Network *(adapted from http://bl.ocks.org/mbostock/4062045#miserables.json)*
CODE: https://github.com/mkarlovc/d3dssg/blob/master/examples/exp_2_net.html

DEMO: http://mkarlovc.github.io/d3dssg/examples/exp_2_net.html
#### Community evolution
CODE: https://github.com/mkarlovc/d3dssg/blob/master/examples/exp_3_cmty.html

DEMO: http://mkarlovc.github.io/d3dssg/examples/exp_3_cmty.html

# Resources
#### Scott Murray's D3 tutorial http://alignedleft.com/tutorials/d3
Many parts of this tutorial were addapted from the Scott's tutorial
#### Mike Bostock's D3 tutorial http://bost.ocks.org/mike/d3/workshop/#63
Another very nice tutorial in form of presentation
#### Chris Viau's D3 http://christopheviau.com/d3_tutorial/
Tutorial with some nice examples
#### Transitions http://blog.visual.ly/creating-animations-and-transitions-with-d3-js/
Good explanations and illustrations of transitions
#### D3.js examples https://github.com/mbostock/d3/wiki/Gallery
Bunch of inspiring examples made with D3
