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
  </br>double-quoted string literal.</i></li>
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

# 19.7.2
## Representing Patterns

<ul>
  <li>Regular expressions can include metacharacters
    </br>such as ^, $, and . that specify patters.</li>
  <li>For example, the caret (^) metacharacter matches
    </br>the beginning of a string, while the dollar sign ($)
    </br>matches the end of a string.</li>
  <li>The period (.) metacharacter matches any single
    </br>character.</li>
  <li>Bracket expressions are lists of characters enclosed
    </br>in square brackets ([]) that match any single
    </br>character from the list</li>
  <li>Ranges can be specified by supplying the
    </br>beginning and the end of the range separated by a
    </br>dash (-).</li>
</ul>

## (Cont'd.)

<ul>
  <li>The \b before and after the parentheses indicates
    </br>the beginning and end of a word, respectively&#8212;in
    </br>other words, we're attempting to match whole
    </br>words.</li>
  <li>Quantifiers are used in regular expressions to
    </br>denote how often a particular character or set of
    </br>characters can appear in a match.</li>
</ul>

# Fig. 19.10
## Some regular expression quantifiers.

<table>
  <thead>
    <tr>
      <th>Quantifier</th>
      <th>Matches</th>
    </tr>
  </thead>
  
  <tr>
  <td>{<i>n</i>}</td>
  <td>Exactly <i>n</i> times</td>
  </tr>
  
  <tr>
  <td>{<i>m</i>, <i>n</i>}</td>
  <td>Between <i>m</i> and <i>n</i> times, inclusive</td>
  </tr>
  
  <tr>
  <td>{<i>n</i>,}</td>
  <td><i>n</i> or more times</td>
  </tr>
  
  <tr>
  <td>+</td>
  <td>One or more times (same as {1,})</td>
  </tr>
  
  <tr>
  <td>*</td>
  <td>Zero or more times (same as {0,})</td>
  </tr>
  
  <tr>
  <td>?</td>
  <td>Zero or one time (same as {0, 1})</td>
  </tr>
  </table>

# 19.7.3
## Finding Matches

<ul>
  <li>The optional third argument to function preg
    </br>_match is an array that stores matches to each
    </br>parenthetical statement of the regular expression.</li>
  <li>The first element stores the string matched for the
    </br>entire pattern, and the remaining elements are
    </br>indexed from left to right.</li>
  <li>To find multiple instances of a given patter, we
    </br>must make multiple calls to preg_match, and
    </br>remove matched instances before calling the
    </br>function again by using a function such as
    </br>preg_replace.</li>
</ul>

# 19.7.4
## Character Classes

<ul>
  <li>Character classes are enclosed by the delimiters [:
    </br> and :].</li>
  <li>When this expression is placed in another set of
    </br>brackets, it is a regular expression matching all of
    </br>the characters in the class.</li>
  <li>A bracketed expression containing two or more
    </br>adjacent character classes in the class delimiters
    </br>represents those character sets combined.</li>
</ul>

# Fig. 19.11
## Some regular expression character classes.

<table>
  <thead>
    <tr>
      <th>Character class</th>
      <th>Description</th>
    </tr>
  </thead>
  
  <tr>
  <td>alnum</td>
  <td>Alphanumeric characters(i.e., letters[a-zA-Z] or digits[0-9])</td>
  </tr>
  
  <tr>
  <td>alpha</td>
  <td>Word characters(i.e., letters[a-zA-Z])</td>
  </tr>
  
  <tr>
  <td>digit</td>
  <td>Digits</td>
  </tr>
  
  <tr>
  <td>space</td>
  <td>White space</td>
  </tr>
  
  <tr>
  <td>lower</td>
  <td>Lowercase letters</td>
  </tr>
  
  <tr>
  <td>upper</td>
  <td>Uppercase letters</td>
  </tr>
</table>

# 19.7.5
## Finding Multiple Instances of a Pattern

