# Node.js MySQL 模块性能测试


对比模块：

* [mysql](https://github.com/felixge/node-mysql)
* [mysql2](https://github.com/sidorares/node-mysql2)

**注意**：因为测试时使用的是内存表，建议修改 mysql 配置适当增大内存表大小上限。

```bash
# my.cnf
tmp_table_size = 256M
max_heap_table_size = 256M
```

## 使用

* 配置 MySQL 链接信息

```js
// ./bin/config.js
host: '127.0.0.1',
port: 3306,
user: 'root',
password: '',
database: 'test',
test_table: 'test_table',
```

* 启动测试

```bash
yarn

yarn test
```

* 输出结果

module|init(s)|escapes(ops/s)|inserts(ops/s)|selects(ops/s)
--|--|--|--|--
mysql|0.399|243, 0134|10, 152|270, 270
mysql2|0.167|256, 0819|11, 291|639, 386

可以看到 mysql2 的性能在 select 上是 mysql 的 2 倍多。

* 测试环境

node|MySQL|mysql|mysql2
--|--|--|--
v8.15.0|5.7.22|2.16.0|1.6.5

os: macOS 64 10.14(18A391), 2.3 GHz Intel Core i5, 8 GB 2133 MHz LPDDR3

