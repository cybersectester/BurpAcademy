# CL.TE

<br>
<br>

# TE.CL
<img width="638" height="376" alt="image" src="https://github.com/user-attachments/assets/24397d64-aa9e-4472-9340-030387e1c449" />

A3\r\n  is 4 for content length and no need to count \r\n one line above it when calculate the content length in the first request  
Transfer encoding 0 always end with the  
0/r/n  
/r/n  

<br>
<br>

# H2.CL
<img width="572" height="260" alt="image" src="https://github.com/user-attachments/assets/62b146ca-69af-49cf-802a-5c30941e7d27" />
Front end accpet h2 CL and backend accepts/downgraded to http1.1 with CL   
This attack alter the host header so that victim load attacker controlled js  

<br>
<br>

# H2.TE
<img width="678" height="310" alt="image" src="https://github.com/user-attachments/assets/083d6050-3836-4365-b00c-8cc93a9215de" />

This attack to smuggle the admin request to ourself by proving two invalid requests so that genuine requests of admin can be received to burp suite   
Terminate the host header last by providing the two \r\n so that the request completed   
Remove content length header add only transfer encoding header   
Front end determine the content length for http2 built in mechanism and back end prefer over the chunked header to process the data  

<br>
<br>

# HTTP2 CRLF smuggling
<img width="988" height="838" alt="image" src="https://github.com/user-attachments/assets/28b3f663-85e7-4520-bb23-92696d10ca32" />

Front end stripping the tranasfer encoding in h2 method  

<img width="774" height="372" alt="image" src="https://github.com/user-attachments/assets/8a2ffd24-6ab1-4bae-95fc-e8e597cea446" />

Another user request will add to the request and show in search field

<br>
<br>


# Request splitting CRLF H2

<img width="1154" height="874" alt="image" src="https://github.com/user-attachments/assets/bc106ead-0c55-4a10-a047-ccf2e3e98fc4" />

Adding another request using the header in http2  
So smuggle the order of the sequence to get the admin response to us  

<br>
<br>

# CL.0

<img width="1876" height="368" alt="image" src="https://github.com/user-attachments/assets/7f004915-e835-4f7d-8ea6-f665804634f2" />

<br>

<img width="786" height="312" alt="image" src="https://github.com/user-attachments/assets/72fb9a74-783b-4401-8cc4-a904c987826b" />

Using a static file send the parallel connection  
The susequent request get no found /rtttt for this  

<img width="682" height="306" alt="image" src="https://github.com/user-attachments/assets/b57456af-ea88-452a-a694-18cc28276eba" />

We can access admin now  

