# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex class that uses the @future annotation to update Account records.**

Create an Apex class with a future method that accepts a List of Account IDs and updates a custom field on the Account object with the number of contacts associated to the Account. Write unit tests that achieve 100% code coverage for the class. Every hands-on challenge in this module asks you to create a test class.


* Create a field on the Account object:
    - Label: Number Of Contacts
    - Name: Number_Of_Contacts
    - Type: Number
    - This field will hold the total number of Contacts for the Account
* Create an Apex class:
    - Name: AccountProcessor
    - Method name: countContacts
    - The method must accept a List of Account IDs
    - The method must use the @future annotation
    - The method counts the number of Contact records associated to each Account ID passed to the method and updates the 'Number_Of_Contacts__c' field with this value
* Create an Apex test class:
    - Name: AccountProcessorTest
    - The unit tests must cover all lines of code included in the AccountProcessor class, resulting in 100% code coverage.
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature


# Solution

Here’s a complete solution using the **@future** annotation to update **Account.Number_Of_Contacts__c** with the count of related **Contact** records. This includes both the Apex class and a test class that achieves 100% code coverage.

# 🧮 Apex Class: AccountProcessor

``` apex
public class AccountProcessor {
    @future
    public static void countContacts(List<Id> accountIds) {
        Map<Id, Integer> contactCounts = new Map<Id, Integer>();

        for (AggregateResult ar : [
            SELECT AccountId, COUNT(Id) contactCount
            FROM Contact
            WHERE AccountId IN :accountIds
            GROUP BY AccountId
        ]) {
            contactCounts.put((Id)ar.get('AccountId'), (Integer)ar.get('contactCount'));
        }

        List<Account> accountsToUpdate = new List<Account>();

        for (Id acctId : accountIds) {
            Integer count = contactCounts.containsKey(acctId) ? contactCounts.get(acctId) : 0;
            accountsToUpdate.add(new Account(Id = acctId, Number_Of_Contacts__c = count));
        }

        if (!accountsToUpdate.isEmpty()) {
            update accountsToUpdate;
        }
    }
}

```
# 🧪 Apex Test Class: AccountProcessorTest

``` apex
@isTest
private class AccountProcessorTest {
    @isTest
    static void testCountContacts() {
        Account acct1 = new Account(Name = 'Test Account 1');
        Account acct2 = new Account(Name = 'Test Account 2');
        insert new List<Account>{acct1, acct2};

        Contact c1 = new Contact(FirstName = 'Ana', LastName = 'Bell', AccountId = acct1.Id);
        Contact c2 = new Contact(FirstName = 'John', LastName = 'Doe', AccountId = acct1.Id);
        Contact c3 = new Contact(FirstName = 'Lia', LastName = 'Kim', AccountId = acct2.Id);
        insert new List<Contact>{c1, c2, c3};

        Test.startTest();
        AccountProcessor.countContacts(new List<Id>{acct1.Id, acct2.Id});
        Test.stopTest();

        List<Account> updatedAccounts = [SELECT Id, Number_Of_Contacts__c FROM Account WHERE Id IN :new List<Id>{acct1.Id, acct2.Id}];
        for (Account a : updatedAccounts) {
            if (a.Id == acct1.Id) {
                System.assertEquals(2, a.Number_Of_Contacts__c);
            } else if (a.Id == acct2.Id) {
                System.assertEquals(1, a.Number_Of_Contacts__c);
            }
        }
    }
}

```

# 🔎 Heads-Up Before Verification
* Run "Run All" from Developer Console to confirm 100% coverage.

* Ensure the custom field Number_Of_Contacts__c exists in your org.

* If the future method doesn’t seem to execute during testing, remember it will run after Test.stopTest().