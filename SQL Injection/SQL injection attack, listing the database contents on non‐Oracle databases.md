This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The application has a login function, and the database contains a table that holds usernames and passwords. You need to determine the name of this table and the columns it contains, then retrieve the contents of the table to obtain the username and password of all users.

To solve the lab, log in as the administrator user.

## Solution

To get the number of columns, we can use following payload,
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/6e74e3c7-74aa-4152-a381-a5de8c067aa4

To get the strings, we can use following payload,
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/8c9af730-3ff2-40c7-8546-b6393ccc21ac)

To list the tables, following payload can be used.
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/83d287b4-b0d7-4156-962a-68f75301ef9d)

We got the column as "users_gldqfo"

To retrieve the columns details, use the following payload.
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/73cfd91b-5cd5-40ed-8bc6-0058a55b63c0)

To retrieve the names of the column containing username and password
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/31b9a2eb-8ced-44cc-9314-bb8bb15a22e6)

In the login page, give the details of username and password.
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/6efd26b8-671b-4d81-9f97-23b7e7bfc850)

We signed in with administrator
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/4d44481b-c559-4795-95ae-c3ae67af7ecf)
