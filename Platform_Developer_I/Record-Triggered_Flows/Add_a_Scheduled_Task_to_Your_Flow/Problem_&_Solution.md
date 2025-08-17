# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Add a Scheduled Path to Your Flow**

Create a scheduled path that waits until 3 days after an opportunity is changed and then creates a task for the opportunity owner.

* Add a scheduled path to a flow:
    - Flow: Review Opportunity with Account Owner
    - Path Label: 3 Days After Last Modified Date
    - API Name: X3_Days_After_Last_Modified_Date
    - Time Source: Opportunity: Last Modified Date
    - Offset Number: 3
    - Offset Option: Days After
* Add a Create Records element to the scheduled path:
    - Label: Create Phone Call Task
    - API Name: Create_Phone_Call_Task
    - Description: Create a task for the opportunity owner to check in with the customer by phone (we won’t check the actual text)
    - How to set record field values: choose the option that allows you to reference records other than the record that triggered the flow
    - Object: Task
    - Field values:
        - Field: Subject, Value: Outreach phone call (we won’t check the actual text)
        - Field: Description, Value: Call to check in with the customer (we won’t check the actual text)
        - Field: Due Date Only, Value: enter today’s date (we won't check the actual date, just that it's a valid date)
        - Field: Related To ID, Value: Triggering Opportunity > Opportunity ID
        - Field: Assigned To ID, Value: Triggering Opportunity > Owner ID (choose the Owner ID that doesn’t have a > at the end of the line)
* Save the flow

# Solution

# 🔄 Scheduled Path Configuration
**🧭 Add Scheduled Path**

* Flow: Review Opportunity with Account Owner
* Path Label: 3 Days After Last Modified Date
* API Name: X3_Days_After_Last_Modified_Date
* Time Source: Opportunity: Last Modified Date
* Offset Number: 3
* Offset Option: Days After

➕ This path will initiate 3 days after the opportunity record is updated—perfect for time-based follow-up automation.

# 📝 Create Task Element in Scheduled Path
**🔹 Element Details**

* Label: Create Phone Call Task
* API Name: Create_Phone_Call_Task
* Description: Task to check in with the customer via phone

# ⚙️ Task Configuration

| **Field**         | **Value**                                                        |
|-------------------|------------------------------------------------------------------|
| Subject           | Outreach phone call                                              |
| Description       | Call to check in with the customer                               |
| Due Date Only     | Any valid date (e.g., `TODAY()` function)                        |
| Assigned To ID    | `Opportunity.Owner ID` (no `>` suffix)                           |
| Related To ID     | `Opportunity.Opportunity ID` (no `>` suffix)                     |

* How to Set Field Values: Use separate resources and literal values — this allows referencing related records.


# 💾 Save Your Flow
Your scheduled path is now wired to automatically generate a phone call task 3 days after any qualifying opportunity update.

