This lab contains a path traversal vulnerability in the display of product images.

The application blocks traversal sequences but treats the supplied filename as being relative to a default working directory.

To solve the lab, retrieve the contents of the /etc/passwd file.

## Solution

Use Burp Suite to intercept and modify a request that fetches a product image.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/155aad7c-354d-4943-8621-aba1249591e1)

Modify the filename parameter, giving it the value /etc/passwd.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b7db9da8-bf13-40bc-8f29-24f3bba16c4a)

Observe that the response contains the contents of the /etc/passwd file

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/1f6fb1df-3a2c-4135-b52f-61648272d44b)

