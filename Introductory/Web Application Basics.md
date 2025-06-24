<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/2d29d11807430c2448e77a00f10d52c9c4f1993af71c9765190b36986323d7af.66c513e4445cb5649e636a36-1725441274792" alt="Room Icon" width="200"/>
</p>

# Web Application Basics
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/strategos">strategos</a>, <a href="https://tryhackme.com/p/1337rce">1337rce</a>, <a href="https://tryhackme.com/p/MartaStrzelec">MartaStrzelec</a>, <a href="https://tryhackme.com/p/l000g1c">l000g1c</a>, <a href="https://tryhackme.com/p/rePl4stic">rePl4stic</a>, <a href="https://tryhackme.com/p/MonAha">MonAha</a>

## Task 2: Web Application Overview
### Front End
- Interface of an web application that users can see and interact with.
- HTML, CSS, JavaScript.

### Back End
- Something you don't see but are important for the web application to work.
- Database, Infrastructure, Web Application Firewall (WAF).

<br>

#### Q1: Which component on a computer is responsible for hosting and delivering content for web applications?
<pre>web server</pre>
<br>

#### Q2: Which tool is used to access and interact with web applications?
<pre>web browser</pre>
<br>

#### Q3: Which component acts as a protective layer, filtering incoming traffic to block malicious attacks, and ensuring the security of the web application?
<pre>web application firewall</pre>
<br>

