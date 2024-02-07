![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/c454d6a1-3a44-4cdd-a804-065d9deea28d)

Use Burp Suite to intercept and modify a request that fetches a product image.

Modify the filename parameter, giving it the value:

..%252f..%252f..%252fetc/passwd
Observe that the response contains the contents of the /etc/passwd file.
