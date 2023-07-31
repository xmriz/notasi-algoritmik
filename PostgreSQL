# PostgreSQL CheatSheet

## Materi PBD

### Postgre Command
- `\l` : List all databases
- `\df` : List all functions
- `dv` : List all views
- `\dt` : List all tables


### Import/Export Database
#### Import
- buat database terlebih dahulu
- pastikan file sql berada di direktori yang sama dengan terminal
```bash
psql -U {username} -d {database_name} < {external_file_name}.sql
```
#### Export
- pastikan file sql berada di direktori yang sama dengan terminal
```bash
pg_dump -U {username} -d {database_name} > {external_file_name}.sql
```
#### Menyalin Database
```bash
CREATE DATABASE <new_database_name> WITH TEMPLATE <old_database_name>;
```


### Manage Database
- Connect Database
```bash
\c <database_name>
```
- Create Database
```bash
CREATE DATABASE [IF NOT EXISTS] <database_name>;
```
- Drop Database
```bash
DROP DATABASE [IF EXISTS] <database_name>;
```
- Rename Database
```bash
ALTER DATABASE <old_database_name> RENAME TO <new_database_name>;
```

### Manage Table
- Create Table
```bash
CREATE TABLE <table_name> (
    <column_name> <data_type> [<constraint>],
    <column_name> <data_type> [<constraint>],
    ...
);
```
  - data_type : 
    - `serial` : auto increment integer
    - `varchar(n)` : string with max length n
    - `text` : string with unlimited length
    - `int` : integer
    - `float` : float
    - `boolean` : boolean
    - `date` : date
    - `time` : time
    - `timestamp` : timestamp
  - constraint :
    - `PRIMARY KEY` : primary key
    - `UNIQUE` : unique value
    - `NOT NULL` : not null value
    - `DEFAULT <value>` : default value

- Drop Table
```bash
DROP TABLE [IF EXISTS] <table_name>;
```

- Rename Table
```bash
ALTER TABLE <old_table_name> RENAME TO <new_table_name>;
```

### Manage Column

- Add Column
```bash
ALTER TABLE <table_name> ADD COLUMN <column_name> <data_type> [<constraint>];
```

- Drop Column
```bash
ALTER TABLE <table_name> DROP COLUMN <column_name>;
```

- Rename Column
```bash
ALTER TABLE <table_name> RENAME COLUMN <old_column_name> TO <new_column_name>;
```

- Modify Column
```bash
ALTER TABLE <table_name> ALTER COLUMN <column_name> TYPE <data_type> [<constraint>];
```

- SET/DROP DEFAULT
```bash
ALTER TABLE <table_name> ALTER COLUMN <column_name> [SET DEFAULT <value> | DROP DEFAULT];
```

- INSERT INTO
```bash
INSERT INTO <table_name> (<column_name>, ...) VALUES (<value1>, ...), (<value2>, ...), ...;
``` 

### Manage Data


- UPDATE
```bash
UPDATE <table_name>
SET <column_1> = <value_1>, <column_2> = <value_2>
WHERE <column_1> = <value> AND <column_2> = <value>;
```

- DELETE ALL
```bash
DELETE FROM <table_name>;
```

- DELETE SPECIFIC
```bash
DELETE FROM <table_name> 
WHERE <column_name> = <value>;
```

#### Data Query

- SELECT LIMIT
```bash
SELECT * FROM <table_name> LIMIT <number>;
```

- SELECT UNIQUE
```bash
SELECT DISTINCT <column_name> FROM <table_name>;
```

- JOIN
```bash
-- JOIN 
SELECT <column_name> 
FROM <table_name_1> [INNER | LEFT | OUTER] JOIN <table_name_2> ON <table_name_1>.<column_name> = <table_name_2>.<column_name>;

-- NATURAL JOIN
SELECT <column_name>
FROM <table_name_1> NATURAL JOIN <table_name_2>;

-- CROSS JOIN
SELECT <column_name>
FROM <table_name_1> CROSS JOIN <table_name_2>;
```

- UNION
note : column name must be same, and result will be unique
```bash
SELECT <column_name> FROM <table_name_1>
UNION
SELECT <column_name> FROM <table_name_2>;
```

- INTERSECT
note : column name must be same, and result will be unique
```bash
SELECT <column_name> FROM <table_name_1>
INTERSECT
SELECT <column_name> FROM <table_name_2>;
```

- EXCEPT
note : column name must be same, and result will be unique
```bash
SELECT <column_name> FROM <table_name_1>
EXCEPT
SELECT <column_name> FROM <table_name_2>;
```

- CONCAT
```bash
SELECT CONCAT(<column_name_1>, <column_name_2>) FROM <table_name>;
```

- INTERVAL
```bash
-- Menghitung selisih waktu antara dua tanggal
SELECT '2023-07-30'::DATE - '2023-07-15'::DATE AS selisih_hari;

-- Menambahkan waktu ke tanggal
SELECT '2023-07-30'::DATE + INTERVAL '3 days' AS tanggal_setelah_3_hari;

-- Mengurangi waktu dari tanggal
SELECT '2023-07-30'::DATE - INTERVAL '1 month' AS tanggal_sebulan_sebelumnya;

-- Operasi matematika pada INTERVAL
SELECT INTERVAL '2 hours' * 3 AS total_jam;
```

