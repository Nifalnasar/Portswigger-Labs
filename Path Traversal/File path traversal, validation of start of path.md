## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3137d238-f3ba-44d1-9be1-7ca55368fe6b)

## Solution:

This lab contains a path traversal vulnerability in the display of product images.

The application transmits the full file path via a request parameter, and validates that the supplied path starts with the expected folder.

To solve the lab, retrieve the contents of the /etc/passwd file.

Open the hoome page and click on one product

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a458c596-e659-4e1f-9afa-3c972512f841)

Change the image filename to ```../../../etc/passwd``` and check the http request

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/35ae242b-7f01-44d8-83c5-cf24cf4cadb6)

We got the contents of lab and hence lab solved.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/5813d79a-9e18-49b9-b87a-a6abcc687aa3)

