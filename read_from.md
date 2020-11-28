
# 19.9
## Reading from a Database

<ul>
  <li>Function mysql_connect connects the MySQL
    </br>database. It takes three arguments&#8212;
    <ul>
      <li>the server's hostname</li>
      <li>a username</li>
      <li>a password</li>
    </ul>
    <div><p>and returns a database handle&#8212;a representation of
          </br>PHP's connection to the database, or false if the
          </br>connection fails.</p></div>
  <li>Function mysql_select_db selects and opens the
    </br>database to be queried.</li>
  <li>The function returns true on success or false on
    </br>failure.</li>
</ul>

# 19.9
## (Cont'd.)

<ul>
  <li>To query the database, we call function mysql_query,
    </br>specifying the query string and the database to query.</li>
  <li>This returns a resource containing the result of the query, or
    </br>false if the query fails.</li>
  <li>It can also execute SQL statements such as INSERT or DELETE
    </br>that do not return results.</li>
  <li>The mysql_error function returns any error strings from the
    </br>database.</li>
  <li>mysql_close closes the connection to the database specified
    </br>in its argument</li>
  <li>The mysql_fetch_row function returns an array containing
    </br>the values for each column in the current row of the query
    </br>result ($result).</li>
</ul>

# Fig. 19.15
## Form to query a MySQL database.
``` html
<!DOCTYPE html>

<html>
  <head>
    <meta charset="utf-8">
    <title>Sample Database Query</title>
  </head>
  <body>
    <h1>Querying a MySQL database.</h1>
    <form method="post" action="database.php">
      <p>Select a fied to display:
        <!-- add a select box containing options -->
        <!-- for SELECT query -->
        <select name="select">
          <option selected>*</option>
          <option>ID</option>
          <option>Title</option>
          <option>Category</option>
          <option>ISBN</option>
        </select></p>
      
      <p><input type="submit" value="Send Query"></p>
    </form>
  </body>
</html>
```

# Fig. 19.16
## Querying a database and displaying the results.

``` php
<!DOCTYPE html>

<!-- database.php -->
<html>
<head>
<meta charset="utf-8">
<title>Search Results</title>

<style type="text/css">
   body   { font-family: sans-serif;
            background-color: lightyellow; }
   table  { background-color: lightblue;
            border-collapse: collapse;
            border: 1px solid gray; }
   td   { padding: 5px; }
   tr:nth-child(odd) {
      background-color: white; }
</style>
</head>

<body>
   <?php
      $select = $_POST[ "select" ]; // creates variable $select
      
      // build SELECT query
      $query = "SELECT " .$select. " FROM books";
      
      // connect to MySQL
      if ( !( $database = mysql_connect( "localhost", "iw3htp", "password" ) ) )
         die( "Could not connect to database </body></html>" );
      
      // open Products database
      if ( !mysql_select_db( "products", $database ) )
         die( "Could not open products database </body></html>" );
         
      // query Products database
      if( !( $result = mysql_query( $query, $database ) ) )
      {
         print( "<p>Could not execute query!</p>" );
         die( mysql_error(). "</body></html>" );
      } // end if
      
      mysql_close( $database );
   ?> <!-- end PHP script -->
   
   <table>
      <caption>Results of "SELECT <?php print( "$select" ) ?>
         FROM books"</caption>
         
         <?php
         // fetch each record in result set
            while ( $row = mysql_fetch_row( $result ) )
            {
               // build table to display results
               print( "<tr>" );
            
               foreach ( $row as $key => $value )
                  print( "<td>$value</td>" );
               
               print( "</tr>" );
            } // end while
         ?> <!-- end PHP script -->
   </table>
   
   <p>Your search yielded
      <?php print( mysql_num_rows( $result ) ) ?> results.</p>
   <p>Please email comments to <a href="mailto:deitel@deitel.com">
         Deitel and Associates, Inc.</a></p>
</body>
</html>
```
