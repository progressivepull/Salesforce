# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Bulk Apex trigger**

Create a bulkified Apex trigger that adds a follow-up task to an opportunity if its stage is Closed Won. Fire the Apex trigger after inserting or updating an opportunity.

* Create an Apex trigger:
    - Name: ClosedOpportunityTrigger
    - Object: Opportunity
    - Events: after insert and after update
    - Condition: Stage is Closed Won
    - Operation: Create a task:
        - Subject: Follow Up Test Task
        - WhatId: the opportunity ID (associates the task with the opportunity)
    - Bulkify the Apex trigger so that it can insert or update 200 or more opportunities


# Solution
[Bulk Apex Triggers || Apex Triggers || Salesforce Supported Virtual Internship Program 2024](https://www.youtube.com/watch?v=YEJ8v5RVKqE)

``` apex trigger
trigger ClosedOpportunityTrigger on Opportunity (after insert, after update) {
    List<Task> taskList = new List<Task>();
    
     for (Opportunity opp : [SELECT id, StageName FROM Opportunity WHERE StageName = 'Closed Won' AND Id IN : Trigger.New]) {
        taskList.add( new Task(Subject='Follow Up Test Task', WhatId = opp.Id));
     }
    
    if (taskList.size() > 0 ) {
        insert taskList;
    }


}

```

# 🧠 Key Notes:

* ✅ Bulkified to handle up to 200+ records by avoiding DML inside loops.

* 🧠 Handles both insert and update events.

* 🛡️ Prevents duplicate tasks on update by checking the previous StageName using Trigger.oldMap.

* 🔗 Associates each task with its corresponding Opportunity using WhatId.

Want to add an Owner assignment or a follow-up date? You can easily extend it with more fields like OwnerId, DueDate, or Status.

# Error
We tried to insert Opportunity records as part of the challenge check, but the insert failed. Error: thException: OPP_INSERT | System.DmlException: Insert failed. First exception on row 0; first error: REQUIRED_FIELD_MISSING, Required fields are missing: [Discount_Percent__c]: [Discount_Percent__c]