## Task 3: Uniform Resource Locator
A URL is a web address that allows you to access online content.
### Anatomy of a URL
![image](https://github.com/user-attachments/assets/36eaa027-3ec9-4143-994b-b5c5aa2338b1)
- **Scheme**: Protocol used to acess website (i.e., HTTP).
- **User**: User login details (security risk).
- **Host/Domain**: Tells which website you're accessing.
  - Domain names that appear real but with small differences - **typosquatting**.
- **Port**: Directs browser to right service on web server (1-65535).
- **Path**: Specific file or page you're trying to access.
- **Query String**: Starts with a question mark (?). Used for search terms or inputs.
  - Important to handle securely to prevent **injection** attacks. 
- **Fragment**: Starts with a hash symbol (#). Points to specific section of webpage. Users can also modify this too.

<br>

#### Q1: Which protocol provides encrypted communication to ensure secure data transmission between a web browser and a web server?
<pre>HTTPS</pre>
<br>

#### Q2: What term describes the practice of registering domain names that are misspelt variations of popular websites to exploit user errors and potentially engage in fraudulent activities?
<pre>Typosquatting</pre>
<br>

#### Q3: What part of a URL is used to pass additional information, such as search terms or form inputs, to the web server?
<pre>Query String</pre>
<br>

## Task 4: HTTP Messages
- HTTP messages are packets of data exchanged between user and web server.
![image](https://github.com/user-attachments/assets/a3bb27b5-204d-44d2-bf50-dfcf757b35c0)
- Two types: **HTTP Requests, HTTP Responses**
  - **Start Line**: Intro. Tells what kind of message is being sent and how it should be handled.
  -  **Headers**: Provide extra information about HTTP message. Gives instructions to client and server.
  -  **Empty Line**: Little divider separating header from body.
  -  **Body**: Where actual data is stored.

<br>

#### Q1: Which HTTP message is returned by the web server after processing a client's request?
<pre>HTTP response</pre>
<br>

#### Q2: What follows the headers in an HTTP message?
<pre>Empty Line</pre>
<br>

## Task 5: HTTP Request: Line and Methods
![image](https://github.com/user-attachments/assets/e4584fdc-3b48-45cd-b7d4-aac827caef50)
- **Request Line**: Tells server what kind of request it's dealing with.
  - Three main parts: **HTTP method, URL path, and HTTP version**.
  - Example: ```METHOD /path HTTP/version```
### HTTP Methods
- Tells server what action user wants to perform on resource.
- **GET**: Fetch data from server.
- **POST**: Send data to server.
- **PUT**: Replaces or updates something on server.
- **DELETE**: Removes something from server.
- **PATCH**: Update part of resource.
- **HEAD**: Similar to GET but only retrieves headers.
- **OPTIONS**: Tells what methods are available for specific resource.
- **TRACE**: Shows which methods are allowed (often for debugging).
- **CONNECT**: Used to create secure connection.
### URL Path
- Validate URL path to prevent unauthorized access.
- Sanitise path to avoid injection attacks.
- Protect data by conducting privacy and risk assessments.
### HTTP Version
- Protocol version used to communicate between client and server.
- **HTTP/0.9** (1991) - First version, only supports GET requests.
- **HTTP/1.0** (1996) - Added headers and better support for content, improving caching.
- **HTTP/1.1** (1997) - Persistent connections, chunked transfer encoding, better cachine. Widely used.
- **HTTP/2** (2015) - Multiplexing, header compression, and prioritisation for faster performance.
- **HTTP/3** (2022) - Uses new protocol (QUIC) for quicker and secure connections.

<br>

#### Q1: Which HTTP protocol version became widely adopted and remains the most commonly used version for web communication, known for introducing features like persistent connections and chunked transfer encoding?
<pre>HTTP/1.1</pre>
<br>

#### Q2: Which HTTP request method describes the communication options for the target resource, allowing clients to determine which HTTP methods are supported by the web server?
<pre>OPTIONS</pre>
<br>

#### Q3: In an HTTP request, which component specifies the specific resource or endpoint on the web server that the client is requesting, typically appearing after the domain name in the URL?
<pre>URL Path</pre>
<br>

## Task 6: HTTP Request: Headers and Body
- Common Request Headers:
  - **Host**: Name of web server request is for.
  - **User-Agent**: Information about web browser the request is coming from.
  - **Referer**: URL from which the request came from.
  - **Cookie**: Information web server previously stored (user preferences).
  - **Content-Type**: Type of data in request.
### Request Body
- **URL Encoded (application/x-www-form-urlencoded)**: Data is structured in key-value pairs. Separated by an & symbol. Special characters are percent-encoded.
  - Example: ```name=Aleksandra&age=27&country=US```
- **Form Data (multipart/form-data)**: Multiple blocks of data. Used for uploading files or images to a web server.
  - Example:
    ```----WebKitFormBoundary7MA4YWxkTrZu0gW
    Content-Disposition: form-data; name="username"
    
    aleksandra
    ----WebKitFormBoundary7MA4YWxkTrZu0gW
    Content-Disposition: form-data; name="profile_pic"; filename="aleksandra.jpg"
    Content-Type: image/jpeg
    
    [Binary Data Here representing the image]
    ----WebKitFormBoundary7MA4YWxkTrZu0gW--```
- **JSON (application/json)**: Data can be sent using JSON. Formatted in key-value pairs, with each pair separated by commas and all enclosed in curly braces.
- **XML (application/xml**: Data is structured inside labels called tags.

<br>

#### Q1: Which HTTP request header specifies the domain name of the web server to which the request is being sent?
<pre>Host</pre>
<br>

#### Q2: What is the default content type for form submissions in an HTTP request where the data is encoded as key=value pairs in a query string format?
<pre>application/x-www-form-urlencoded</pre>
<br>

#### Q3: Which part of an HTTP request contains additional information like host, user agent, and content type, guiding how the web server should process the request?
<pre>Request Headers</pre>
<br>

## Task 7: HTTP Response: Status Line and Status Codes
- HTTP response include a status code and short explanation (aka Reason Phrase).
### Status Line
- First line in HTTP response.
- Three key pieces of info:
  1. **HTTP Version**
  2. **Status Code**: Three-digit number describing the outcome.
  3. **Reason Phrase**
### Status Codes and Reason Phrases
- **Informational Responses (100-199)**
  - These codes mean the server has received part of the request and is waiting for the rest. It’s a "keep going" signal.
- **Successful Responses (200-299)**
  - These codes mean everything worked as expected. The server processed the request and sent back the requested data.
- **Redirection Messages (300-399)**
  - These codes tell you that the resource you requested has moved to a different location, usually providing the new URL.
- **Client Error Responses (400-499)**
  - These codes indicate a problem with the request. Maybe the URL is wrong, or you’re missing some required info, like authentication.
- **Server Error Responses (500-599)**
  - These codes mean the server encountered an error while trying to fulfil the request. These are usually server-side issues and not the client’s fault.
### Common Status Codes
- **100 (Continue)**
  - The server got the first part of the request and is ready for the rest.
- **200 (OK)**
  - The request was successful, and the server is sending back the requested resource.
- **301 (Moved Permanently)**
  - The resource you’re requesting has been permanently moved to a new URL. Use the new URL from now on.
- **404 (Not Found)**
  - The server couldn’t find the resource at the given URL. Double-check that you’ve got the right address.
- **500 (Internal Server Error)**
  - Something went wrong on the server’s end, and it couldn’t process your request.

<br>

#### Q1: What part of an HTTP response provides the HTTP version, status code, and a brief explanation of the response's outcome?
<pre>Status Line</pre>
<br>

#### Q2: Which category of HTTP response codes indicates that the web server encountered an internal issue or is unable to fulfil the client's request?
<pre>Server Error Responses</pre>
<br>

#### Q3: Which HTTP status code indicates that the requested resource could not be found on the web server?
<pre>404</pre>
<br>

## Task 8: HTTP Response: Headers and Body
![image](https://github.com/user-attachments/assets/b3300523-d76a-4e94-9ccb-a17b1fd85aab)
### Required Response Headers
- **Date**
- **Content-Type**: For example, HTML or JSON.
- **Server**: Shows what kind of server software is handling the request.

### Other Common Response Headers
- **Set-Cookie**: Sends cookie from server to client. Clients uses this with future requests.
  - Ensure cookies are set with ```HttpOnly``` flag (can't be accessed by JS) and ```Secure``` flag (only sent over HTTPS).
-  **Cache-Control**: Tells client how long response can be cached before checking server again.
-  **Location**: Tells client where to go next if resource moved.

<br>

#### Q1: Which HTTP response header can reveal information about the web server's software and version, potentially exposing it to security risks if not removed?
<pre>Server</pre>
<br>

#### Q2: Which flag should be added to cookies in the Set-Cookie HTTP response header to ensure they are only transmitted over HTTPS, protecting them from being exposed during unencrypted transmissions?
<pre>Secure</pre>
<br>

#### Q3: Which flag should be added to cookies in the Set-Cookie HTTP response header to prevent them from being accessed via JavaScript, thereby enhancing security against XSS attacks?
<pre>HttpOnly</pre>
<br>

## Task 9: Security Headers
- Can use a site like https://securityheaders.io/ to analyse security headers of any website.
- **Content-Security-Policy (CSP)**: Mitigates against Cross-Site-Scripting (XSS).
  - Declares which domains or sources are safe.
  - Properties: **default-src** (default policy), **script-src** (where scripts can be loaded from), **style-src** (where CSS style sheets can be loaded from).
  - Example: ```Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'``` 
- **Strict-Transport-Security (HSTS)**: Ensures web browsers will always connect over HTTPS.
  - Properties: **max-age** (expiry time), **includeSubDomains** (instructs browser to apply setting to all subdomains), **preload** (website to be included in preload lists [before first website visit]).
  - Example: ```Strict-Transport-Security: max-age=63072000; includeSubDomains; preload```  
- **X-Content-Type-Options**: Instructs browsers to only use Content-Type header.
  - Example: ```X-Content-Type-Options: nosniff```
    - **nosniff**: No sniff or guess MIME type.
- **Referrer-Policy**: Controls amount of information sent to web server.
  - **no-referrer**: Disables any info about referrer.
  - **same-origin**: Only sends referrer information when destination part of same origin.
  - **strict-origin**: Policy only sends referrer as origin when protocol stays the same.
  - **strict-origin-when-cross-origin**: Sends full URL path in origin header.

<br>

#### Q1: In a Content Security Policy (CSP) configuration, which property can be set to define where scripts can be loaded from?
<pre>script-src</pre>
<br>

#### Q2: When configuring the Strict-Transport-Security (HSTS) header to ensure that all subdomains of a site also use HTTPS, which directive should be included to apply the security policy to both the main domain and its subdomains?
<pre>includeSubDomains</pre>
<br>

#### Q3: Which HTTP header directive is used to prevent browsers from interpreting files as a different MIME type than what is specified by the server, thereby mitigating content type sniffing attacks?
<pre>nosniff</pre>
<br>

## Task 10: Practical Task: Making HTTP Requests
This task involves launching a static site in Split View. Click on **View Site** to begin. The following answers will be based on this site.
<br>

#### Q1: Make a GET request to /api/users. What is the flag?
<pre>THM{YOU_HAVE_JUST_FOUND_THE_USER_LIST}</pre>
Append ```/api/users``` to the end of the URL. Then click Go to receive the flag.

<br>

#### Q2: Make a POST request to /api/user/2 and update the country of Bob from UK to US. What is the flag?
<pre>THM{YOU_HAVE_MODIFIED_THE_USER_DATA}</pre>
Change the ending of the URL to ```/api/user/2```. Change the request type to POST. Click on the cogwheel icon and set **country** as the key and **US** as the value then save. Click Go and you should receive the flag.

<br>

#### Q3: Make a DELETE request to /api/user/1 to delete the user. What is the flag?
<pre>THM{YOU_HAVE_JUST_DELETED_A_USER}</pre>
Change the request type to DELETE and change the end of the URL to ```/api/user/1```. Click Go and you should receive the flag.

