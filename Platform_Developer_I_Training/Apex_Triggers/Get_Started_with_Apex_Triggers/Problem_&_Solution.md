# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex trigger**

Create an Apex trigger that sets an account’s Shipping Postal Code to match the Billing Postal Code if the Match Billing Address option is selected. Fire the trigger before inserting an account or updating an account.

**Pre-Work:**
Add a checkbox field to the Account object:

    - Field Label: Match Billing Address
    - Field Name: Match_Billing_Address
    Note: The resulting API Name should be Match_Billing_Address__c.

* Create an Apex trigger:
    - Name: AccountAddressTrigger
    - Object: Account
    - Events: before insert and before update
    - Condition: Match Billing Address is true
    - Operation: set the Shipping Postal Code to match the Billing Postal Code


# Solution

[Get Started with Apex Triggers || Apex Triggers || Salesforce Supported Virtual Internship 2024](https://www.youtube.com/watch?v=WoryKz-jOFo)

``` apex
trigger AccountAddressTrigger on Account (before insert, before update) {
    for (Account acc : Trigger.new) {
        if (acc.Match_Billing_Address__c == true && acc.BillingPostalCode != null) {
            acc.ShippingPostalCode = acc.BillingPostalCode;
        }
    }
}

```

# ✅ Highlights:

* Events: Executes on before insert and before update, ensuring postal code adjustment before the record is saved.

* Condition: Checks if Match_Billing_Address__c is selected (true).

* Operation: Sets ShippingPostalCode to match BillingPostalCode.

* Bulkified: Uses a for loop over Trigger.new to handle many records efficiently.

If you’re planning to test it, try inserting or updating a few Account records with different address combinations and toggle the checkbox. Want to add similar logic for other fields like street or city?

# Error
We updated an account that had 'Match_Billing_Address__c' set to true. We expected the trigger to fire, but it didn’t. Make sure the trigger fires if 'Match_Billing_Address__c' is true.

DID But Do not think get do this: General Options -> Default Value -> Checked

My apex code was not saved

