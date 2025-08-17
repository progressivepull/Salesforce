# Problems & Solution

# 1 How can developers prevent CSRF attacks in their Salesforce Lightning applications?

A By avoiding the use of POST or PUT requests

B By relying solely on the default Salesforce CSRF tokens

C By using HTTP GET requests with state-changing parameters

D By validating the origin header and implementing anti-CSRF tokens

# ✅ 1. How can developers prevent CSRF attacks in their Salesforce Lightning applications?

**Correct Answer: D – By validating the origin header and implementing anti-CSRF tokens**

* CSRF (Cross-Site Request Forgery) attacks trick users into unknowingly submitting requests to a server.

* Validating the origin/header and using anti-CSRF tokens in server requests is a standard way to protect applications from these attacks.

## ANSWER

#  2 When is a Lightning page vulnerable to CSRF?

A When it uses POST or PUT requests for server-side operations

B When server-side DML operations are executed automatically as part of a page-loading event

C When it does not include anti-CSRF tokens in XMLHttpRequests

D When it does not implement allowlisting for Lightning components

## ANSWER

# ✅ 2. When is a Lightning page vulnerable to CSRF?

**Correct Answer: D – When server-side DML operations are executed automatically as part of a page-loading event**

* Without CSRF tokens, malicious third-party sites could perform unauthorized actions by leveraging a user’s authenticated session.

* Salesforce includes protections like CSRF tokens in its Lightning framework, but developers must ensure they’re implemented correctly during custom XMLHttpRequests.



