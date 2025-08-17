# Problems

### Get Ready
You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

---

### Create a Validation Rule
Create a validation rule that displays an error message and prevents users from creating or updating a contact for an account if the contact and account have different zip codes. Allow creating and updating contacts that have no associated account.

---

* Create a validation rule:
   - **Rule Name:** `Contact_must_be_in_Account_ZIP_Code`
   - Operator: **AND** (return true if both conditions are true)
   - Define the two conditions that, combined, will show the error message:
        - The contact is associated with an account id
        - The contact mailing zip code is different than the account shipping zip code
Hint: Use the API names (**MailingPostalCode** and **Account.ShippingPostalCode**) and the <> **(Not Equal)** operator.
* Enter an error message for the validation rule


# Solution

Here’s how to create the validation rule as described:

**Object:** Contact
**Rule Name:** Contact_must_be_in_Account_ZIP_Code

Formula:

``` apex
AND(
    NOT(ISBLANK(AccountId)),
    MailingPostalCode <> Account.ShippingPostalCode
)
```

## Error Message:
Contact Mailing Zip Code must match the Account Shipping Zip Code.

## Explanation:

* The rule fires if the Contact is linked to an Account (AccountId is not blank) AND the Contact's Mailing Zip Code is different from the Account's Shipping Zip Code.
* Contacts with no Account can be created/updated.
* Enter the error message above in the Error Message field when creating the validation rule.