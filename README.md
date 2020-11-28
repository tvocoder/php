# 19.5
## Initializing and Manipulating Arrays

<ul>
  <li>PHP provides the capability to store data in arrays. Arrays are
      </br>divided into elements that behave as individual variables.
      </br>Array names, like other variables begin with the $ symbol.</li>
  <li>Individual array elements are accessed by following the
    </br>array's variable name with an index enclosed in the square
    </br>brackets([]).</li>
  <li><i>If a value is assigned to an array element of an array that
    </br>does not exist, then the array is created.</i> Likewise, assigning a
    </br>value to an element where the index is omitted appends a
    </br>new element to the end of the array.</li>
  <li>Function count returns the total number of elements in the
    </br>array.</li>
  <li>Function array creates an array that contains the arguments
    </br>passed to it. The first item in the argument list is stored as
    </br> the first array element(index 0), the second item is stored as 
    </br>the second array element and so on.</li>
</ul>

### (Cont.)

<ul>
  <li>Arrays with nonnumeric indices are called
    </br>associative arrays.</li>
  <li>You can create an associative array using the
    </br>operator =>, where the value to the left of the
    </br>operator is the array index and the value to the
    </br>right is the element's value.</li>
  <li>PHP provides functions for iterating through the
    </br>elements of an array.</li>
  <li>Each array has a built-in interal pointer, which
    </br>points to the array element currently being
    </br>referenced.</li>
  <li>Function reset sets the interal pointer to the first
    </br>array element. Function key returns the index of
    </br>the element currently referenced by the internal
    </br>pointer, and function next moves the internal
    </br>pointer to the next element.</li>
</ul>

# 19.5
## (Cont.)

<ul>
  <li>The foreach statement, designed for
  </br>iterating through arrays, starts with the
  </br>array to iterate through, followed by the
  </br>keyword as, followed by two variables &#8212;the 
  </br>first is assigned the index of the element
  </br>and the second is assigned the value of that
  </br>index's element. (If only one variable is
  </br>listed after as, it is assigned the value of
  </br>the array element.)</li>
</ul>

``` php
<!DOCTYPE html>

<!-- Fig. 19.7: arrays.php -->
<!-- Array manipulation. -->
<html>
<head>
<meta charset="utf-8">
<title>Array manipulation</title>
<style type="text/css">
   p   { margin: 0; }
   .head { margin-top: 10px; font-weight: bold; }
</style>
</head>

<body>
   <?php
   // create array first
   print( "<p class='head'>Creating the first array</p>" );
   $first[ 0 ] = "zero";
   $first[ 1 ] = "one";
   $first[ 2 ] = "two";
   $first[] = "three";
   
   // print each element's index and value
   for ( $i = 0; $i < count( $first ); ++$i )
      print( "Element $i is $first[$i]</p>" );
   
   print( "<p class='head'>Creating the second array</p>" );
   
   // call function array to create array second
   $second = array( "zero", "one", "two", "three" );
   
   for ( $i = 0; $i < count( $second ); ++$i )
      print( "Element $i is $second[$i]</p>" );
      
   print("<p class='head'>Creating the third array</p>" );
   
   // assign values to entries using nonnumeric indices
   $third[ "Amy" ] = 21;
   $third[ "Bob" ] = 18;
   $third[ "Carol" ] = 23;
   
   // iterate through the array elements and print each
   // element's name and value
   for ( reset( $third ); $element = key( $third); next( $third ) )
      print( "<p>$element is $third[ $element ]</p>" );
   
   print( "<p class='head'>Creating the fourth array</p>" );
   
   // call function array to create array fourth using
   // string indices
   $fourth = array(
      "January"   => "first",    "February" => "second",
      "March"     => "third",    "April"    => "fourth",
      "May"       => "fifth",    "June"     => "sixth",
      "July"      => "seventh",  "August"   => "eighth",
      "September" => "ninth",    "October"  => "tenth",
      "November"  => "eleventh", "December" => "twelfth" );
      
   // print each element's name and value
   foreach ( $fourth as $element => value )
      print("<p>$element is the $value month</p>" );
   
   ?> <!-- end PHP script -->
</body>
</html>
```
