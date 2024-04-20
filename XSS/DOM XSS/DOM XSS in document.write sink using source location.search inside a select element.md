## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d2f4b67b-0451-449f-a016-23a086b5a91a)

## Solution:

On the product pages, notice that the dangerous JavaScript extracts a `storeId` parameter from the `location.search` source. It then uses `document.write` to create a new option in the select element for the stock checker functionality.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/8020becc-c6d5-4eb8-a1d8-8644af95fe7c)

In the browser, notice that your random string is now listed as one of the options in the drop-down list.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/6e268f7b-2c02-4961-b6e4-2711dfb6db4f)

Right-click and inspect the drop-down list to confirm that the value of your storeId parameter has been placed inside a select element.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/1136b78f-39df-41ca-88a4-2c58ffbc6a1e)

Change the URL to include a suitable XSS payload inside the `storeId` parameter as follows:

```
product?productId=1&storeId="></select><img%20src=1%20onerror=alert(1)>
```
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e8131935-e08d-468a-8a55-69c36b1798cb)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/48334a91-cf24-445b-91f8-7d0627c7ccdb)
