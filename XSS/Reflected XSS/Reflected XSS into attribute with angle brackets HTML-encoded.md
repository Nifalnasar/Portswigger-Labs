## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/172ee52d-2f9c-487b-a753-1c2c4f63bd72)

## Solution:

Search for a string ```abcd1234```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3413e863-aa97-47bb-9297-827c9a28005a)

We can see when we search a string it is taken in by using single inverted commas

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/c08559b2-aaf3-4e46-888e-0ea7bde21475)

Replace  input with the following payload to escape the quoted attribute and inject an event handler:

```"onmouseover="alert(1)```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d62ef2fd-8381-4775-baeb-81d9f98f8cca)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/1c3babf3-0ec5-4ec9-b38f-d7505dacdab0)
