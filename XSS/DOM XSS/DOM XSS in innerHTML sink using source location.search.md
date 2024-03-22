## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/27526234-f3e1-4ec3-b153-18f17c108bcb)

## Solution:

Enter the following into the into the search box:

```<img src=1 onerror=alert(1)>```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a2e873fc-2a40-4832-af12-cf871cb08f8d)

Click "Search".

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/beac5fbf-05de-44b6-af45-dc59907ebf9f)

The value of the src attribute is invalid and throws an error. This triggers the onerror event handler, which then calls the ```alert()``` function. As a result, the payload is executed whenever the user's browser attempts to load the page containing your malicious post.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7770c7ee-6283-4e72-9238-aefd3f7ca88a)
