## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/824c66f3-9d81-44f8-a214-225f60d372d9)

## Solution:

Open the website and search for ```XSS```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/773859af-4769-4b98-8674-62b4733b037c)

Check the http request in burp

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e01ab095-df3d-497c-8d27-8d1941a71da8)

In burp goto- target- and then resources and in the java script response search for ```eval()```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fc3e5b2e-fc11-41df-8469-b999d1b4096d)


now try to search for ```\"-alert(1)}//``` we will get alert 

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/5a004a79-05c7-476f-b26d-e616eab0887e)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/53f0b977-e27a-40cb-8407-304cc7e1b7ea)

