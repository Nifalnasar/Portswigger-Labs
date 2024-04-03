## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/f8aac420-b153-437f-b477-d40944a26097)

## Solution:

Click on the product and intercpt using burp

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/8c226a8a-9938-453e-897e-d40af6a284c9)

Change ```38.jpg``` to ```../../../etc/passwd%00.png``` and go to http request we will get etc/passwd file

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e4af1b3c-9a5e-41d5-95ea-979685f7538a)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d69bf587-9294-487e-afbf-d3a36921b9b3)
