![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/233c8eba-fa2b-41ad-ba20-2425cb4f5902)

## Solution:

Use Burp Suite to intercept and modify a request that fetches a product image.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3a8044ee-2822-4d7d-8a23-a9c7a2f58139)

Modify the filename parameter, giving it the value:
> ....//....//....//etc/passwd

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b124982f-199e-4ca1-aec6-e5abe282ad68)

Observe that the response contains the contents of the /etc/passwd file.
