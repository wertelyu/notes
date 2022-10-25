# api

[API medium](https://medium.com/@perrysetgo/what-exactly-is-an-api-69f36968a41f)

API - a publicly available web-based API that returns data, likely in JSON or XML. The API is not the database or even the server, it is the code that governs the access point(s) for the server.
It does not generally need to contain a frontend — no HTML, CSS.

## api gateways

Gateways help protect your API's from DDoS and Brute force attacks. 
API Gateways will do authentication and authorization for you.
API Gateways get abused by attackers.

## logging monitoring alerting

How else can you protect yourself from your API's being abused and manipulated? 
It's chipper
for obvious reason

## Block HTTP Methods and Commands

I'm gonna talk dirty to your API's.

Who are you talking to?

## API top 10

API1:2019 Broken Object Level Authorization

    This may lead to unauthorized access to sensitive data. This issue is extremely common in API-based applications because the server component usually does not fully track the client’s state, and instead, relies more on parameters like object IDs, that are sent from the client to decide which objects to access.

    Unauthorized access can result in data disclosure to unauthorized parties, data loss, or data manipulation. Unauthorized access to objects can also lead to full account takeover.

API2:2019 Broken User Authentication
    
    Attackers can gain control to other users’ accounts in the system, read their personal data, and perform sensitive actions on their behalf, like money transactions and sending personal messages.

API3:2019 Excessive Data Exposure

API4:2019 Lack of Resources & Rate Limiting

    Exploitation requires simple API requests. No authentication is required. Multiple concurrent requests can be performed from a single local computer or by using cloud computing resources.

    Exploitation may lead to DoS, making the API unresponsive or even unavailable.

    API requests consume resources such as network, CPU, memory, and storage. 

API5:2019 Broken Function Level Authorization

    Such flaws allow attackers to access unauthorized functionality. 

API6:2019 Mass Assignment

API7:2019 Security Misconfiguration
    
    Attackers will often attempt to find unpatched flaws, common endpoints, or unprotected files and directories to gain unauthorized access or knowledge of the system.

    Security misconfigurations can not only expose sensitive user data, but also system details that may lead to full server compromise.

API8:2019 Injection
    
    Attackers will feed the API with malicious data through whatever injection vectors are available (e.g., direct input, parameters, integrated services, etc.), expecting it to be sent to an interpreter.
    Injection flaws are very common and are often found in SQL, LDAP, or NoSQL queries, OS commands, XML parsers, and ORM. 

    Injection can lead to information disclosure and data loss. It may also lead to DoS, or complete host takeover.

    API is vulnerable if:

    - Client-supplied data is not validated, filtered, or sanitized by the API.
    - Client-supplied data is directly used or concatenated to SQL/NoSQL/LDAP queries, OS commands, XML parsers, and Object Relational Mapping (ORM)/Object Document Mapper (ODM).
    - Data coming from external systems (e.g., integrated systems) is not validated, filtered, or sanitized by the API.

API9:2019 Improper Assets Management

    Old API versions are usually unpatched and are an easy way to compromise systems without having to fight.
    Attackers may gain access to sensitive data, or even takeover the server through old, unpatched API versions connected to the same database.

API10:2019 Insufficient Logging & Monitoring

    Attackers take advantage of lack of logging and monitoring to abuse systems without being noticed.
    Without visibility over on-going malicious activities, attackers have plenty of time to fully compromise systems.

### TODO

ffuf - u http://<>/FUZZ -w /usr/share/worldlists/dirb/common.txt
ffuf - u http://<>/api/FUZZ -w /usr/share/worldlists/dirb/common.txt
