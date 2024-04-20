## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/cc57f559-5a50-4261-b784-2c9b295e86dc)

## Solution:

In the serch functionality type `cyber` and observe the html code.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/ece95049-f748-4334-93d1-6a12c5c16633)

Try sending the payload `test'payload` and observe that your single quote gets backslash-escaped, preventing you from breaking out of the string.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d373de24-5a25-4079-bc65-c2e5c233a292)

`</script><script>alert()</script>`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/87628b22-3df3-4b33-a797-39f07e0ce032)

Lab Solved.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/2a966560-6de7-40b3-bc01-2ef921ff30f7)

