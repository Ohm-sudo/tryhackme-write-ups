<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/5e6bbe59a46ee9407fd65bbe-1726735019985" alt="Room Icon" width="200"/>
</p>

# CyberChef: The Basics
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/magic4n6">magic4n6</a>, <a href="https://tryhackme.com/p/strategos">strategos</a>, <a href="https://tryhackme.com/p/Aashir.Masood">Aashir.Masood</a>

## Task 1: Introduction
- CyberChef is like having a toolbox of tools for different tasks.
- Uses recipes - consists of sequential tasks.
- Recommended to check out following rooms before starting room:
  - Hashing Basics
  - Cryptography Basics
 
## Task 2: Accessing the Tool
<a href="https://gchq.github.io/CyberChef">Online Access</a><br>
<a href="https://github.com/gchq/CyberChef/releases">Offline or Local Copy</a>

## Task 3: Navigating the Interface

Consists of four areas:
1. Operations
2. Recipe
3. Input
4. Output

![image](https://github.com/user-attachments/assets/a221ea5b-17f6-4128-8b9b-51b0453b280c)

### Common Operations
| Operations | Description |
|------------|-------------|
| From Morse Code | Translate morse code into alphanumeric characters. |
| URL Encode | Encodes characters into percent-encoding |
| To Base64 | Encodes raw data into Base64 |
| To Hex | Converts string to hexadecimal |
| To Decimal | Converts input data to ordinal integer array |
| ROT13 | Caesar substitution cipher which rotates characters by specified amount (default is 13) |

#### Q1: In which area can you find "From Base64"?
<pre>Operations</pre>
- Located on left side of CyberChef webpage.
<br>

#### Q2: Which area is considers the heart of the tool?
<pre>Recipe</pre>

## Task 4: Before Anything Else
Thought process of using CyberChef:
Step 1: Set a clear objective.
Step 2: Put data into input area.
Step 3: Select Operations you might want to use.
Step 4: Check output if intended result. Hence repeat process from step 1 or 3.

#### Q1: At which step would you determine, "What do I want to accomplish?"
<pre>1</pre>
- Step 1 is to set a clear objective - what you want to accomplish.

## Task 5: Practice, Practice, Practice
- Recognize which category to utilize to use CyberChef efficiently and effectively.
- Below are categories.

### Extractors
- Extract IP addresses.
- Extract URLs.
- Extract email addresses

### Date and Time
- From UNIX Timestamp
  - Converts from datetime string.
- To UNIX Timestamp
  - UNIX is less readable.

### Data Format
- From Base64
- URL Decode
- From Base85
- From Base58
- To Base62

Download the task files associated with this task to answer the questions below using CyberChef.

#### Q1: What is the hidden email address?
<pre>hidden@hotmail.com</pre>
- Use the **Extract email addresses** operation to extract the email from the input data.
<br>

#### Q2: What is the hidden IP address that ends in .232?
<pre>102.20.11.232</pre>
- Use the **Extract IP addresses** operation to extract IP addresses from the input data and select IP ending in .232.
<br>

#### Q3: Which domain address starts with the letter "T"?
<pre>TryHackMe.com</pre>
- Use the **Extract domains** operation to extract domains from input data and select domain that starts with "T".
<br>

#### Q4: What is the binary value of the decimal number 78?
<pre>01001110</pre>
- Use the **From Decimal** and **To Binary** operations to convert decimal 78 to binary.
- By default when you enter 78 as the input data, its not formatted as decimal.
<br>

#### Q5: What is the URL encoded value of https://tryhackme.com/r/careers?
<pre>https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Fcareers</pre>
- Use the **URL Encode** operation and check the box **Encode all special characters** to encode the given URL.
<br>

## Task 6: Your First Official Cook

#### Q1: Using the file you downloaded in Task 5, which IP starts and ends with "10"?
<pre>10.10.2.10</pre>
- Use the **Extract IP addresses** operation extract IP from input and find the IP that ends with 10.
<br>

#### Q2: What is the base64 encoded value of the string "**Nice Room!**"?
<pre>TmljZSBSb29tIQ==</pre>
- Use the **To Base64** operation to encode the string into base64.
<br>

#### Q3: What is the URL decoded value for ```https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics```?
<pre>https://tryhackme.com/r/room/cyberchefbasics</pre>
- Use the **URL Decode** operation to decode the encoded URL.
<br>

#### Q4: What is the datetime string for the Unix timestamp ```1725151258```?
<pre>Sun 1 September 2024 00:40:58 UTC</pre>
- Use the **From UNIX Timestamp** to convert the Unix timestamp to datetime string.
<br>

#### Q5: What is the Base85 decoded string of the value ```<+oue+DGm>Ap%u7```?
<pre>This is fun!</pre>
- Use the **From Base85** operation to decode the given string.
<br>
