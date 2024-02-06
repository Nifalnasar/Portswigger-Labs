This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you first need to determine the number of columns returned by the query. You can do this using a technique you learned in a previous lab. The next step is to identify a column that is compatible with string data.

The lab will provide a random value that you need to make appear within the query results. To solve the lab, perform a SQL injection UNION attack that returns an additional row containing the value provided. This technique helps you determine which columns are compatible with string data.

## Solution:

In Product Category field we can find the string 'lE0RlR'
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/60c21c39-84d0-4e76-abd7-32293d06d6e2)

When Interceptor is ON in burpsuite we can see following 
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/ff798ab4-8e6c-4766-9cb2-0515906a9487)

When we tried sql injection as below we got error in first try
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/98d12731-1d41-49c9-a8fb-6457d06587d1)

When tried in following way we got to know that the given string lies in second column.
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/e0abe122-83b7-402d-9b8c-85fade4c3e77)

