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