<ul>
  <li>Function preg_replace takes three
    </br>arguments&#8212;
    <ul>
  <li>the pattern to match</li>
  <li>a string to replace the matched string and</li>
  <li>the string to search. The modified string is
    </br>returned.</li>
  </ul>
  </li>
</ul>

# 19.8
## Form Processing and Business Logic

<ul>
  <li>Superglobal arrays are associative arrays
    </br>predefined by PHP that hold variables acquired
    </br>from user input, the environment or the web server
    </br>and are accessible in any variable scope.</li>
  <li>The <b>arrays</b> $_GET and $_POST retrieve information
    </br>sent to the server by HTTP get and post requests,
    </br>respectively.</li>
</ul>

# Fig. 19.12
## Some useful superglobal arrays.

<table>
  <thead>
    <tr>
      <th>Variable
    </br>name</th>
  <th>Description</th>
  </tr>
  
  <tr>
  <td>$_SERVER</td>
  <td>Data about the currently running server.</td>
  </tr>
  
  <tr>
  <td>$_ENV</td>
  <td>Data about the client's environment.</td>
  </tr>
  
  <tr>
  <td>$_GET</td>
  <td>Data sent to the server by a get request.</td>
  </tr>
  
  <tr>
  <td>$_POST</td>
  <td>Data sent to the server by a post request.</td>
  </tr>
  
  <tr>
  <td>$_COOKIE</td>
  <td>Data contained in cookies on the client's computer.</td>
  </tr>
  
  <tr>
  <td>$GLOBALS</td>
  <td>Array containing all global variables.</td>
  </tr>
</table>

# 19.8.2
## Using PHP to Process HTML5 Forms

<ul>
  <li>Using method="post" appends form data to the
    </br>browser request that contains the protocol and the
    </br>requested resource's URL. Scripts located on the 
    </br>web server's machine can access the form data
    </br>sent as part of the request.</li>
</ul>

# 19.4
## Form Processing and Business Logic (Cont.)

<ul>
  <li>We escape the normal meaning of a character in a
    </br>string by preceding it with the backslash character
    </br>(\).</li>
  <li>Function die <i>terminates</i> script execution. The
    </br>function's optional argument is a string, which is
    </br>printed as the scripts exits</li>
</ul>

# Fig. 19.13
## HTML5 form for gathering user input.

``` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Sample Form</title>
    <style type="text/css">
      label { width: 5em; float: left; }
    </style>
  </head>
  <body>
    <h1>Registration Form</h1>
    <p>Please fill in all fields and click Register.</p>
    
    <!-- post form data to form.php -->
    <form method="post" action="form.php">
      <h2>User Information</h2>
      
      <!-- create four text boxes for user input -->
      <div>
        
      <div><label>First name:</label>
        <input type="text" name="fname"></div>
      <div><label>Last name:</label>
        <input type="text" name="lname"></div>
      <div><label>Email:</label>
        <input type="text" name="email"></div>
      <div><label>Phone:</label>
        <input type="text" name="phone"
               placeholder = "(281) 713-1036"></div>
      </div>
      
      <h2>Publications</h2>
      <p>Which book would you like information about?</p>
      
      <!-- create drop-down list containing book names -->
      <select name = "book">
        <option>Internet and WWW How to Program</option>
        <option>C++ How to Program</option>
        <option>Java How to Program</option>
        <option>Visual Basic How to Program</option>
      </select>
      
      <h2>Operating Systems</h2>
      <p>Which operating system do you use?</p>
      
      <!-- create five radio buttons -->
      <p><input type="radio" name="os" value="windows"
                checked>Windows
        <input type="radio" name="os" value="Mac OS X">Mac OS X
        <input type="radio" name="os" value="Linux">Linux
        <input type="radio" name="os" value="Other">Other</p>
      
      <!-- create a submit button -->
      <p><input type="submit" name="submit" value="Register"></p>
    </form>
  </body>
</html>
```
