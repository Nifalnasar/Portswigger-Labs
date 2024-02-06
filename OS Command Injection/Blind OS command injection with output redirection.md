This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response. However, you can use output redirection to capture the output from the command. There is a writable folder at:

> /var/www/images/

The application serves the images for the product catalog from this location. You can redirect the output from the injected command to a file in this folder, and then use the image loading URL to retrieve the contents of the file.

To solve the lab, execute the whoami command and retrieve the output.

## Solution

1. Use Burp Suite to intercept and modify the request that submits feedback.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/631ab184-b751-46ea-8e09-0ffa52105cfe)

2. Modify the email parameter, changing it to:

> email=||whoami>/var/www/images/output.txt||

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/99685772-d389-47fa-9569-8161220c07da)

3. Now use Burp Suite to intercept and modify the request that loads an image of a product.

4. Modify the filename parameter, changing the value to the name of the file you specified for the output of the injected command:

> filename=output.txt

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/c411861e-3dd1-48a4-85fb-99e37268c5b6)

5. Observe that the response contains the output from the injected command.

![image](https://github.com/Nifalnasar/Web-Security-Lab/assets/141356053/c3c21a5e-ec0e-4de3-ba1f-01fe64d4197e)

