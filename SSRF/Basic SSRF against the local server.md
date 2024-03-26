## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fc4e07ed-941f-4f1f-9993-a12447c6c6e6)

## Solution:

Click on to one product and using burp intercept the request made, we can see stockapi

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/15177b5c-10c4-4963-928b-97bc7b746b8a)

change the stock api to ```http://localhost/admin```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/191a0ef8-ce0f-40db-97fd-252e06222c87)

To delete the user carlos change the stockapi as ```http://localhost/admin/delete?username=carlos```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/dd1e96a9-aa94-4762-adb5-ee85dc3442d0)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a29a81d5-ee68-4d3a-ad8d-f59da87df612)


