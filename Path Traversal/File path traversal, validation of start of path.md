## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3137d238-f3ba-44d1-9be1-7ca55368fe6b)

## Solution:

An application may require the user-supplied filename to start with the expected base folder, such as 1```/var/www/images```. In this case, it might be possible to include the required base folder followed by suitable traversal sequences.

For example: ```filename=/var/www/images/../../../etc/passwd```

Use Burp Suite to intercept and modify a request that fetches a product image.
