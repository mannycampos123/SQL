# SQL
My SQL Portfolio

//Problem: split one column with a string of variable characters into 5 unique columns seperated by a pipe delimeter


//first, creating a table

create table  name(
demo_key varchar (50)
);

//second import the data

insert into name
values
("N|WM2534|NC+3|I|3"),
("N|MN1834|NC+3|I|3"),
("N|MN1834|NC+3|I|3"),
("N|HH|N|R|X|R|0|"),
("N|AD2554|N|I|"),
("N|AD2549|NC+3|I|3"), 
("N|MN2534|NC+3|R|3"),
("N|MN1834|NC+3|I|3"),
("N|WM1834|NC+3|R|3"),
("N|AD1834|NC+3|I|3"),
("N|HH|N|I|X|X|"),
("N|AD2554|NC+3|I|3"),
("N|MN2534|NC+3|R|3"),
("N|AD1849|NC+3|I|3"),
("N|AD2549|NC+3|R|3"),
("N|WM1834|NC+3|I|3"),
("N|MN2549|NC+3|R|3"),
("N|AD2554|NC+3|I|3");

//results: select * from name;

+-------------------+
| demo_key          |
+-------------------+
| N|WM2534|NC+3|I|3 |
| N|MN1834|NC+3|I|3 |
| N|MN1834|NC+3|I|3 |
| N|HH|N|R|X|R|0|   |
| N|AD2554|N|I|     |
| N|AD2549|NC+3|I|3 |
| N|MN2534|NC+3|R|3 |
| N|MN1834|NC+3|I|3 |
| N|WM1834|NC+3|R|3 |
| N|AD1834|NC+3|I|3 |
| N|HH|N|I|X|X|     |
| N|AD2554|NC+3|I|3 |
| N|MN2534|NC+3|R|3 |
| N|AD1849|NC+3|I|3 |
| N|AD2549|NC+3|R|3 |
| N|WM1834|NC+3|I|3 |
| N|MN2549|NC+3|R|3 |
| N|AD2554|NC+3|I|3 |
+-------------------+


//lastly, seperate the columns by using the SUBSTRING_INDEX function and adjusting the perameters (using another SUBSTRING_INDEX if needed)
select demo_key,
SUBSTRING_INDEX(demo_key, "|", 1) as column1,
SUBSTRING_INDEX(SUBSTRING_INDEX(demo_key, "|", 2), "|", -1) as column2,
SUBSTRING_INDEX(SUBSTRING_INDEX(demo_key, "|", -3), "|", 1) as column3,
SUBSTRING_INDEX(SUBSTRING_INDEX(demo_key, "|", -2), "|", 1) as column4, 
SUBSTRING_INDEX(demo_key, "|", -1) as column5
from name;

//final results: 

+-------------------+---------+---------+---------+---------+---------+
| demo_key          | column1 | column2 | column3 | column4 | column5 |
+-------------------+---------+---------+---------+---------+---------+
| N|WM2534|NC+3|I|3 | N       | WM2534  | NC+3    | I       | 3       |
| N|MN1834|NC+3|I|3 | N       | MN1834  | NC+3    | I       | 3       |
| N|MN1834|NC+3|I|3 | N       | MN1834  | NC+3    | I       | 3       |
| N|HH|N|R|X|R|0|   | N       | HH      | R       | 0       |         |
| N|AD2554|N|I|     | N       | AD2554  | N       | I       |         |
| N|AD2549|NC+3|I|3 | N       | AD2549  | NC+3    | I       | 3       |
| N|MN2534|NC+3|R|3 | N       | MN2534  | NC+3    | R       | 3       |
| N|MN1834|NC+3|I|3 | N       | MN1834  | NC+3    | I       | 3       |
| N|WM1834|NC+3|R|3 | N       | WM1834  | NC+3    | R       | 3       |
| N|AD1834|NC+3|I|3 | N       | AD1834  | NC+3    | I       | 3       |
| N|HH|N|I|X|X|     | N       | HH      | X       | X       |         |
| N|AD2554|NC+3|I|3 | N       | AD2554  | NC+3    | I       | 3       |
| N|MN2534|NC+3|R|3 | N       | MN2534  | NC+3    | R       | 3       |
| N|AD1849|NC+3|I|3 | N       | AD1849  | NC+3    | I       | 3       |
| N|AD2549|NC+3|R|3 | N       | AD2549  | NC+3    | R       | 3       |
| N|WM1834|NC+3|I|3 | N       | WM1834  | NC+3    | I       | 3       |
| N|MN2549|NC+3|R|3 | N       | MN2549  | NC+3    | R       | 3       |
| N|AD2554|NC+3|I|3 | N       | AD2554  | NC+3    | I       | 3       |
+-------------------+---------+---------+---------+---------+---------+

