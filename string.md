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

# 19.7
## String Processing with Regular Expressions

<ul>
  <li>Text manipulation is usually done with regular expressions&#8212;
  </br>a series of characters that serve as <i>pattern-matching</i>
  </br>templates (or search criteria) in strings, text files and
  </br>databases.</li>
  <li>Function preg_match uses regular expressions to search a
    </br>string for a specified pattern using Perl-compatible regular
    </br>expressions (PCRE)</li>
  <li>If a pattern is found, preg_match returns the length of the
    </br>matched string&#8212;which evaluates to true in a boolean
    </br>context.</li>
  <li><i>Anything enclosed in single quotes in a print statement is
  </br>not interpolated, unless the signle quotes are nested in a
  </br>double-quoted string literal.</li>
  <li>Function preg_match takes two arguments&#8212;a regular&#8211;
  </br>expression pattern to search for and the string to search.</li>
  <li>Function preg_match performs <i>case-insensitive pattern matches.</i></li>
</ul>

# Fig. 19.9
## Regular expressions.

``` php
<!DOCTYPE html>

<!-- Fig. 19.9: expression.php -->
<!-- Regular expressions. -->

<html>
<head>
<meta charset="utf-8">
<title>Regular expressions</title>
<style type="text/css">
   p { margin: 0; }
</style>
</head>

<body>
   <?php
      $search = "Now is the time";
      print( "<p>Test string is '$search'</p>" );
      
      // call preg_match to search for pattern 'Now" in variable search
      if ( preg_match( "/Now/", $search ) )
         print( "<p>'Now' was found.</p>" );
         
      // search for pattern 'Now' in the beginning of the string
      if ( preg_match( "/^Now/", $search ) )
         print( "<p>'Now' found at the beginning of the line.</p>" );
     
     // search for pattern 'Now' at the end of the string
     if ( !preg_match( "/Now$/", $search ) )
        print( "<p>'Now' was not found at the end of the line.</p>" );
        
     // search for any word ending in 'ow'
     if ( preg_match( "/\b([a-zA-Z]*ow)\b/i", $search, $match ) )
        print( "<p>Word found ending in 'ow': " .$match[1]. "</p>" );
     
     // search for any words beginning with 't'
     print( "<p>Words beginning with 't' found: " );
     
     while ( preg_match( "/\b(t[[:alpha:]]+)\b/", $search, $match ) )
     {
        print( $match[1]. " " );
        
        // remove the first occurrence of a word beginning
        // with 't' to find other instances in the string
        $search = preg_replace("/" .$match[ 1 ]. "/", "", $search );
     }
     
     print( "</p>" );
     
     ?> <!-- end PHP script -->
  </body>
</html>
```
