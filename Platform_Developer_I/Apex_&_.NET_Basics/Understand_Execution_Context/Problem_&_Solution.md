# Problem
**Write an Apex trigger that modifies Account fields before inserting records.**      

Write an Apex trigger that fires before records are inserted and ensures that the ShippingState field has the same value as the BillingState field.          


* Create an Apex class that contains a public static method:
    - Name: AccountTriggerHandler
    - Method name: CreateAccounts
    - The method must accept a List of Account objects
    - For each Account record, before saving, update the the ShippingState field to have the same value as the BillingState field
* Create an Apex Trigger:
    - Name: AccountTrigger
    - sObject: Account
    - Fires: before records are inserted
    - Your trigger must call the AccountTriggerHandler.CreateAccounts() method with the collection of new records
    - Use the isBefore and isInsert trigger context variables
* Create a test class:
    - Name: AccountTriggerTest
    - Your test class must insert 200 Account records with a BillingState of CA
    - After the insert, test to ensure that all 200 records have a ShippingState of CA
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature

# Solution 
These files provide:

* A trigger handler class (AccountTriggerHandler) with a static method to update ShippingState
* An Apex Trigger (AccountTrigger) that fires before insert, using the handler
* A test class (AccountTriggerTest) that inserts 200 accounts and verifies the logic

AccountTriggerHandler.cls

``` apex
public class AccountTriggerHandler {
    /**
     * Ensures each Account's ShippingState is set to the BillingState.
     * @param newAccounts List of new Account records to process before insert.
     */
    public static void CreateAccounts(List<Account> newAccounts) {
        for (Account acc : newAccounts) {
            acc.ShippingState = acc.BillingState;
        }
    }
}
```

AccountTrigger.trigger

``` apex
trigger AccountTrigger on Account (before insert) {
    if (Trigger.isBefore && Trigger.isInsert) {
        AccountTriggerHandler.CreateAccounts(Trigger.new);
    }
}
``` 

AccountTriggerTest.cls 
``` apex
@isTest
public class AccountTriggerTest {
    @isTest
    static void testShippingStateMatchesBillingState() {
        List<Account> accountsToInsert = new List<Account>();
        for (Integer i = 0; i < 200; i++) {
            accountsToInsert.add(new Account(
                Name = 'Test Account ' + i,
                BillingState = 'CA'
            ));
        }
        insert accountsToInsert;
        // Query the inserted accounts
        List<Account> insertedAccounts = [SELECT Id, BillingState, ShippingState FROM Account WHERE BillingState = 'CA'];
        System.assertEquals(200, insertedAccounts.size(), 'Should have inserted 200 accounts');
        for (Account acc : insertedAccounts) {
            System.assertEquals('CA', acc.ShippingState, 'ShippingState should be set to CA');
        }
    }
}
```