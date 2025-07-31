# think


First I had to install the sql-server into my linux system, and using terminal I had to grant permission privileges to a new user assigned to the db for localhost(faced some permission issues there)
After succesfully setting up the sql-server, I created the Database which a schema. Here, I made a huge mistake --> I accidentaly thought that there were only 4 fields in the products file so I created the schema keeping that in mind
<img width="1872" height="1015" alt="image" src="https://github.com/user-attachments/assets/5159523b-c867-4db8-9f61-c37d50585459" />

Then i tried to load the data into mysql using LOAD Infile command of the sql and kept facing the issue of a mismatch between the expected schema and actual resulting schema(took almost 1 hour to figure out that it was a silly mistake on my end where i kept loading wrong number of fields into sql)

Issues faced while loading, mysql-server accepts files from only /var/lib/mysql-files/ inside LINUX system, so I had to cp the content of the products.csv into that directory manually with escalated privileges

to see the changes, I had to use ls -l command to verify the output

i received a successful log of load data succesfull in mysql
mysql> DESCRIBE TABLE products;
+----+-------------+----------+------------+------+---------------+------+---------+------+-------+----------+-------+
| id | select_type | table    | partitions | type | possible_keys | key  | key_len | ref  | rows  | filtered | Extra |
+----+-------------+----------+------------+------+---------------+------+---------+------+-------+----------+-------+
|  1 | SIMPLE      | products | NULL       | ALL  | NULL          | NULL | NULL    | NULL | 48498 |   100.00 | NULL  |
+----+-------------+----------+------------+------+---------------+------+---------+------+-------+----------+-------+
1 row in set, 1 warning (0.00 sec)
