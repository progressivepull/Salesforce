# Problems & Solution

# 1 What does a search for a single object look like in SOSL?

* A FIND {cloud} RETURNING Account
* B FIND in ACCOUNT RETURNING "cloud"
* C FIND "cloud" in ACCOUNT
* D FIND (cloud) RIGHT NOW!

## ANSWER

# Correct Answer: A FIND {cloud} RETURNING Account

* In SOSL, the syntax for searching a single object includes the FIND keyword with the search term in curly braces {} and the RETURNING keyword followed by the object name.

* Example: FIND {cloud} RETURNING Account searches for the term "cloud" in the Account object.

* Other options are incorrect because they do not follow the correct SOSL syntax.

# 2 How does a custom object search differ from other queries?

* A The name is in all caps.
* B It includes __c at the end of the object name.
* C In the query, you specify that an object is custom.
* D You surround the custom object name in quotes.

## ANSWER

# Correct Answer: B It includes __c at the end of the object name.

* Custom objects in Salesforce are identified by the __c suffix in their API names.

* For example, a custom object named "Invoice" would be referenced as Invoice__c in queries.

* The other options are incorrect because they do not reflect how Salesforce distinguishes custom objects.