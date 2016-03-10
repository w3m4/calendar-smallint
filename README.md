# calendar-smallint
Concise SQL calendar script based on a smallint surrogate primary key

There are two SQL scripts provided currently - one for PostgreSQL and one for SQL Server.  Each script is intended to run in their respective databases to create a Dates table.

The main feature of the Dates dimension table is the use of a smallint as the surrogate primary key.  This reduces the size of fact tables that would normally store date keys as an integers, e.g. 20160308.  Using a 2 byte smallint instead of a 4 byte integer saves twice as much space for every record.

Another feature is the use of negative integers to essentially double the date range:

| DateId | Date       |
| -----: | ---------- |
| -25567 | 1900-01-01 |
| -25566 | 1900-01-02 |
| ...    | ...        |
| -2     | 1969-12-30 |
| -1     | 1969-12-31 |
| 0      | NULL       |
| 1      | 1970-01-01 |
| 2      | 1970-01-02 |
| ...    | ...        |
| 25566  | 2039-12-30 |
| 25567  | 2039-12-31 |


 
