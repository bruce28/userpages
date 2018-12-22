[Golang] sqlite3 Database Example - Basic Usage
###############################################

:date: 2016-01-09T01:28+08:00
:tags: Go, Golang, SQLite, Database
:category: Go
:summary: Use SQLite_ in Go_ program. Write a Golang_ program to initialize a
          database, create a table, write some data to the table and read data
          from the table.
:adsu: yes

Introduction
++++++++++++

This post gives an example of Go_ application which uses SQLite_ SQL database
engine. We will write a Go_ program that opens a database, creates a table in
the database, writes some data to the table, and then reads the data from the
table.

Golang_ provides a generic interface around SQL (or SQL-like) databases [5]_. To
use SQLite_, we need to install the Go SQLite driver first. We will use the
popular `mattn/go-sqlite3`_ driver in our program. Install the driver by:

.. code-block:: bash

  $ go get -u github.com/mattn/go-sqlite3

Source Code
+++++++++++

The following is the source code of Go_ program that uses SQLite_ (version 3):

.. adsu:: 2
.. show_github_file:: siongui userpages content/code/go-sqlite/sqlite3.go
.. adsu:: 3

Now we open database and create a table in our test program. Then write some
data to the table and then read the data from the table.

.. show_github_file:: siongui userpages content/code/go-sqlite/sqlite3_test.go
.. adsu:: 4

Output of Test Code
+++++++++++++++++++

.. code-block:: txt

  === RUN   TestAll
  --- PASS: TestAll (0.76s)
          sqlite3_test.go:19: [{1 A 213} {2 B 214}]
          sqlite3_test.go:28: [{3 D 216} {2 B 214} {1 C 215}]
  PASS


Tested on: ``Ubuntu Linux 15.10``, ``Go 1.5.2``.

----

References:

.. [1] Google Search `go sqlite <https://www.google.com/search?q=go+sqlite>`__

.. [2] Google Search `golang initialize struct array <https://www.google.com/search?q=golang+initialize+struct+array>`__

.. [3] `mattn/go-sqlite3 · GitHub <https://github.com/mattn/go-sqlite3>`_
       |godoc|

.. [4] `SQLDrivers · golang/go Wiki · GitHub <https://github.com/golang/go/wiki/SQLDrivers>`_

.. adsu:: 5

(SQLite)

.. [5] `sql - The Go Programming Language <https://golang.org/pkg/database/sql/>`_

.. [6] `sqlite - INSERT IF NOT EXISTS ELSE UPDATE? - Stack Overflow <http://stackoverflow.com/questions/3634984/insert-if-not-exists-else-update>`_

.. [7] `SQLite "INSERT OR REPLACE INTO" vs. "UPDATE ... WHERE" - Stack Overflow <http://stackoverflow.com/questions/2251699/sqlite-insert-or-replace-into-vs-update-where>`_

.. [8] `How do I check in SQLite whether a table exists? - Stack Overflow <http://stackoverflow.com/questions/1601151/how-do-i-check-in-sqlite-whether-a-table-exists>`_

.. [9] `constraints - insert if not exists statement in sqlite - Stack Overflow <http://stackoverflow.com/questions/19337029/insert-if-not-exists-statement-in-sqlite>`_

.. [10] `php - INSERT or REPLACE is creating duplicates - Stack Overflow <http://stackoverflow.com/questions/6740733/insert-or-replace-is-creating-duplicates>`_

.. [11] `sqlite - How to get INSERT OR IGNORE to work - Stack Overflow <http://stackoverflow.com/questions/12105198/sqlite-how-to-get-insert-or-ignore-to-work>`_

.. [12] `android - SQLiteDatabase insert or replace if changed - Stack Overflow <http://stackoverflow.com/questions/19134274/sqlitedatabase-insert-or-replace-if-changed>`_

.. [13] `sql - SQLite Order By Date - Stack Overflow <http://stackoverflow.com/questions/14091183/sqlite-order-by-date>`_

.. [14] `inserting current date and time in sqlite database - Stack Overflow <http://stackoverflow.com/questions/15473325/inserting-current-date-and-time-in-sqlite-database>`_

