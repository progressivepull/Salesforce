# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an approval process**

Create an approval process to ensure that prospect accounts with more than 500 employees are approved before they’re converted to customers

**Before You Start**

Go to Object Manager. In Fields and Relationships for the Account object, check the Type field’s picklist values for **Prospect, Customer, and Pending**. Add any of these values that are missing.

**Use the Jump Start Wizard to create an approval process:**

* Manage Approval Processes For: Account
* Name: Approve New Account
* Unique Name: Approve_New_Account
* Approval Assignment Email Template: choose any template
* Entry Criteria:
    - Account: Type equals Prospect
    - Account: Employees is greater than 500
* Approver:
    - Automatically assign to approver(s)
    - User: assign yourself
* Add an initial submission action that updates fields:
    - Name: Account Type To Pending
    - Unique Name: Account_Type_To_Pending
    - Action: Update the Type field to Pending
* Add a final approval action that updates fields:
    - Name: Account Type To Customer
    - Unique Name: Account_Type_To_Customer
    - Action: Update the Type field to Customer
* Edit the existing final approval action:
    - Name: Record Lock
    - Action: Unlock the record for editing
* Add a final rejection action that updates fields:
    - Name: Account Type To Prospect
    - Unique Name: Account_Type_To_Prospect
    - Action: Update the Type field to Prospect
* Activate the approval process


# Solution

