# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

Salesforce approval process: an overview
The Salesforce Approval Process is an automated system for managing record approval workflows within your organization. It ensures that records meet predefined criteria and are reviewed and approved by the appropriate personnel before any further actions are taken.

## Key elements of a Salesforce Approval Process
* **Approval Steps:** These define the sequential stages records go through for approval. Each step can have its own criteria and assigned approvers.
* **Approvers:** These are the individuals or groups responsible for reviewing and making decisions on approval requests. Approvers can be assigned based on various factors, such as hierarchy, roles, or queues.
* **Entry Criteria:** Conditions a record must meet to initiate the approval process.
* **Actions:** Automated tasks that occur at different stages of the approval process. These include:

- **Initial Submission Actions:** Actions triggered when a record is first submitted for approval, like locking the record or sending notifications.
- **Approval Actions:** Actions triggered when a record is approved at a particular step, such as updating fields or creating tasks.
- **Rejection Actions:** Actions triggered when an approver rejects a request, like sending notifications or updating statuses.
- **Recall Actions:** Actions triggered when the submitter decides to withdraw the request before approval.

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

## References
* [Build an Approval Process || Approve Records with Approval Processes - Salesforce with shri - YouTube](https://www.youtube.com/watch?v=z5gfIR1EUpI)

 Here’s a full walkthrough based on what you’ve outlined, tailored for Salesforce setup using the Jump Start Wizard:

---

🛠 Step-by-Step Solution for Approval Process

🔎 Object Manager Setup
- Go to Setup → Object Manager → Account
- In Fields & Relationships, open the Type picklist
- Ensure the values Prospect, Customer, and Pending exist
- If any are missing, click New to add them

---

🚀 Create the Approval Process (Jump Start Wizard)
- Go to Setup → Approval Processes
- Select Manage Approval Processes For: Account
- Click Jump Start Wizard
- Name: Approve New Account
- Unique Name: ApproveNewAccount
- Approval Assignment Email Template: Select any template
- Entry Criteria:
- Account Type = Prospect
- Employees > 500
- Approver:
- Automatically assign to approver(s)
- User: Assign to yourself

---

📥 Initial Submission Action
- Name: Account Type To Pending
- Unique Name: AccountTypeTo_Pending
- Action Type: Field Update
- Field: Type
- New Value: Pending

---

✅ Final Approval Actions
1. Field Update
- Name: Account Type To Customer
- Unique Name: AccountTypeTo_Customer
- Field: Type → Value: Customer
2. Unlock Record for Editing
- Name: Record Lock
- Action Type: Unlock

---

❌ Final Rejection Action
- Name: Account Type To Prospect
- Unique Name: AccountTypeTo_Prospect
- Field Update: Set Type to Prospect

---

✅ Activate It
- Don’t forget to Activate the approval process to make it live!

---

This setup ensures your Account records follow a structured approval flow based on Type and employee count, with clear transitions between statuses. If you’re also adding notifications or want to customize layouts based on status, I can help jazz that up too.

Want a visual checklist or printable quick guide for this?

