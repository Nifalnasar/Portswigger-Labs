This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The database contains a different table called users, with columns called username and password.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user.

## Solution
We need to find the number of columns and in which column the string is returning
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/5810b59e-7abc-4bb7-a52e-f87e5e8403a3)
Here we have 2 columns and string returned in second column.

By following payload we can retrieve the username and password in one column
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/03ccf1ca-13fe-4600-aa31-d93b57e808aa)

