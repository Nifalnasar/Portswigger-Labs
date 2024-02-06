This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you need to combine some of the techniques you learned in previous labs.

The database contains a different table called users, with columns called username and password.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user.

## Solution

To get username and password from the users column we need to know number of columns being retrieved by the query.

When we tried with 1 string we get error.
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/5905fb94-f3e5-45e0-81f4-1d7c64095847)

When tried with 2 strings we got as it is having two columns
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/98ba7a5c-bca5-42e8-b208-2846dd3b2735)

To retrieve username and password we can use following sql commands
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/2034953a-7bb6-471d-b95f-5b7ecf91f9eb)

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/08108a42-f91f-4455-b6b8-0702b72fa87c)

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/a83bd8e5-335f-4a78-9d83-4651cf0e2db9)

