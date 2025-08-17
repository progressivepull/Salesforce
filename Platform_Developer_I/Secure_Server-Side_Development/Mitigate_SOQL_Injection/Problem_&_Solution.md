# Problems & Solution

# 1 How can SOQL injection occur in a Salesforce application?

A By executing DML operations

B By using the WITH SECURITY_ENFORCED clause in SOQL queries

C By trusting user input and incorrectly handling it in the SOQL query

D By chaining multiple queries together

## ANSWER

# ✅ 1. How can SOQL injection occur in a Salesforce application?

**Correct Answer: C – By trusting user input and incorrectly handling it in the SOQL query**

* SOQL injection can happen when user input is directly concatenated into a query string without validation or sanitization.

* This allows attackers to manipulate the structure or logic of the query to access unauthorized data or perform unintended actions.


# 2 What technique is recommended to prevent SOQL injection attacks when using dynamic queries?

A Static queries with bind variables

B Replacing characters in the user input

C Escaping single quotes using string.escapeSingleQuotes()

D Implementing allowlisting for user input

## ANSWER

# ✅ 2. What technique is recommended to prevent SOQL injection attacks when using dynamic queries?

**Correct Answer: A – Static queries with bind variables**

* Bind variables are the safest way to construct dynamic SOQL.

* They ensure user input is treated as a literal value, not executable query logic—effectively neutralizing injection risks.