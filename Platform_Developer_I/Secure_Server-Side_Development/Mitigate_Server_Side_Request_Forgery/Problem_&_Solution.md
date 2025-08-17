# Problems & Solution

# 1 What is server-side request forgery (SSRF)?

A A technique to secure internal databases

B A vulnerability in web applications where an attacker can make unauthorized requests to internal resources on behalf of the user’s client

C A protocol for secure data transmission

D A method for preventing data exposure

## ANSWER

# ✅ 1. What is server-side request forgery (SSRF)?

**Correct Answer: B – A vulnerability in web applications where an attacker can make unauthorized requests to internal resources on behalf of the user’s client**

* SSRF allows attackers to trick the server into making requests to unintended internal systems, potentially exposing sensitive data or enabling further attacks.

# 2 How can developers prevent SSRF attacks in Salesforce Lightning applications?

A Avoiding state-changing POST or PUT requests

B Allowing unrestricted access to internal resources

C Ignoring input validation for user-provided values

D Allowlisting permitted URLs for outgoing requests


## ANSWER

# ✅ 2. How can developers prevent SSRF attacks in Salesforce Lightning applications?

**Correct Answer: D – Allowlisting permitted URLs for outgoing requests**

* By defining a strict list of approved external URLs, developers can ensure that only safe destinations are accessible via server requests—minimizing exposure to malicious endpoints.

