# DatabaseConnector 2.7.0

DatabaseConnector is a handy PHP wrapper class to allow easy access to database connections to different database types without changing of usage, queries etc..

The class uses the PHP _PDO_ functionality and is able to connect to each database type, that's driver is installed/activated in the PHP configuration and also to use transactions and prepared statements.

## Documentation

Visit https://www.simatex.de/documentation/databaseconnector for detailed information.

## Example

    // Include class to project
    require_once 'DatabaseConnector/DatabaseConnector.php';
    
    // Create DatabaseConnector object
    $DB = new DatabaseConnector();
    
    // Connect to an existing MySql database
	$DB->ConnectMysql ('localhost', 'user01', 'passwd02', 'database03');
	
	// Select data from table in database
	if ( $DB->IsConnected() )
	{
		$Result = $DB->SqlGetLines ('SELECT * FROM table01 WHERE id IN (1, 2, 3)');
		
		foreach ( $Result AS $Row )
		{
			echo 'Username: ' . $Row['username'] . '<br>';
		}
	}


## History

**Version 2.7.0 - 2023-03-31**
* Added Method SqlExecutePrepared() to execute prepared Statements

**Version 2.6.1 - 2023-03-10**
* Minor error correction

**Version 2.6.0 - 2016-10-14**
* Outputting an error message in SqlExecute(), if no database connection exists
* Checking write protection when using SQLite database files
* Avoiding multideclarations of the DatabaseConnector class
* Several smaller code adjustments

**Version 2.5.0 - 2014-07-29**
* Minor corrections in the internal call of IsConnected()
* Adding a new (optional) $FetchMode parameter in SqlPrepareStatement()
* SqlGetPreparedLines() and SqlGetPreparedLinesAsObject() can accept arrays instead of single method parameters now
* Adding SqlPrepareBindParam() and SqlPrepareBindValue() to bind variables or values to prepared statements

**Version 2.4.0 - 2014-03-09**
* Adding the possibility to use prepared statements
* Adding an optional timeout parameter to the conntection methods
* Adding the method SqlHasResult() to check, if an SQL statement _would_ return a result (without returning the result data)
* All query methods are returning _NULL_ now, if there was no result to return
* Correction of an access error in TransactionRollback()
* Correction of SqlGetLinesAsObject(), because empty results returned _FALSE_ instead of _NULL_
* Entfernen von falsch gesetzten ExecutionTimern für die Abfragedauer-Messung

**Version 2.3.0 - 2013-08-13**
* Error correction in GetAvailableDrivers() to allow a query of all available database drivers even if no database connection exists
* Error correction in the `<div>`-Tag which is printed with an active _PrintSql_ configuration. CSS formatting can be done with _class_ instead of _id_ now.
* New method SqlGetExecutionTime() to return the execution time of the last statement in milliseconds

**Version 2.2.1 - 2013-07-25**
* Error correction in SqlGetFirstLineAsObject() and SqlGetNextLineAsObject(), to allow the methods to return with _NULL_ instead of stopping execution with an error

**Version 2.2.0 - 2013-07-24**
* Changing the return type of SqlGetLines() from _PDOObject_ to an _array_ to allow a more comfortable access to the result (backward compatible up to version 2.0.0)
* New Method SqlGetLinesAsObject(), SqlGetFirstLineAsObject() and SqlGetNextLineAsObject() to allow a return of dynamically generated PHP objects (with columns as attributes) instead of arrays

**Version 2.1.0 - 2013-07-14**
* Removing direct accesses to result arrays when methods are called, to guarantee compatibility to different PHP versions

**Version 2.0.0 - 2013-02-19**
* Complete code conversion to PDO, to allow working with different types of database (MySql, SQLite, Postgresql etc.)

**Version 1.2.0 - 2011-08-26**
* New method getDBInfo() to get database information as string

**Version 1.1.0 - 2009-02-04**
* New method printDBInfo() to return database information

**Version 1.0.0 - 2009-02-03**
* Initial version
