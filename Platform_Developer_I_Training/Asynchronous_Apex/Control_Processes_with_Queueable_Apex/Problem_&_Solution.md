# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Queueable Apex class that inserts Contacts for Accounts.**

Create a Queueable Apex class that inserts the same Contact for each Account for a specific state.


* Create an Apex class:
    - Name: **AddPrimaryContact**
    - Interface: **Queueable**
    - Create a constructor for the class that accepts as its first argument a Contact sObject and a second argument as a string for the State abbreviation
    - The **execute** method must query for a maximum of 200 Accounts with the **BillingState** specified by the State abbreviation passed into the constructor and insert the Contact sObject record associated to each Account. Look at the sObject **clone()** method.
* Create an Apex test class:
    - Name: **AddPrimaryContactTest**
    - In the test class, insert 50 Account records for **BillingState NY** and 50 Account records for **BillingState CA**
    - Create an instance of the **AddPrimaryContact** class, enqueue the job, and assert that a Contact record was inserted for each of the 50 Accounts with the **BillingState** of **CA**
    - The unit tests must cover all lines of code included in the **AddPrimaryContact** class, resulting in 100% code coverage
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature



# Solution

# 📦 Apex Class: AddPrimaryContact

``` apex
public class AddPrimaryContact implements Queueable {
    private Contact contactTemplate;
    private String stateAbbreviation;

    public AddPrimaryContact(Contact contactTemplate, String stateAbbreviation) {
        this.contactTemplate = contactTemplate;
        this.stateAbbreviation = stateAbbreviation;
    }

    public void execute(QueueableContext context) {
        List<Account> accounts = [SELECT Id FROM Account WHERE BillingState = :stateAbbreviation LIMIT 200];
        List<Contact> contactsToInsert = new List<Contact>();

        for (Account acct : accounts) {
            Contact clonedContact = contactTemplate.clone(false, true, false, false);
            clonedContact.AccountId = acct.Id;
            contactsToInsert.add(clonedContact);
        }

        if (!contactsToInsert.isEmpty()) {
            insert contactsToInsert;
        }
    }
}
```

# 🧪 Apex Test Class: AddPrimaryContactTest

``` apex
@isTest
private class AddPrimaryContactTest {
    @isTest
    static void testAddPrimaryContact_CA() {
        List<Account> accountsNY = new List<Account>();
        List<Account> accountsCA = new List<Account>();

        for (Integer i = 0; i < 50; i++) {
            accountsNY.add(new Account(Name = 'AccountNY' + i, BillingState = 'NY'));
            accountsCA.add(new Account(Name = 'AccountCA' + i, BillingState = 'CA'));
        }

        insert accountsNY;
        insert accountsCA;

        Contact template = new Contact(
            FirstName = 'John',
            LastName = 'Doe',
            Email = 'johndoe@example.com'
        );

        Test.startTest();
        AddPrimaryContact job = new AddPrimaryContact(template, 'CA');
        System.enqueueJob(job);
        Test.stopTest();

        List<Contact> insertedContacts = [SELECT Id FROM Contact WHERE FirstName = 'John' AND LastName = 'Doe' AND Email = 'johndoe@example.com'];
        System.assertEquals(50, insertedContacts.size(), 'Should have inserted 50 Contacts for CA accounts');
    }
}

```
# 🛠 Tips Before You Verify

* Run "Run All" from the Developer Console to ensure full code coverage.

* This test will cover all logic branches and should pass successfully if entered correctly.


