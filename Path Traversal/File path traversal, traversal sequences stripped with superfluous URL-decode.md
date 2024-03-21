## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/c454d6a1-3a44-4cdd-a804-065d9deea28d)

Solution:

You can sometimes bypass this kind of sanitization by URL encoding, or even double URL encoding, the ```../``` characters. This results in ```%2e%2e%2f``` and ```%252e%252e%252f``` respectively. Various non-standard encodings, such as ```..%c0%af``` or ```..%ef%bc%8f```, may also work.

Use Burp Suite to intercept and modify a request that fetches a product image.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/384d0bf6-f8f6-4a54-a372-e7752284c852)

Check the http request for the above product and send it to the repeater

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/2835bc16-81d4-4c04-8cab-709e7237e5bd)

Modify the filename parameter, giving it the value:

```..%252f..%252f..%252fetc/passwd``` what we did here is double url enconding.
