## Lab: Basic password reset poisoning

<img width="824" height="510" alt="image" src="https://github.com/user-attachments/assets/1a7f6ed5-7a0a-4564-bcf2-f3e7dcff5083" />

Change the host header to get the logs of password reset link to the attacker controlled server

<br>
<br>

<img width="1011" height="180" alt="image" src="https://github.com/user-attachments/assets/4ba4cf5e-a38a-4b74-b5ab-9c86e7b78479" />

Token log to the attacker controlled server
use the token to change the password 

<br>
<br>

## Lab: Host header authentication bypass

<img width="886" height="664" alt="image" src="https://github.com/user-attachments/assets/6074f3ed-038d-4835-81b8-17150bec0e22" />

Use the host header injection burp extension to guess the host header as localhost to access the admin page. 

<br>
<br>

## Web cache poisoning via ambiguous requests (double host heaeder injection) 

<img width="1271" height="632" alt="image" src="https://github.com/user-attachments/assets/d6a1b86e-3873-4ffe-9071-7826c0328815" />
This app has cache web cache identified in burp scan and leveraged the poisioning with the host header attack to inject the external js code 

<br>
<br>

## Lab: Routing-based SSRF

<img width="898" height="433" alt="image" src="https://github.com/user-attachments/assets/024a9f2c-83ac-4b75-b554-4c129a23e472" />

In scan we got the host header SSRF with the collaborator payload. perfomed intruder attack to identify the internal IP address to access the IP panal with the given IP range of addresses

## Lab: Lab: Host validation bypass via connection state attack

<img width="1459" height="1171" alt="image" src="https://github.com/user-attachments/assets/20cb5d89-287a-4c8d-b95a-2ff0ddc00e45" />

This attack access the admin page by sending the parallal requests in a single connection. 

<img width="1714" height="1115" alt="image" src="https://github.com/user-attachments/assets/1942f20d-f53e-4d46-a7e0-7d5c16c3d55c" />

in second tab of the repeater which is in a group request we can access the admin page. 

