## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/407f2ec9-80c4-4019-867d-e7f42ef3b7cc)

## Solution:

Add a comment in the link and intercept using burp

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/9380e937-8113-4dd4-8fc6-6f371b8bc38c)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d6af1d1d-33c8-4579-bacf-e4a49bdb8e9e)

Now go back to blog and refresh the browser intercept and send to repeater

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/25acd16b-03c5-4177-8540-5e7ee58f1ecc)
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d7a73778-29b8-4722-9af5-ecbd99d749e7)

add the comment again and in the website section add payload as

`http://foo?&apos;-alert(1)-&apos;`

Go back to the blog and if we click the last comment we will get alert

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e8921def-fa2f-4f4f-8f6f-d682328fa292)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/0341e574-b4d7-4e2b-84e4-7960f861eedb)