.. [15] `ios - SQLite inserting bool value - Stack Overflow <http://stackoverflow.com/questions/7316747/sqlite-inserting-bool-value>`_

.. adsu:: 6

(RSS)

.. [16] `news feed - RSS update single item - Stack Overflow <http://stackoverflow.com/questions/15245896/rss-update-single-item>`_

.. [17] `syndication - RSS Item updates - Stack Overflow <http://stackoverflow.com/questions/164124/rss-item-updates>`_

(News)

.. [18] | `Early preview of a DB driver for SQLite without CGO (ATM Linux/Intel only) : golang <https://www.reddit.com/r/golang/comments/66lo5t/early_preview_of_a_db_driver_for_sqlite_without/>`_
        | `GitHub - cznic/sqlite: Package sqlite is an in-process implementation of a self-contained, serverless, zero-configuration, transactional SQL database engine. (Work In Progress) <https://github.com/cznic/sqlite>`_
.. [19] | `Blog Post: Playing Around with BoltDB : golang <https://www.reddit.com/r/golang/comments/66gm6y/blog_post_playing_around_with_boltdb/>`_
        | `Playing Around with BoltDB - zupzup <https://zupzup.org/boltdb-example/>`_
.. [20] | `Badger – A fast key-value store written natively in Go | Hacker News <https://news.ycombinator.com/item?id=14335931>`_
        | `GitHub - dgraph-io/badger: Fastest key/value store in Go. <https://github.com/dgraph-io/badger>`_

.. [21] `Good approach to interacting with databases? : golang <https://old.reddit.com/r/golang/comments/9i5cpg/good_approach_to_interacting_with_databases/>`_
.. [22] `sqlingo is a SQL DSL & ORM library in Go. It generates code from your database and lets you write SQL queries easily. : golang <https://old.reddit.com/r/golang/comments/9zx2u4/sqlingo_is_a_sql_dsl_orm_library_in_go_it/>`_
.. [23] `Golang SQL Layer on FoundationDB : golang <https://old.reddit.com/r/golang/comments/a11iee/golang_sql_layer_on_foundationdb/>`_
.. [24] | `ObjectBox: new super-fast DB to store for Go objects (structs) : golang <https://old.reddit.com/r/golang/comments/a16m55/objectbox_new_superfast_db_to_store_for_go/>`_
        | `ObjectBox: Fast object-oriented database for Go | Hacker News <https://news.ycombinator.com/item?id=18568029>`_
.. [25] `Sqlx, Dat, Pg. What's the difference and what should I use to connect to a Postgres DB? : golang <https://old.reddit.com/r/golang/comments/a2hiy2/sqlx_dat_pg_whats_the_difference_and_what_should/>`_
.. [26] `cloudfoundry/go-diodes: Diodes are ring buffers manipulated via atomics. : golang <https://old.reddit.com/r/golang/comments/a2yipg/cloudfoundrygodiodes_diodes_are_ring_buffers/>`_
.. [27] `Do you use database in your Go project? : golang <https://old.reddit.com/r/golang/comments/a6yo8k/do_you_use_database_in_your_go_project/>`_
.. [28] `Any decent SQL query builders out there? : golang <https://old.reddit.com/r/golang/comments/a7usrp/any_decent_sql_query_builders_out_there/>`_
.. [29] `Enum and SQL databases : golang <https://old.reddit.com/r/golang/comments/a7vx2w/enum_and_sql_databases/>`_
.. [30] `Database/sql or sqlx: should I use transactions for everything or no? : golang <https://old.reddit.com/r/golang/comments/a85ex4/databasesql_or_sqlx_should_i_use_transactions_for/>`_

.. _Go: https://golang.org/
.. _Golang: https://golang.org/
.. _SQLite: https://www.sqlite.org/
.. _mattn/go-sqlite3: https://github.com/mattn/go-sqlite3

.. |godoc| image:: https://godoc.org/github.com/mattn/go-sqlite3?status.png
   :target: https://godoc.org/github.com/mattn/go-sqlite3
