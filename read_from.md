
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
