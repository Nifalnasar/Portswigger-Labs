## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b6a68636-015c-4eab-8bfd-5809b08b3916)

## Solution:

Enter a random alphanumeric string into the search box.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fa6b3592-c7db-45cf-b4da-6e334ed0442b)

View the page source and observe that your random string is enclosed in an ng-app directive.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3d1628e8-be10-413a-9139-1fe157546a5d)

Enter the following AngularJS expression in the search box:

```
{{$on.constructor('alert(1)')()}}
```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/4cc1906a-c5eb-4c13-8029-00cfb3190972)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3fc20ee1-1086-4c68-997a-da70d9f1558b)
