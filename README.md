# SQLSRV DataBase Class
### Version
0.2.0

### About
This PHP class is a tool for interacting with Microsoft SQL (MSSQL) databases using the SQLSRV feature, as `mssql_*` functions in PHP it self are deprecated alongside `mysql_*`.

It is inspired by the [`WPDB` class from WordPress][WPDB]

### Features

One of the primary concerns when working with MSSQL databases is how pickey they are with data values, I've tried to work around this with the support for database schemas built into the class.

For example, imagine that `column` in the example below is set to the type `smallint`, you can't run the following query:
```
UPDATE table SET column = '3'
```

The SQL server will throw a warning that the query is invalid because you can't use quotes around numeric values like you can in MySQL

The example from before, ran through the class:
```
SQLSRV::update(
    'table',
    array(
        'column' => 3
    )
);
```

This will run the `SQLSRV::update()` function on `table` and set `column` to the desired value after checking it with `SQLSRV::schema_prepare_value()`


### Functionality

The most important public features are ported in and self-documented:

- [`SQLSRV::insert()`][SQLSRV::insert]
- [`SQLSRV::update()`][SQLSRV::update]
- [`SQLSRV::delete()`][SQLSRV::delete]
- [`SQLSRV::get_row()`][SQLSRV::get_row]
- [`SQLSRV::get_results()`][SQLSRV::get_results]
- [`SQLSRV::last_insert_id()`][SQLSRV::last_insert_id]
- [`SQLSRV::has_error()`][SQLSRV::has_error]

License
----

GPLv2

[WPDB]: <http://codex.wordpress.org/wpdb>
[SQLSRV::insert]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L453>
[SQLSRV::update]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L366>
[SQLSRV::delete]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L416>
[SQLSRV::get_row]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L490>
[SQLSRV::get_results]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L518>
[SQLSRV::last_insert_id]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L549>
[SQLSRV::has_error]: <https://github.com/Clorith/SQLSRV-DataBase-Class/blob/master/db.php#L625>
