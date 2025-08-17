# Problems

**Create a Unit Test for a Simple Apex Trigger**

Create a simple Apex trigger which blocks inserts and updates to any contact with a last name of 'INVALIDNAME'. You'll copy the code for the class from the Get Ready for the Hands-on Challenge section. Then write unit tests that achieve 100% code coverage.


* Create an Apex trigger on the Contact object
    - Name: **RestrictContactByName**
    - Code: **Copy from Get Ready for the Hands-on Challenge section above**
* Place the unit tests in a separate test class
    - Name: **TestRestrictContactByName**
    - Goal: 100% test coverage
* Run your test class at least once


# Solution

# 📛 Apex Trigger: RestrictContactByName

``` apex
trigger RestrictContactByName on Contact (before insert, before update) {
    for (Contact c : Trigger.new) {
        if (c.LastName == 'INVALIDNAME') {
            c.addError('The Last Name "INVALIDNAME" is not allowed.');
        }
    }
}
```
* The trigger runs before insert and update, and adds an error to any contact with the last name 'INVALIDNAME'.

# 🧪 Unit Test Class: TestRestrictContactByName

``` apex
@isTest
public class TestRestrictContactByName {
    @isTest
    static void testInsertInvalidName() {
        Contact c = new Contact(
            FirstName = 'Test',
            LastName = 'INVALIDNAME'
        );
        Test.startTest();
        try {
            insert c;
            System.assert(false, 'Expected error was not thrown.');
        } catch (DmlException e) {
            System.assert(e.getMessage().contains('INVALIDNAME'), 'Error message should mention INVALIDNAME');
        }
        Test.stopTest();
    }

    @isTest
    static void testUpdateInvalidName() {
        Contact c = new Contact(
            FirstName = 'Test',
            LastName = 'ValidName'
        );
        insert c;

        c.LastName = 'INVALIDNAME';
        Test.startTest();
        try {
            update c;
            System.assert(false, 'Expected error was not thrown on update.');
        } catch (DmlException e) {
            System.assert(e.getMessage().contains('INVALIDNAME'), 'Error message should mention INVALIDNAME');
        }
        Test.stopTest();
    }

    @isTest
    static void testValidInsertAndUpdate() {
        Contact c = new Contact(
            FirstName = 'Test',
            LastName = 'ValidName'
        );
        insert c;

        c.LastName = 'AnotherValidName';
        update c;

        System.assertEquals('AnotherValidName', [SELECT LastName FROM Contact WHERE Id = :c.Id].LastName);
    }
}
```

# ✅ Achievements
* Tests insert, update, and valid paths for complete logic coverage

* Triggered error verified through DmlException

* Ensures 100% code coverage