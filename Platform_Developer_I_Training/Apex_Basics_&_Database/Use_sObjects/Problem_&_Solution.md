# Problems & Solution

# 1 Describe the relationship between sObjects and Salesforce records.

* A The name of an sObject field in Apex is the label of the field in Salesforce.
* B A custom object's API name and label are the same.
* C Every record in Salesforce is natively represented as an sObject in Apex.

## ANSWER

# Correct Answer: C Every record in Salesforce is natively represented as an sObject in Apex.

* In Apex, every Salesforce record (standard or custom) is represented as an sObject. For example, an Account record is represented as an Account sObject, and a custom object like Book__c is represented as a Book__c sObject.

* Option A is incorrect because the name of an sObject field in Apex corresponds to the API name, not the label.

* Option B is incorrect because a custom object's API name and label are not necessarily the same.


# 2 How do you create an sObject instance, such as an Account?

* A Declare a variable and assign a new sObject instance to it.
* B Use the sObject.newInstance() method.
* C Insert a persistent record into Salesforce using SOQL.

## ANSWER

# Correct Answer: A Declare a variable and assign a new sObject instance to it.

* You can create an sObject instance by declaring a variable and assigning it a new instance, such as Account acc = new Account();.

* Option B is incorrect because sObject.newInstance() is not a valid method in Apex.

* Option C is incorrect because SOQL is used for querying records, not for creating sObject instances.


# 3 Which of the following is correct about a generic sObject variable?

* A A generic sObject variable can be assigned only to another generic sObject.
* B Generic sObjects can't be created.
* C A generic sObject variable can be assigned to any specific standard or custom sObject, such as Account or Book__c, using casting.

## ANSWER

# Correct Answer: C A generic sObject variable can be assigned to any specific standard or custom sObject, such as Account or Book__c, using casting.

* A generic sObject variable is flexible and can hold any specific sObject type, such as Account or Book__c. You can cast it to a specific type when needed.

* Option A is incorrect because a generic sObject variable can be assigned to specific sObjects, not just other generic sObjects.

* Option B is incorrect because generic sObjects can indeed be created and used in Apex.