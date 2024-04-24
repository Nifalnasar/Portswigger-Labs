## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/2d2507be-536b-49a4-8696-a95a9fbfa9b3)

## Solution:

This lab contains a SQL injection vulnerability in its stock check feature. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables.

The database contains a users table, which contains the usernames and passwords of registered users. To solve the lab, perform a SQL injection attack to retrieve the admin user's credentials, then log in to their account.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/dc172a10-5c3d-4a46-b59f-477071aa3050)

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/db6b0001-2296-4650-a10c-bccc077989fd)
