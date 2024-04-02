## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/84af0b27-9683-4e52-9f48-67f48954d245)

## Solution

Inject a standard XSS payload, such as ```<img src=1 onerror=alert(1)>```, we will get page not found

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/15c8bad0-d217-47c0-bc49-08dd9d9d290d)

Check the http request and send that session to intruder

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b6f22856-edad-4dc7-9bb3-c0bf5d724aa1)

Clear the search and add ```$$```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/3f330e60-52b6-4577-9200-388ce19e3c16)

From cross-site scripting cheat sheet, copy tage to clipboard and paste it to the ```payload settings``` field in the payloads

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/d251e5c3-6c72-42ea-bd69-cfa4edc2844e)

Start the attack

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/5e45ec40-4fd5-4143-a838-969ace094287)

Again go to the cheat sheet and copy events to clipboard and paste it to the ```payload settings``` in payloads

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/8254b0f3-aef1-47b4-a227-f2bb48331fae)

Start attack and now we get 200 ok message at onebegin

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/ea38d35a-52fe-42fa-96ae-4a479542328e)

Now search in the url ```https://0a9100d803939a4882bb103600d2006b.h1-web-security-academy.net/?search=%22%3E%3Csvg%3E%3Canimatetransform%20onbegin=alert(1)%3E```

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/48c961fe-0e4a-4cda-b1ea-8e32ed3bd914)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/56342cf7-40d8-468f-bff3-5cd7dc77e8d4)
