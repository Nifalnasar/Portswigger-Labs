This lab contains a path traversal vulnerability in the display of product images.
To solve the lab, retrieve the contents of the /etc/passwd file.

## Solution

Use Burp Suite to intercept and modify a request that fetches a product image.
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d9ad9d07-8f90-4e93-866e-0389e4cdc7f9)

Modify the filename parameter, giving it the value:
> ../../../etc/passwd
![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3e971066-36e3-430d-bed6-1034fd262a6f)
