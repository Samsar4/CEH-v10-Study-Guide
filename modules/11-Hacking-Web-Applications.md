# Hacking Web Applications

## <u>Web Organizations</u>

- **Internet Engineering Task Force (IETF)** - Creates engineering documents to help make the Internet work better.
- **World Wide Web Consortium (W3C)** - A standards-developing community.
- **Open Web Application Security Project (OWASP)** - Organization focused on improving the security of software.

## <u>OWASP Web Top 10</u>

![owasp](https://sdtimes.com/wp-content/uploads/2017/11/OWASP.png)

- **A1 - Injection Flaws** - SQL, OS and LDAP injection
- **A2 - Broken Authentication and Session Management** - functions related to authentication and session management that aren't implemented correctly
- **A3 - Sensitive Data Exposure** - not properly protecting sensitive data (SSN, CC  numbers, etc.)
- **A4 - XML External  Entities (XXE)** - exploiting XML  processors by uploading hostile content in an XML document
- **A5 - Broken Access Control** - having improper controls on areas that should be protected
- **A6 - Security Misconfiguration** - across all parts of the server and application
- **A7 - Cross-Site Scripting (XSS)** - taking untrusted data and sending it without input validation
- **A8 - Insecure Deserialization** - improperly de-serializing data
- **A9 - Using Components with Known Vulnerabilities** - libraries and frameworks that have known security holes
- **A10 - Insufficient Logging and Monitoring** - not having enough logging to detect attacks

**WebGoat** - project maintained by OWASP which is an insecure web application meant to be tested

## <u>Web Application Attacks</u>

- Most often hacked before of inherent weaknesses built into the program
- First step is to identify entry points (POST data, URL parameters, cookies, headers, etc.)
- **Tools for Identifying Entry Points**
  - WebScarab
  - HTTPPrint
  - BurpSuite
- **Web 2.0** - dynamic applications; have a larger attack surface due to simultaneous communication

### SQL Injection

Injecting SQL commands into input fields to produce output
  - Data Handling - Definition (DDL), manipulation (DML) and control (DCL)

SQL injection usually occurs when you ask a user for input, like their username/userid, and instead of a name/id, the user gives you an SQL statement that you will unknowingly run on your database.

**SQL Syntax - Basics:**

SQL Command | Info.
-- | :--
``SELECT`` | extracts data from a database
``UPDATE`` | updates data in a database
``DELETE`` | deletes data from a database
``INSERT INTO`` | inserts new data into a database
``ALTER TABLE`` | modifies a table
``DROP TABLE`` | deletes a table
``CREATE INDEX`` | creates an index (search key)
``DROP INDEX`` | deletes an index

---

### SQL Injection in action

- On the UserId input field, you can enter: 
    - `105 OR 1=1`.

- The is valid and will not return only UserId 105, this injection will return ALL rows from the "Users" table, **since OR 1=1 is always TRUE**. Then, the SQL statement will look like this:
    - `SELECT * FROM Users WHERE UserId = 105 OR 1=1;`

- Double dash (`--`) tells the server to ignore the rest of the query (in this example, the password check)

- `"' OR 1 = 1 --"` into a login field - basically tells the server **if 1 = 1 (always true)** to allow the login.

- Based on `=` is always true;
    - `" or ""="` --> The SQL above is valid and will return all rows from the "Users" table, since OR ""="" is always TRUE. 
    - This is valid and the SQL statement behind will look like this: ` SELECT * FROM Users WHERE Name ="John Doe" AND Pass ="myPass" `


- Basic test to see if SQL injection is possible is just inserting a single quote (`'`)

- **Fuzzing** - inputting random data into a target to see what will happen

- **Tautology** - using always true statements to test SQL (e.g. `1=1`)

- **In-band SQL injection** - uses same communication channel to perform attack

- Usually is when data pulled can fit into data exported (where data goes to a web table)

- Best for using UNION queries

- **Out-of-band SQL injection** - uses different communication channels (e.g. export results to file on web server)

- **Blind/inferential** - error messages and screen returns don't occur; usually have to guess whether command work or use timing to know

- **Tools**
    - Sqlmap
    - sqlninja
    - Havij
    - SQLBrute
    - Pangolin
    - SQLExec
    - Absinthe
    - BobCat

### RFI and LFI - Remote File Inclusion and Local File Inclusion 
**Remote File Inclusion (RFI)** is a method that allows an attacker to employ a script to include a remotely hosted file on the webserver. The vulnerability promoting RFI is largely found on websites running on PHP. This is because PHP supports the ability to ‘include’ or ‘require’ additional files within a script. 

**Local File Inclusion (LFI)** is very much similar to RFI. The only difference being that in LFI, in order to carry out the attack instead of including remote files, the attacker has to use local files i.e files on the current server can only be used to execute a malicious script.

### Directory Traversal
An attacker can get sensitive information like the contents of the /etc/passwd file that contains a list of users on the server; Log files, source code, access.log and so on

Example:
- `http://example.com/?file=../../../../etc/passwd`

### Command Injection
Attacker gains shell access using Java or similar

### LDAP Injection
Exploits applications that construct LDAP statements
  - Format for LDAP injection includes )(&)

### SOAP Injection
Inject query strings in order to bypass authentication
  - SOAP uses XML to format information
  - Messages are "one way" in nature

### Buffer Overflow** (Smashing the stack)
Attempts to write data into application's buffer area to overwrite adjacent memory, execute code or crash a system
  - Inputs more data than the buffer is allowed
  - Includes stack, heap, NOP sleds and more
  - **Canaries** - systems can monitor these - if they are changed, they indicate a buffer overflow has occurred; placed between buffer and control data

### XSS (Cross-site scripting)
Inputting JavaScript into a web form input field that alters what the page does.
  - Can also be passed via URL
  - Can be malicious by accessing cookies and sending them to a remote host
  - Can be mitigated by setting **HttpOnly** flag for cookies; But many hackers can circumvent this in order to execute XSS payloads.
  - **Stored XSS** (Persistent or Type-I) - stores the XSS in a forum or like for multiple people to access
  - **Reflected XSS** (or also called a non-persistent XSS); when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way. 

Examples of XSS payloads:
- `"><script>alert(1)</script>`
- `<svg/onload="alert(1);"`
- ```<svg/OnLoad="`${prompt``}`">```
- `p=<svg/1='&q='onload=alert(1)>`

*Note: they vary regarding the filtering, validation and WAF capabilities.*

### Cross-Site Request Forgery (CSRF)
Forces an end user to execute unwanted actions on an app they're already authenticated on
  - Inherits  identity and privileges of victim to perform an undesired function on victim's behalf
  - Captures the session and sends a request based off the logged in user's credentials
  - Can be mitigated by sending **random challenge tokens**

### Session Fixation
Attacker logs into a legitimate site and pulls a session ID; sends link with session ID to victim.  Once victim logs in, attacker can now log in and run with user's credentials

- **Cookies** - small text-based files stored that contains information like preferences, session details or shopping cart contents
  - Can be manipulated to change functionality (e.g. changing a cooking that says "ADMIN=no" to "yes")
  - Sometimes, but rarely, can also contain passwords

### HTTP Response Splitting
Adds header response data to an input field so server splits the response
  - Can be used to redirect a user to a malicious site
  - Is not an attack in and of itself - must be combined with another attack
 
### Countermeasures
Input scrubbing for injection, SQL parameterization for SQL injection, keeping patched servers, turning off unnecessary services, ports and protocols