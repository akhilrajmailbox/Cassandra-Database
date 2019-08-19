# Cassandra Database


## Docs Links

[single node configuration]()

[multi node configuration]()

[cql basics]()

[quick guide]()


## Backup and Import scripts

[Import]()

[backup]()



## login

```
cqlsh 192.168.1.253 9042
```

## localhost login

```
cqlsh
```


## check status

```
sudo nodetool status
```

## check status of particular keyspace

```
sudo nodetool status mydb
```

## create keyspace with replication 

```
CREATE KEYSPACE mydb WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : 2 };
```


## check on both server (If it is cluster configurartion)

```
SELECT * FROM system_schema.keyspaces;
```

## to use that keyspace (database)

```
use mydb;
```


## create tables

```
cqlsh> use mydb;
cqlsh:mydb> create table emp (empid int primary key,
... emp_first varchar, emp_last varchar, emp_dept varchar);
cqlsh:mydb>
```

## add another values to that table

```
cqlsh:mydb> insert into emp (empid, emp_first, emp_last, emp_dept)
... values (1,'fred','smith','eng');
cqlsh:mydb>
```

## check from both server

```
cqlsh:mydb> select * from emp;

 empid | emp_dept | emp_first | emp_last
-------+----------+-----------+----------
     1 |      eng |      fred |    smith

(1 rows)
```


```
partitioner: org.apache.cassandra.dht.RandomPartitioner
```

## to check the partioning

```
ubuntu@mydb:~$ nodetool getendpoints
nodetool: getendpoints requires keyspace, table and partition key arguments
See 'nodetool help' or 'nodetool help <command>'.
```



[cassandra import and export](https://github.com/linkbynet/cassandra-migrate-keyspace-from-cluster)