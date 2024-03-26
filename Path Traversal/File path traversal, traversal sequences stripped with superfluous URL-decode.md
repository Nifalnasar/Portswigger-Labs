## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/c454d6a1-3a44-4cdd-a804-065d9deea28d)

Solution:

Use Burp Suite to intercept and modify a request that fetches a product image.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/afe947a3-22f5-406a-b0ce-adb12de4de7d)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/f8cd5be6-2f10-4d50-aadc-263330e25630)

Modify the filename parameter, giving it the value by ```..%252f..%252f..%252fetc/passwd```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b3048264-f58d-46ab-a987-4c1785415e2c)

Lab Solved

![Uploading image.png…]()
