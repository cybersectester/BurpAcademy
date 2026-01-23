## Lab: Web cache poisoning with an unkeyed header
<img width="2194" height="1020" alt="image" src="https://github.com/user-attachments/assets/7d86e046-2b27-45f7-91a0-aef8b56cfbf9" />
In scanning it has been identified as the cache poision attack

<img width="2127" height="961" alt="image" src="https://github.com/user-attachments/assets/e88821d8-4c84-48cb-8e83-47be51fc6352" />
Host the jscode from the attacker controlled website to get the pop up 
<br>
<br>

## Lab: Web cache poisoning with an unkeyed cookie
<img width="2319" height="1079" alt="image" src="https://github.com/user-attachments/assets/abe3a972-0d5a-4760-94d3-b8b1edb53f40" />

<br>
<br>

## Lab: Web cache poisoning with multiple headers
<img width="2207" height="837" alt="image" src="https://github.com/user-attachments/assets/6591b68f-1d4a-4501-964e-0bad03d90d9f" />
Used multiple headers to cache the response but in scanner it gave only one header 

<br>
<br>

## Lab: Targeted web cache poisoning using an unknown header
<img width="2228" height="1016" alt="image" src="https://github.com/user-attachments/assets/db2ceadb-7bea-46ec-b041-f4d6132efd75" />

This lab serve to the intended users who uses certain browsers.

<img width="833" height="562" alt="image" src="https://github.com/user-attachments/assets/f2912bf9-4661-4413-914d-bc2592226d33" />

HTML to get the post logs to the exploit servers 

<img width="1501" height="400" alt="image" src="https://github.com/user-attachments/assets/cd0b42ea-7b88-431d-901c-3f91f5c1e66a" />

got the user agent from the victim

## Lab: Web cache poisoning via an unkeyed query string
<img width="2124" height="1125" alt="image" src="https://github.com/user-attachments/assets/ed3fe301-ba7e-4581-b1d7-58dad3f1d030" />

scanner identified the issue 

<img width="2194" height="914" alt="image" src="https://github.com/user-attachments/assets/f0a49117-d170-4fd5-938f-81108f9f7a6b" />

cached the XSS payload but we need to wait untill the cache expire to reflect the XSS bcz we don't know the cache buster 

<img width="2034" height="909" alt="image" src="https://github.com/user-attachments/assets/303ec595-6ea4-44d8-b4ef-1a1a08c95faa" />

if try with the different headers it came to know origin header is cache buster

<img width="1790" height="822" alt="image" src="https://github.com/user-attachments/assets/deab5a9b-9b67-407c-8496-f380e32ed69e" />

to get the info about the cache key in the response 

<img width="2148" height="807" alt="image" src="https://github.com/user-attachments/assets/c4ddb609-3527-4adf-bb32-8dfdf3ad69b2" />

but the burp scanner identified different cache key with the param miner


