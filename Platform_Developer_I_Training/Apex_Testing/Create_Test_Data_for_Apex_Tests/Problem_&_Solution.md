# Problems

**Create a Contact Test Factory**

Create an Apex class that returns a list of contacts based on two incoming parameters: the number of contacts to generate and the last name, which is common to all contacts. Do not insert the generated contact records into the database.

NOTE: For the purposes of verifying this hands-on challenge, don't specify the @isTest annotation for either the class or the method, even though it's usually required.

* Create an Apex class in the **public** scope
    - Name: **RandomContactFactory** (without the @isTest annotation)
* Use a Public Static Method to consistently generate contacts with unique first names based on the iterated number in the format Test 0, Test 1, and so on
    - Method Name: **generateRandomContacts** (without the @isTest annotation)
    - Parameter 1: An integer that controls the number of contacts being generated with unique first names, such as Test 0 and Test 1
    - Parameter 2: A string containing the common last name of the contacts
    - Return Type: **List<Contact>**


# Solution

Here’s a clean implementation of the **RandomContactFactory** Apex class that matches all your challenge requirements:

# 📄 Apex Class: RandomContactFactory

``` apex
public class RandomContactFactory {
    public static List<Contact> generateRandomContacts(Integer count, String lastName) {
        List<Contact> contacts = new List<Contact>();

        for (Integer i = 0; i < count; i++) {
            Contact c = new Contact(
                FirstName = 'Test ' + i,
                LastName = lastName
            );
            contacts.add(c);
        }

        return contacts;
    }
}
```
# ✅ What It Does
* Public scope class with a static method

* Accepts:

    - count: how many contacts to generate

    - lastName: shared across all contacts

* Generates Contact objects with unique first names like "Test 0", "Test 1", etc.

* Does not insert any records into the database