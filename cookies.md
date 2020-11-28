
# 19.10
## Using cookies

<ul>
  <li>A cookie is a piece of information that's stored by a server in
    </br>a text file on a client's computer to maintain information
    </br>about the client during and between browsing sessions.</li>
  <li><i>A server can access only the cookies that it has placed on the
  </br>client.</i></li>
  <li>Function setcookie takes the name of the cookie to be set
    </br>as the first argument, followed by the value to be stored in
    </br>the cookie.</li>
  <li>The optional third argument indicates the expiration date of
    </br>the cookie.</li>
  <li><i>If no expiration date is specified, the cookie lasts only until
    </br>the end of the current session&#8212;</i>that is, when the user closes
    </br>the browser. This type of cookie is known as a session
    </br>cookie, while one with an expiration date is persistent
    </br>cookie.</li>
</ul>

# 19.10
## (Cont'd.)

<ul>
  <li>If only the name argument is passed to function
    </br>setcookie, the cookie is deleted from the client's
    </br>computer.</li>
  <li>Cookies defined in function setcookie are sent to
    </br>the client at the same time as the information in
    </br>the HTTP header; therefore, setcookie needs to
    </br>be called <i>before</i> any other output</li>
  <li>PHP creates the superglobal array $_COOKIE, which
    </br>contains all the cookie values indexed by their
    </br>names, similar to the values stored in array $_POST
    </br>when an HTML5 form is posted</li>
</ul>

# Fig. 19.17
## Gathering data to be written as a cookie.

``` html
<!DOCTYPE html>

<!-- cookies.html -->
<html>
  <head>
    <meta charset="utf-8">
    <title>Writing a cookie to the client computer</title>
    <style type="text/css">
      label { width: 7em; float: left; }
    </style>
  </head>
  
  <body>
    <h2>Click Write Cookie to save your cookie data.</h2>
    
    <form method="post" action="cookies.php">
      <div><label>Name:</label>
        <input type="text" name="name"></div>
      
      <div><label>Height:</label>
        <input type="text" name="height"></div>
      
      <div><label>Favorite Color:</label>
        <input type="text" name="Color"></div>
      
      <p><input type="submit" value="Write Cookie"></p>
    </form>
  </body>
</html> 
```

# Fig. 19.18
## Writing a cookie to the client.

``` php
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Writing a cookie to the client.</title>
</head>

<body>
   <p>The cookie has been set with the following data:</p>
   
   <!-- print each form field's value -->
   <p>Name: <?php print( $Name ) ?></p>
   <p>Height: <?php print( $Height ) ?></p>
   <p>Favorite Color:
      <span style="color: <?php print( "$Color") ?>;">
      <?php print( "$Color" ) ?></span></p>
   <p>Click <a href="readCookies.php">here</a>
      to read the saved cookie.</p>
</body>
</html>
```
