# CTLR Sqlite

_Cheap Tricks Library for RingoJS - Sqlite package_

## Usage

    var sqlite = require("ctlr-sqlite");
    sqlite.connect("/path/to/file.sqlite");
    
    var one_value = sqlite.get_one("select id from table limit 0,1");
    var rows = sqlite.get_all("select * from table");

    var id = sqlite.prepared_query("insert into ? (?,?) values(?,?)", ["table", "name", "email", "User", "user@example.org"]);

### API

<table><tbody>
<tr><td valign="top"><b>connect</b></td>
    <td>(file_name)
        <br>Connects to the Sqlite database stored in the file. Returns a <a href="http://download.oracle.com/javase/6/docs/api/java/sql/Connection.html">Connection</a> object.</td></tr>
<tr><td valign="top"><b>close</b></td>
    <td>([Connection])
        <br>Close a connection to a database (provided by <tt>Connection</tt> or the last opened Connection).</td></tr>
<tr><td valign="top"><b>getConnection</b></td>
    <td>([Connection])
        <br>Returns the last opened Connection or the provided Connection.</td></tr>
<tr><td valign="top"><b>query</b></td>
    <td>(sql, [Connection])
        <br>Runs the <tt>sql</tt> query and returns a <a href="http://download.oracle.com/javase/6/docs/api/java/sql/ResultSet.html">ResultSet</a>/affected-rows-count/last-insert-id on success.</td></tr>
<tr><td valign="top"><b>prepared_query</b></td>
    <td>(sql, parameters, [Connection])
        <br>Runs the <tt>sql</tt> query with provided <tt>parameters</tt> Array and retuns a ResultSet/affected-rows-count/last-insert-id on success.</td></tr>
<tr><td valign="top"><b>get_row</b></td>
    <td>(sql/ResultSet)
        <br>Retrieves one row from the given <tt>ResultSet</tt> or a ResultSet built with the given <tt>sql</tt> query.</td></tr>
<tr><td valign="top"><b>get_all</b></td>
    <td>(sql/ResultSet)
        <br>Retrieves an Array of all rows from the given <tt>ResultSet</tt> or a ResultSet built with the given <tt>sql</tt> query.</td></tr>
<tr><td valign="top"><b>get_iterator</b></td>
    <td>(sql/ResultSet)
        <br>Returns a <em>generator</em> on all rows from the given <tt>ResultSet</tt> or a ResultSet built with the given <tt>sql</tt> query.
        <br><em>Note: due to Sqlite recommendation to close all resultsets ASAP for better performance this is just a wrapper around <em>get_all()</em>.</td></tr>
<tr><td valign="top"><b>get_col</b></td>
    <td>(sql/ResultSet, [column=1])
        <br>Retrieves an Array of all values in one column from the given <tt>ResultSet</tt> or a ResultSet built with the given <tt>sql</tt> query.</td></tr>
<tr><td valign="top"><b>get_one</b></td>
    <td>(sql/ResultSet)
        <br>Restrieves the first value in the first row from the given <tt>ResultSet</tt> or a ResultSet build with the given <tt>sql</tt> query.</td></tr>
</tbody></table>

## Requirements

- RingoJS v0.8

## License

This is free software, and you are welcome to redistribute it under certain conditions; see LICENSE.txt for details.

## Credits

- John Lim for his <a href="http://adodb.sourceforge.net/">ADOdb Database Abstraction Library for PHP</a> (an inspiration for this package).
- David Crawshaw for <a href="http://www.zentus.com/sqlitejdbc/">SQLite JDBC Driver</a>.

## Contact

Emilis Dambauskas <emilis.d@gmail.com>, <http://emilis.github.com/>
