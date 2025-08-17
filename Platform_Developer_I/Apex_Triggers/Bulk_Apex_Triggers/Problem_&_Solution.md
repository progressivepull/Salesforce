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

``` apex
trigger ClosedOpportunityTrigger on Opportunity (after insert, after update) {
    List<Task> tasksToCreate = new List<Task>();

    for (Opportunity opp : Trigger.new) {
        // Only process if StageName is 'Closed Won' AND it was not 'Closed Won' before
        if (opp.StageName == 'Closed Won') {
            // For after update, check that the Stage actually changed to avoid redundant tasks
            if (Trigger.isInsert || 
               (Trigger.isUpdate && Trigger.oldMap.get(opp.Id).StageName != 'Closed Won')) {

                Task followUpTask = new Task(
                    Subject = 'Follow Up Test Task',
                    WhatId = opp.Id
                );
                tasksToCreate.add(followUpTask);
            }
        }
    }

    if (!tasksToCreate.isEmpty()) {
        insert tasksToCreate;
    }
}

```

# 🧠 Key Notes:

* ✅ Bulkified to handle up to 200+ records by avoiding DML inside loops.

* 🧠 Handles both insert and update events.

* 🛡️ Prevents duplicate tasks on update by checking the previous StageName using Trigger.oldMap.

* 🔗 Associates each task with its corresponding Opportunity using WhatId.

Want to add an Owner assignment or a follow-up date? You can easily extend it with more fields like OwnerId, DueDate, or Status.

