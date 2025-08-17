# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Record-Triggered Flow**

Create a record-triggered flow that creates a task for a high-value opportunity owner when negotiation begins.

* Create a record-triggered flow:
    - Object: Opportunity
    - Trigger the Flow When: A record is created or updated
    - Condition Requirements: All Conditions Are Met (AND)
        - First condition:
            - Field: Stage
            - Operator: Equals
            - Value: Negotiation/Review
        - Second condition:
           - Field: Amount
           - Operator: Greater Than
           - Value: 100000
    - When to Run the Flow for Updated Records: Only when a record is updated to meet the condition requirements
    - Optimize the Flow for: choose the option that allows you to create records
* Add a Create Records element to your flow:
    - Label: Create Email Task
    - API Name: Create_Email_Task
    - Description: Create a task for the opportunity owner to send a follow email to the account owner today (we won’t check the actual text)
    - How to set record field values: choose the option that allows you to reference records other than the record that triggered the flow
    - Object: Task
    - Field values:
        - Field: Subject, Value: Follow up with the account owner by email (we won’t check the actual text)
        - Field: Due Date Only, Value: enter today’s date (we’ll only check that you entered a date; it could be any date)
        - Field: Assigned To ID, Value: Triggering Opportunity > Owner ID (choose the Owner ID that doesn’t have a > at the end of the line)
        - Field: Related To ID, Value: Triggering Opportunity > Account ID (choose the Account ID that doesn’t have a > at the end of the line)
* Save your flow:
    - Flow Label: Review Opportunity with Account Owner
    - Flow API Name: Review_Opportunity_with_Account_Owner
    - Description: When a high-value opportunity is ready for negotiation and review, create a task for the owner to follow up with the account owner (We won’t check the actual text)


# Solution

# 🛠️ Step-by-Step Flow Configuration

**1. Flow Setup**

* Type: Record-Triggered Flow
* Object: Opportunity
* Trigger: A record is created or updated
* Condition Logic: All Conditions Are Met (AND)
    - Stage = Negotiation/Review
    - Amount > 100000
* Run for Updated Records: Only when a record is updated to meet the condition requirements
* Optimize the Flow for: Actions and Related Records (this allows creating records)

**2. Create Records Element**

* Label: Create Email Task
* API Name: Create_Email_Task
* Description: Create a task for the opportunity owner to send a follow-up email today
* Object: Task
* How to Set Field Values: Use separate resources and literal values (allows referencing other records)
  

| **Field**         | **Value**                                                   |
|-------------------|-------------------------------------------------------------|
| Subject           | Follow up with the account owner by email                   |
| Due Date Only     | Any valid date (e.g., `TODAY` function or system date)      |
| Assigned To ID    | `Opportunity.Owner ID` (without the `>` suffix)             |
| Related To ID     | `Opportunity.Account ID` (again, without the `>` suffix)    |

# 💾 Final Flow Metadata

* Flow Label: Review Opportunity with Account Owner
* Flow API Name: Review_Opportunity_with_Account_Owner
* Description: Create a task for the Opportunity Owner to follow up with the Account Owner