- EXTRACT
```bash
-- Mengambil bagian dari tanggal
SELECT EXTRACT(YEAR FROM '2023-07-30'::DATE) AS tahun;
SELECT EXTRACT(MONTH FROM '2023-07-30'::DATE) AS bulan;
SELECT EXTRACT(DAY FROM '2023-07-30'::DATE) AS hari;

-- Mengambil bagian dari waktu
SELECT EXTRACT(HOUR FROM '2023-07-30 09:00:00'::TIMESTAMP) AS jam;
SELECT EXTRACT(MINUTE FROM '2023-07-30 09:30:00'::TIMESTAMP) AS menit;
SELECT EXTRACT(SECOND FROM '2023-07-30 09:30:30'::TIMESTAMP) AS detik;
```

- LIKE/ILIKE
  * `%` : any character
  * `_` : single character
  * LIKE : case sensitive
  * ILIKE : case insensitive
```bash
SELECT <column_name> 
FROM <table_name> 
WHERE <column_name> LIKE '%<value>%';
```

- IN
```bash
SELECT <column_name>
FROM <table_name>
WHERE <column_name> IN (<value_1>, <value_2>, ...);
```

- BETWEEN
```bash
SELECT <column_name>
FROM <table_name>
WHERE <column_name> BETWEEN <value_1> AND <value_2>;
```

- GROUP BY
  * GROUP BY, biasanya digunakan untuk mengelompokkan data berdasarkan nilai tertentu, dan digunakan bersamaan dengan fungsi agregasi seperti COUNT, SUM, AVG, MAX, MIN, dll.
  * <column_name> pada SELECT harus muncul di GROUP BY [atau di fungsi agregasi].
  * <column_name> pada GROUP BY tidak harus muncul di SELECT.
  * <column_name> pada fungsi agregasi tidak harus muncul di SELECT atau GROUP BY.
```bash
SELECT <column_name>, COUNT(<column_name>) AS total
FROM <table_name>
GROUP BY <column_name>;
```

- HAVING
  * HAVING, biasanya digunakan untuk melakukan filter terhadap hasil GROUP BY.
```bash
SELECT <column_name>, COUNT(<column_name>) AS total
FROM <table_name>
GROUP BY <column_name>
HAVING COUNT(<column_name>) > 1;
```

- ORDER BY
```bash
SELECT <column_name>
FROM <table_name>
GROUP BY <column_name>
HAVING COUNT(<column_name>) > 1
ORDER BY <column_name> [ASC | DESC], ...;
```

- CASE WHEN
```bash
SELECT <column_name>,
CASE
  WHEN <column_name> = <value_1> THEN <value_2>
  WHEN <column_name> = <value_3> THEN <value_4>
  ELSE <value_5>
END AS <new_column_name>
FROM <table_name>;
```

- AS
```bash
SELECT <column_name> AS <new_column_name>
FROM <table_name> AS t
WHERE t.<column_name> = <value>;
```

- AGGREGATE FUNCTION
  * COUNT : menghitung jumlah baris
  * SUM : menjumlahkan nilai
  * AVG : menghitung rata-rata
  * MAX : mencari nilai maksimum
  * MIN : mencari nilai minimum
```bash
SELECT COUNT(<column_name>) AS total
FROM <table_name>;
```

- SUBQUERY
```bash
SELECT <column_name>
FROM <table_name>
WHERE <column_name> IN (
  SELECT <column_name>
  FROM <table_name>
  WHERE <column_name> = <value>
);
```

- IS/IS NOT
```bash
SELECT <column_name>
FROM <table_name>
WHERE <column_name> IS NULL;
```

### Manage View

- CREATE VIEW
```bash
CREATE VIEW <view_name> AS
SELECT <column_name> FROM <table_name>;
```

- CREATE MATERIALIZE VIEW
```bash
CREATE MATERIALIZED VIEW <view_name> AS
SELECT <column_name> FROM <table_name>;
```

- DROP VIEW
```bash
DROP VIEW [IF EXISTS] <view_name>;
```

- UPDATE VIEW
```bash
UPDATE <view_name>
SET <column_1> = <value_1>, <column_2> = <value_2>
WHERE <column_1> = <value> AND <column_2> = <value>;
```

- ALTER VIEW
```bash
ALTER VIEW <view_name> RENAME TO <new_view_name>;
```


## MATERI MBD

### ROLE
role adalah sebuah objek yang digunakan untuk mengelompokkan user. Role dapat memiliki hak akses yang dapat digunakan oleh user yang tergabung dalam role tersebut.
- CREATE ROLE
```bash
CREATE ROLE <role_name>
[LOGIN | NOLOGIN]
password '<password>'
```
- DROP ROLE
```bash
DROP ROLE <role_name>
```
- GRANT
```bash
GRANT [select, insert, update, delete]
ON <table_name>
TO <role_name>
```

### INDEX
- CREATE INDEX
```bash
CREATE INDEX <index_name>
ON <table_name>
USING <index_method> (<column_name>);
```
  * index_method : btree, hash, gist, spgist, gin, brin

- DROP INDEX
```bash
DROP INDEX <index_name>;
```


