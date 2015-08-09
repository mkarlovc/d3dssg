# d3dssg
D3.js teachout at DSSG 2015

# Fundementals
Empty html page referencing css and js
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
http://mkarlovc.github.io/d3dssg/simple_HTML_CSS_JS/style.css
style.css
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
http://mkarlovc.github.io/d3dssg/simple_HTML_CSS_JS/client.js
client.js
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
# Transitions

```

```
