# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex class that uses Batch Apex to update Lead records.**

Create an Apex class that implements the Database.Batchable interface to update all Lead records in the org with a specific LeadSource.

* Create an Apex class:
    - Name: **LeadProcessor**
    - Interface: **Database.Batchable**
    - Use a QueryLocator in the start method to collect all Lead records in the org
    - The execute method must update all Lead records in the org with the LeadSource value of **Dreamforce**
* Create an Apex test class:
    - Name: **LeadProcessorTest**
    - In the test class, insert 200 Lead records, execute the **LeadProcessor** Batch class and test that all Lead records were updated correctly
    - The unit tests must cover all lines of code included in the **LeadProcessor** class, resulting in 100% code coverage
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature


# Solution

# 📦 Apex Class: LeadProcessor

``` apex
public class LeadProcessor implements Database.Batchable<SObject> {
    
    public Database.QueryLocator start(Database.BatchableContext bc) {
        return Database.getQueryLocator([SELECT Id, LeadSource FROM Lead]);
    }

    public void execute(Database.BatchableContext bc, List<SObject> scope) {
        List<Lead> leadsToUpdate = new List<Lead>();

        for (SObject s : scope) {
            Lead lead = (Lead)s;
            lead.LeadSource = 'Dreamforce';
            leadsToUpdate.add(lead);
        }

        if (!leadsToUpdate.isEmpty()) {
            update leadsToUpdate;
        }
    }

    public void finish(Database.BatchableContext bc) {
        // Optional: Add any post-processing logic or logging if needed
    }
}

```

# 🧪 Apex Test Class: LeadProcessorTest

``` apex
@isTest
private class LeadProcessorTest {
    @isTest
    static void testBatchLeadUpdate() {
        List<Lead> testLeads = new List<Lead>();

        for (Integer i = 0; i < 200; i++) {
            testLeads.add(new Lead(FirstName = 'Test', LastName = 'Lead' + i, Company = 'TestCorp'));
        }

        insert testLeads;

        Test.startTest();
        LeadProcessor processor = new LeadProcessor();
        Database.executeBatch(processor);
        Test.stopTest();

        List<Lead> updatedLeads = [SELECT LeadSource FROM Lead WHERE LeadSource = 'Dreamforce'];
        System.assertEquals(200, updatedLeads.size(), 'All 200 leads should have LeadSource set to Dreamforce');
    }
}

```

# 💡 Deployment Tips
* Run your test class using Developer Console > Test > Run All to confirm coverage.

* The batch job uses QueryLocator for efficiency with large data volumes.

* If needed, you can extend it to filter only blank LeadSource values with a WHERE clause.