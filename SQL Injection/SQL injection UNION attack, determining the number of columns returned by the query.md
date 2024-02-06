This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. The first step of such an attack is to determine the number of columns that are being returned by the query. You will then use this technique in subsequent labs to construct the full attack.

To solve the lab, determine the number of columns returned by the query by performing a SQL injection UNION attack that returns an additional row containing null values.

First Page 
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/4066db4e-265b-4734-bb5e-f7d2ad1293ae)

When Interceptor in Burpsuite is ON, we will get following 
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/378865a7-aef4-4b90-91cb-bc461bf884a7)

To Identify number of columns we can use NULL statement.
In first try, we used as following 
> Payload = 'UNION+SELECT+NULL--
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/fdb7cefd-321e-4e93-9031-50a3899fd527)
But we get error 

>Payload = 'UNION+SELECT+NULL,NULL--
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/eb9d01b7-3fca-475b-a039-939caa831f99)
WE get error

> Payload = 'UNION+SELECT+NULL,NULL,NULL--
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/e9b75f8f-45fa-4ab9-9edf-1e52191bff01)
Now we understand that we have 3 columns in the UNION sql statement
