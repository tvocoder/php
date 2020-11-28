# 19.6
## String Comparisons

<ul>
  <li>Many string-processing tasks can be accomplished
  </br>using the equality and relational operators (==, !=,
  </br><, <=, >, and >=).</li>
  <li>Function strcmp compares two strings. The
    </br>function returns -1 if the first string alphabetically
    </br>preceds the second string, 0 if the strings are
    </br>equal, and 1 if the first string alphabetically follows
    </br>the second.</li>
</ul>

# Fig. 19.8
## Using the string-comparison operators.

``` php
<!DOCTYPE html>

<!-- Fig. 19.8: compare.php -->
<!-- Using the string-comparison operators. -->

<html>
   <head>
      <meta charset="utf-8">
      <title>String Comparison</title>
      <style type="text/css">
         p { margin: 0; }
      </style>
   </head>
<body>
   <?php
   // create array fruits
   $fruits = array( "apple", "orange", "banana" );
   
   // iterate through each array element
   for ( $i = 0; $i < count( $fruits ); ++$i )
   {
      // call function strcmp to compare the array element
      // to string "banana"
      if ( strcmp( $fruits[ $i ], "banana" ) < 0 )
         print( "<p>" .$fruits[ $i ]. " is less than banana ");
      elseif ( strcmp( $fruits[ $i ], "banana" ) > 0 )
         print( "<p>" .$fruits[ $i ]. " is greater than banana ");
      else
         print( "<p>" .$fruits[ $i ]. " is equal to banana ");
         
      // use relational operators to compare each element
      // to string "apple"
      
      if ( $fruits[ $i ] < "apple" )
         print( "and less than apple!</p>" );
      elseif ( $fruits[ $i ] > "apple" )
         print( "and greater than apple!</p>");
      elseif ( $fruits[ $i ] == "apple" )
         print( "and equal to apple!</p>" );
      
      ?> <!-- end PHP script -->
   </body>
</html>
```
