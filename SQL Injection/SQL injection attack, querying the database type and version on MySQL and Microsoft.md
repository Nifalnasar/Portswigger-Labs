This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

To solve the lab, display the database version string.

## Solution

To get number of columns 
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/ae3da3b8-7e58-4e03-a5da-2246fb6a4371)

To get the data-types used
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/c55f1424-b0de-4456-af20-f5c2356834e6)

To get the verion we need to give following payload in any one of the column as follows, then we will get the version of the database
![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/c304129d-e13c-4526-8e3e-5c6cc7a1967d)
