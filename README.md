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

During The second phase when i tried to see the some products related information i found that actually the no data was being loaded into the mysql server, so I had to TRUNCATE TABLE products; then I saw the schema and sql queries working properly like:
<img width="1046" height="121" alt="image" src="https://github.com/user-attachments/assets/5355833d-f1d7-459c-b4f1-1d0cddf3d031" />

gave 758 rows
and here are the end logs:
2025-07-31 12:45:08 |  19.9899997711182 | Women      | F03B7237E53E6D51070F92ED4CCA90EA |                      4 |
| 15983 |   4.6753198776993 | Plus     | Anne Klein Women's 2 Pack Stripe Slipper Socks                                                                                                      | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 |   9.9899997711182 | Women      | C80743F12DE3498A6CF0D7D10E732233 |                      2 |
| 15984 |  76.6158410870767 | Plus     | New Ray Ban RB 4179 601/9A Black Men Women Plastic Sunglasses                                                                                       | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 | 142.9400024414063 | Women      | 5EF9F5AE91440A6E6CB56E870819466A |                      2 |
| 15985 |  11.7844997801185 | Plus     | Acrylic Tallit (imitation Wool) Prayer Shawl in Blue and Silver Size 24 L X 72 W                                                                    | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 |  25.8999996185303 | Women      | 3BEEAB85046CA201D73BB9D129BCFC3F |                      1 |
| 15986 |  23.7119999974966 | Plus     | Three Dots Women's Longsleeve Crewneck Tee                                                                                                          | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 |  48.0000000000000 | Women      | EE0E944A35FE7E542D4C03B05A5E6802 |                      4 |
| 15987 |   4.0988698847267 | Plus     | Solid Color Polyester 3 Piece Fleece Hat Scarf & Glove Women's Winter Set                                                                           | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 |   7.9899997711182 | Women      | 6A710CDCCDB02B3301D71D83ED3D15B3 |                     10 |
| 15988 |   2.7627600161189 | Plus     | Voodoo Tactical Shemagh Arab Head Scarf Kafiya                                                                                                      | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 |   5.9800000190735 | Women      | 9E4F7D7B2E283F464766CB66DBD50A8E |                      4 |
| 15989 |  14.4551799129170 | Plus     | Alfred Dunner Classics Elastic Waist Corduroy Pants                                                                                                 | 2025-07-31 12:45:08 | 2025-07-31 12:45:08 |  29.9899997711182 | Women      | 9070FB51F2C1DBD76E12B4229D24DEAA |                      2 |
+-------+-------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+---------------------+-------------------+------------+----------------------------------+------------------------+
758 rows in set (0.02 sec)


