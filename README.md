
# Hive Usage

## Table of Contents
1. [Access Hive CLI](#1-access-hive-command-line-interface)
2. [Use Hive CLI](#2-use-hive-cli)  
   2.1 [Create schema](#21-create-schema)  
   2.2 [Insert and Query data](#22-insert-and-query-data) 
---

## 1. Access Hive CLI
Change user
```bash
sudo -i
su - hadoop
```

พิมพ์ command ดังนี้ เพื่อเข้า prompt
```bash
hive
```

## 2. Use Hive CLI
## 2.1 Create Schema
### Show databases
```bash
hive> show databases;


# [Example] The result should be

# OK
# default
# mydb
# Time taken: 2.214 seconds, Fetched: 2 row(s)
```

### Create Databases
```bash
hive> CREATE DATABASE mydb;
```

### Select Databases
```bash
hive> use mydb;
```

### Create Table
```bash
hive>
CREATE external TABLE employee (
    name string,
    age int,
    id int
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '|';
```

### Show tables
```bash
hive> show tables;
```

### Check hdfs
- Path ของ data table ควรถูกเก็บไว้ที่ hdfs ที่ /user/hive/warehouse  
- โดย database จะถูกเก็บโดย /user/hive/warehouse/<db_name>.db  
- table จะถูกเก็บโดย /user/hive/warehouse/<db_name>/<table_name>  

สามารถตรวจสอบได้โดยคำสั่งด้านล่าง
```bash
hadoop fs -ls /user/hive/warehouse

# The result should be
# drwxr-xr-x - hadoop supergroup 0 2019-10-30 15:11 /user/hive/warehouse/mydb.db

hadoop fs -ls /user/hive/warehouse/mydb.db

# The result should be
# drwxr-xr-x - hadoop supergroup 0 2019-10-30 19:59 /user/hive/warehouse/mydb.db/employee
```

## 2.2 Insert and Query data
### How to put data
a.) Use INSERT statement  
b.) Use LOAD statement

### Select database
```bash
hive> use mydb;
```

### Insert data directly
```bash
hive> insert into employee values('Test', 32 ,2);
```

### load data
```bash
hive> LOAD DATA LOCAL INPATH '/home/hadoop/hive/examples/files/emp.txt' INTO TABLE employee;
```

### Query
```bash
hive> SELECT * from employee;
```
