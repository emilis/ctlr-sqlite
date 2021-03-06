# CTLR-Sqlite

Sqlite driver for RingoJS with API similar to ADOdb for PHP.

## Usage

### Example

```javascript
var sqlite = require("ctlr-sqlite");
sqlite.connect("/path/to/file.sqlite");

var one_value = sqlite.get_one("select id from table limit 0,1");
var rows = sqlite.get_all("select * from table");

var id = sqlite.prepared_query("insert into ? (?,?) values(?,?)", ["table", "name", "email", "User", "user@example.org"]);
```

### API summary

<table><tbody>
<tr><td align="right"><a href="http://download.oracle.com/javase/6/docs/api/java/sql/Connection.html">Connection</a></td>
    <td><b>connect</b>( file_name )</td>
    <td>Connects to the database stored in the file.</td></tr>
<tr><td align="right">void</td>
    <td><b>close</b>( [Connection] )</td>
    <td>Close a connection to a database.</td></tr>
<tr><td align="right">Connection</td>
    <td><b>getConnection</b>( [Connection] )</td>
    <td>Returns the last opened Connection or the provided Connection.</td></tr>
<tr><td align="right"><a href="http://download.oracle.com/javase/6/docs/api/java/sql/ResultSet.html">ResultSet</a> / number</td>
    <td><b>query</b>( sql, [Connection] )</td>
    <td>Executes the sql query.</td></tr>
<tr><td align="right">ResultSet / number</td>
    <td><b>prepared_query</b>( sql, parameters[], [Connection] )</td>
    <td>Executes the sql query with provided parameters.</td></tr>
<tr><td align="right">Object</td>
    <td><b>get_row</b>( sql/ResultSet )</td>
    <td>Retrieves one row.</td></tr>
<tr><td align="right">Array</td>
    <td><b>get_all</b>( sql/ResultSet )</td>
    <td>Retrieves all rows.</td></tr>
<tr><td align="right"><a href="https://developer.mozilla.org/en/JavaScript/Guide/Iterators_and_Generators">Iterator</a></td>
    <td><b>get_iterator</b>( sql/ResultSet )</td>
    <td>Returns an Iterator on all rows in result.
        <br><em>Note: due to Sqlite recommendation to close all resultsets ASAP for better performance this is just a wrapper around <em>get_all()</em>.</td></tr>
<tr><td align="right">Array</td>
    <td><b>get_col</b>( sql/ResultSet, [column=1] )</td>
    <td>Retrieves all values of one column.</td></tr>
<tr><td align="right">mixed</td>
    <td><b>get_one</b>( sql/ResultSet )</td>
    <td>Retrieves the first column value from the first row.</td></tr>
</tbody></table>

### Requirements

- [RingoJS](http://ringojs.org/) v0.8

## About

### License

This is free software, and you are welcome to redistribute it under certain conditions; see LICENSE.txt for details.

### Thanks 

- John Lim for his <a href="http://adodb.sourceforge.net/">ADOdb Database Abstraction Library for PHP</a> (an inspiration for this package).
- David Crawshaw for <a href="http://www.zentus.com/sqlitejdbc/">SQLite JDBC Driver</a>.

### Author contact

Emilis Dambauskas <emilis.d@gmail.com>, <http://emilis.github.com/>
