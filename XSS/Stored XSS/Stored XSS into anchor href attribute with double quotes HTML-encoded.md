## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/4133ded2-8ad4-4a81-8eaf-473b8fe6de81)

## Solution:

View post and add the comment in comment section and use burpsuite to intercept the request

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/665c13a4-412e-44ee-a8bc-d985de8f414b)

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b9ff622e-2d51-4d04-bcaa-28e7b1f5ab60)

Click to the comment we gave and send it to the repeater

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e0e64c8b-8e3c-4a1e-9556-0da84d8a3e56)

Change the website from ```abcd1234``` to ```javascript:alert(1)```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b263c05b-b1ca-41b1-839f-26b2ff39fe74)

When we click the user name, who wrote the comment we get the alert box

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/28e0769a-97ba-44e3-9b5c-2dabc98beaa9)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/2f68ca60-d1e0-4c31-bfad-9895ed6f4d1e)
