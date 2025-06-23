<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/62a7685ca6e7ce005d3f3afe-1733724189107" alt="Room Icon" width="200"/>
</p>

# Bypass Really Simple Security
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/1337rce">1337rce</a>

## Task 1: Introduction
- Really Simple Security plugin - Widely adopted security plugin.
  - Allowed attackers to bypass authentication and gain unauthorised access to user accounts.   

<br>

## Task 2: How it Works
- Wordpress has various entry points for interaction.
  - Admin Dashboard (via ```/wp-admin``` endpoint).
  - Public Interface: Managed by index.php in root directory.
  - REST API: Flexible entry point for developers to manage data.
 - CVE-2024-10924 is the CVE associated with the Really Simple Security vulnerability.
   - Vulnerability occurred due to insufficient validation of user-supplied values i.e., ```skip_onboarding```
 - Review the source code (in VM): ```/var/www/html/wp-content/plugins/really-simple-ssl/security/wordpress/two-fa```
   - Contains PHP class called ```Rsssl_Two_Factor_On_Board_Api```
   - **skip_onboarding**: Return value from ```check_login_and_get_user``` not validated (means null accepted as valid user).
   - **check_login_and_get_user**: Function that identifies invalid credentials. Relies on caller to return value, but this does not occur.
   - **authenticate_and_redirect**: Blindly redirects users based on parameters passed to it.

<br>

#### Q1: What is the class name that holds the important three functions discussed in the task?
<pre>Rsssl_Two_Factor_On_Board_Api</pre>
<br>

#### Q2: What is the function name that accepts user_id and login_nonce as arguments and validates them?
<pre>check_login_and_get_user</pre>

## Task 3: How to Exploit
- Involves using a POST request to vulnerable endpoint.
- Use **Developer Tools** to add cookies (thus exploiting the vulnerability).
  - Can also use an extension like **Cookiebro Editor**.

<br>

#### Q1: What email address is associated with the username admin (**user_id** 1)?
<pre>admin@fake.thm</pre>
You can find this on ```vulnerablewp.thm:8080/wp-admin/profile.php```

<br>

#### Q2: How many parameters does the endpoint **/reallysimplessl/v1/two_fa/skip_onboarding** accept? Write digit only.
<pre>3</pre>
The answer can be found in the previous task. The skip_onboarding method accepts **user_id, login_None, and redirect_to**.

<br>

#### Q3: What is the HTTP method required for exploiting this vulnerability? (GET/POST)
<pre>POST</pre>

## Task 4: Detection and Mitigation
- Here are some methods for examining logs for potential exploitation:
  - Check weblogs for API calls.
  - Analyze authentication logs.
  - SIEM query.
    - i.e., ```method:POST AND path:"/reallysimplessl/v1/two_fa/skip_onboarding"```

- Additional mitigation measures to secure your website:
  - Apply official patch.
  - Update SIEM alerts.
  - Implement proper input validation and rigorous error handling for all API endpoints.

<br>

#### Q1: As a security engineer, you have identified a call to the **/reallysimplessl/v1/two_fa/skip_onboarding** endpoint from the weblogs. Does that confirm that the user is 100% infected? (yea/nay)
<pre>nay</pre>
Not necessarily. It would be unusual to see repeated POST requests or varying parameters (i.e., user_id, login_nonce).
