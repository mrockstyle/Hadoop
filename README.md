
# Example of Insert data and Query in Hadoop


### 1. Change user
```bash
sudo -i
su - hadoop
```

### 2. Use HIVE command line interface
```bash
cd /home/hadoop
hive

# ***IMPORTANT***
# เรียก hive ที่ /home/hadoop เท่านั้น
```

### 3. Show databases
```bash
hive> show databases;


# The Result should be

# OK
# default
# mydb
# Time taken: 2.214 seconds, Fetched: 2 row(s)
```

### 4. Select Databases
```bash
hive> use mydb;
```

### 5. Show tables
```bash
hive> show tables;
```

### 6. Insert data
### 6.1 Insert data directly
```bash
hive> insert into student values(1, 'myName');
```

### 6.2 load data
```bash
hive> LOAD DATA LOCAL INPATH '/home/hadoop/hive/examples/files/emp.txt' INTO TABLE employee;
```

### 7. Query
```bash
hive> SELECT * from student;
hive> SELECT * from employee;
```




