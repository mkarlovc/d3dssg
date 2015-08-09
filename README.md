# D3.js teachout at DSSG 2015

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
```<body>
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
    
# Transitions

```

```
