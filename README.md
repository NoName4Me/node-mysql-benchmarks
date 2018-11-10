Benchmarks for MySQL modules for Node.js
=========================================

Clone the git repository and run:

    npm install

Then run:

    npm test


You will also need to make sure that `max_heap_table_size=4294967295` is set in your server configuration.

When using Node <=8 mariasql will be tested.

To test C client run:

    BENCH_C=1 npm test

Default MySQL Config
--------------------

    host: 127.0.0.1
    port: 3306
    user: root
    pass: ""

Supported MySQL modules
-----------------------

* [mariasql](https://github.com/mscdex/node-mariasql)
* [mysql](https://github.com/felixge/node-mysql)
* [mysql2](https://github.com/sidorares/node-mysql2)


Benchmark results (2018-11-10)
------------------------------

Full write up @ [Node.js MySQL Driver Benchmarks 2018](https://medium.com/epycly/node-js-mysql-driver-benchmarks-2018-86579c402016)

All benchmarks were conducted on a Gigabyte Aero 15x with an Intel i7-8750H CPU @ 2.20GHz (turbo disabled)
running Ubuntu 18.04 Linux version 4.15.0-38-generic (buildd@lcy01-amd64-023) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)).

## Node v6.14.4
Results (init time in seconds, other values in ops/s):
module,init,escapes,inserts,selects
mysql,0.1,1310616,10162,139587
mysql2,0.05,1324796,10572,453721
mariasql,0.016,3267974,14377,369276
C,0.021,14043924,20837,1095740

## Node v8.12.0
Results (init time in seconds, other values in ops/s):
module,init,escapes,inserts,selects
mysql,0.082,1664817,10416,289519
mysql2,0.029,1630878,11370,625782
mariasql,0.024,3086420,14977,406504
C,0.016,14474160,20985,1052153

## Node v.10.13.0
Results (init time in seconds, other values in ops/s):
module,init,escapes,inserts,selects
mysql,0.086,1805597,10580,291545
mysql2,0.04,1858736,13113,871080
mariasql,0.016,2862595,15343,412201
C,0.029,14099476,20596,1094857
