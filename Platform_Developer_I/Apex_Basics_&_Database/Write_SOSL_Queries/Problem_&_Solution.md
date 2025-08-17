# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex class that returns both contacts and leads based on a parameter.**

To pass this challenge, create an Apex class that returns both contacts and leads that have first or last name matching the incoming parameter.


* The Apex class must be called **ContactAndLeadSearch** and be in the public scope
* The Apex class must have a public static method called **searchContactsAndLeads**
    - The method must accept an incoming string as a parameter
    - The method should then find any contact or lead whose first or last name match the string
    - The method should finally use a return type of **List<List< sObject>>**
* **NOTE:** Because SOSL indexes data for searching, you must create a Contact record and Lead record before checking this challenge. Both records must have the last name **Smith**. The challenge uses these records for the SOSL search


# Solution

``` apex
public class ContactAndLeadSearch {
    public static List<List<sObject>> searchContactsAndLeads(String searchString) {
        List<List<sObject>> searchResults = [
            FIND :searchString
            IN Name Fields
            RETURNING Contact(Id, FirstName, LastName), Lead(Id, FirstName, LastName)
        ];
        return searchResults;
    }
}

```

# 🔍 Breakdown:
* Class Name: ContactAndLeadSearch — declared as public.

* Method Name: searchContactsAndLeads — public static.

* Parameter: A single String called searchString, used in the SOSL FIND.

* Return Type: List<List<sObject>> — SOSL returns a list of lists, one per object type (e.g., Contacts and Leads).

* SOSL Query:

     - Searches in the Name fields (FirstName, LastName) of both Contact and Lead.

     - Retrieves only Id, FirstName, and LastName as requested.

✅ To pass the challenge, make sure you’ve manually added a **Contact** and a Lead with the last name **Smith** in your org before testing. Salesforce indexing requires existing records for SOSL to yield results.