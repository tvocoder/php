
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
