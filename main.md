# Objectives
<span>In this chapter you will:</span>
<ul>
  <li>Manipulate data of various types.</li>
  <li>Use operators, arrays and control statements.</li>
  <li>Use regular expressions to search for text that matches a patterns.</li>
  <li>Construct programs that process form data.</li>
  <li>Store data on the client using cookies.</li>
  <li>Create programs that interact with MySQL databases.</li>
</ul>

<div class="introduction">
  <h2>Introduction</h2>
  <ul>
    <li>PHP, or PHP: Hypertext Preprocessor, has
    </br>become the most popular server-side
    </br>scripting language for creating dynamic web
    </br>pages.</li>
    <li>PHP is open source and platform
    </br>independent&#8211;implementations exist for all
    </br>major UNIX, Linux, Mac and Windows
    </br>operating systems. PHP also supports a large
    </br>number of databases.</li>
  </ul>
</div>

<div class="slide" id="6">
  <h2>A Simple PHP Program</h2>
  <ul>
    <li>The power of the web resides not only in servering content to
    </br>users, but also in responding to requests from users and
    </br>generating web pages with dynamic content.</li>
    <li>PHP code is embedded directly into text-based documents,
</br>such as HTML, though these scrip segments are interpreted
</br>by a server <i>before</i> being delivered to the client.</li>
    <li>PHP script file names end with .php.</li>
    <li>In PHP, code is inserted between the scripting delimiters
</br><?php and ?>. PHP code can be placed anywhere in HTML5
</br>markup, as long as the code is enclosed in these delimiters.</li>
  </ul>
</div>

<div class="cont" id="7">
  <h2>(Cont.)</h2>
  <ul>
    <li>Variables are preceded by a $ and are created the first time
    </br>they're encountered.</li>
    <li>PHP statements terminate with a semicolon (;).</li>
    <li>Single&#8211;line comments which begin with two forward slashes
    </br>(//) or a pound sign (#). Text to the right of the delimiter is
    </br>ignored by the interpreter. Multiline comments begin with
    </br>delimiter /* and end with delimiter */.</li>
    <li>When a variable is ecountered inside a double-quoted("")
      </br>string, PHP interpolates the variable. In other words, PHP
      </br>inserts the variable's value where the variable name appears
      </br>in the string.</li>
    <li>All operations requiring PHP interpolation execute on the
      </br>server before the HTML5 document is sent to the client.</li>
    <li>PHP variables are loosely typed&#8211;they can contain different
      </br>types of data at different times.</li>
  </ul>
</div>

<div class="cperror">
  <p>Variable names in PHP are case sensitive. Failure to use
    </br>the proper mixture of cases to refer to a variable will 
    </br>result in a logic error, since the script will create a new
    </br>variable for any name it doesn't recognize as a
    </br>previously used variable.</p>
  </div>
  
``` php
<!DOCTYPE html>

<!-- Fig. 19.1: first.php -->
<!-- Simple PHP program. -->
<html>
<?php
   $name = "Paul"; // declaration and initialization
?> <-- end PHP script -->

   <head>
      <meta charset = "utf-8">
      <title>Simple PHP document</title>
   </head>
   <body>
      <!-- print variable name's value -->
      <h1><?php print( "Welcome to PHP, $name!" ); ?></h1>
   </body>
</html>
```
  
## PHP types.
<table>
  <tr>
    <th>Type</th>
    <th>Description</th>
  </tr>
  
  <tr>
  <td>int, integer</td>
  <td>Whole number(i.e., numbers without a decimal point).</td>
  </tr>
  
  <tr>
  <td>float, double, real</td>
  <td>Real numbers(i.e., numbers containing a decimal point).</td>
  </tr>
  
  <tr>
  <td>string</td>
  <td>Text enclosed in either sing('') or double("") quotes. [<i>Note:</i> Using
    </br>double quotes quotes allows PHP to recognize more escape sequences.]</td>
  </tr>
  
  <tr>
  <td>bool, boolean</td>
  <td>true or false</td>
  </tr>
  
  <tr>
  <td>array</td>
  <td>Group of elements.</td>
  </tr>
  
  <tr>
  <td>object</td>
  <td>Group of associated data and methods.</td>
  </tr>
  
  <tr>
  <td>resource</td>
  <td>An external source &#8212;usually information from a database.</td>
  </tr>
  
  <tr>
  <td>NULL</td>
  <td>No value.</td>
  </tr>
</table>

# 19.3
## Converting Between Data Types

<ul>
  <li>Type conversions can be performed using function
  </br>settype. This function takes two arguments&#8212;a 
  </br>variable whose type is to be changed and the
  </br>variable's new type.</li>
  <li>Variables are typed based on the values assigned
    </br>to them</li>
  <li>Function gettype returns the current type of its
    </br>argument.</li>
  <li>Calling function settype can result in loss of data.
    </br>For example, doubles are truncated when they are converted to integers.</li>
  <li>When converting from a string to a number, PHP
    </br>uses the value of the number that appears at the
    </br>beginning of the string. If no number appears at
    </br>the beginning, the string evaluates to 0</li>
</ul>

## (Cont'd.)

<ul>
  <li>Another option for conversion between types is
  </br>casting (or type casting). Casting does not change
  </br>a variable's content&#8212;it creates a temporary copy of
  </br>a variable's value in memory.</li>
  <li>The concatenation operator(.) combines multiple
    </br>strings.</li>
  <li>A print statement split over multiple lines prints
    </br>all the data that is enclosed in its parentheses.</li>
</ul>

# Fig. 19.3
## Data type conversion.

``` php
<!DOCTYPE html>

<!-- Fig. 19.3: data.php -->
<!-- Data type conversion. -->
<html>
   <head>
      <meta charset = "utf-8">
      <title>Data type conversion</title>
      <style type = "text/css">
         p      { margin: 0; }
         .head  { margine-top: 10px; font-weight: bold; }
         .space { margin-top: 10px; }
      </style>
   </head>
<body>
   <?php
      // declare a string, double and integer
      $testString = "3.5 seconds";
      $testDouble = 79.2;
      $testInteger = 12;
   ?> <!-- end PHP script -->
   
   <!-- print each variable's value and type -->
   <p class = "head">Original values:</p>
   <?php
      print("<p>$testString is a(n) " .gettype($testString)."</p>");
      print("<p>$testDouble is a(n) " .gettype($testDouble). "</p>");
      print("<p>$testInteger is a(n) " .gettype($testInteger). "</p>");
   ?> <!-- end PHP script -->
   
   <p class = "head">Converting to other data types:</p>
   <?php
      // call function settype to convert variable
      // testString to different data types
      print("<p>$testString ");
      settype($testString, "double");
      print(" as a double is $testString</p>");
      print("<p>$testString ");
      settype($testString, "integer");
      print(" as an integer is $testString</p>);
      settype($testString, "string");
      print("<p class = 'space'>Converting back to a string results in
         $testString</p>);
   
   // use type casting to cast variables to a different type
   $data = "98.6";
   print("<p class = 'space'>Before casting: $data is a " .gettype($data). "</p>");
   print("<p class = 'space'>Using type casting instead:</p>
      <p>as a double: " .(double) $data. "</p>" . "<p>as an integer: " .(integer) $data. "</p>";
   print("<p class = 'space'>After casting: $data is a " .gettype($data). "</p>");
   
   ?> <!-- end PHP script -->
 </body>
</html>
   
```
