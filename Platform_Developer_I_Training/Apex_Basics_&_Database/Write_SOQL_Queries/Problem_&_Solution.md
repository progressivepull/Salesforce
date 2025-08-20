# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex class that returns contacts based on incoming parameters.**


For this challenge, you will need to create a class that has a method accepting two strings. The method searches for contacts that have a last name matching the first string and a mailing postal code matching the second. It gets the ID and Name of those contacts and returns them.


* The Apex class must be called ContactSearch and be in the public scope
* The Apex class must have a public static method called searchForContacts
    - The method must accept two incoming strings as parameters
    - The method should then find any contact that has a last name matching the first string, and mailing postal code (API name: MailingPostalCode) matching the second string
    - The method should finally return a list of Contact records of type List that includes the ID and Name fields


# Solution

``` apex
public class ContactSearch {
    public static List<Contact> searchForContacts(String lastName, String postalCode) {
        List<Contact> matchedContacts = [
            SELECT Id, Name
            FROM Contact
            WHERE LastName = :lastName AND MailingPostalCode = :postalCode
        ];
        return matchedContacts;
    }
}
``` 

# ✅ Breakdown:

* Class Name: ContactSearch – public scope.

* Method Name: searchForContacts – public static.

* Parameters: Two String inputs for lastName and postalCode.

* Query: Uses a SOQL query to find contacts whose LastName and MailingPostalCode match the incoming values.

* Return: A list of Contact records with only Id and Name fields fetched.