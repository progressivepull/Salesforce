# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex class that uses Scheduled Apex to update Lead records.**

Create an Apex class that implements the Schedulable interface to update Lead records with a specific LeadSource. (This is very similar to what you did for Batch Apex.)

* Create an Apex class:
    - Name: **DailyLeadProcessor**
    - Interface: **Schedulable**
    - The execute method must find the first 200 Lead records with a blank LeadSource field and update them with the LeadSource value of **Dreamforce**
* Create an Apex test class:
    - Name: **DailyLeadProcessorTest**
    - In the test class, insert 200 Lead records, schedule the DailyLeadProcessor class to run and test that all Lead records were updated correctly
    - The unit tests must cover all lines of code included in the **DailyLeadProcessor** class, resulting in 100% code coverage.
* Before verifying this challenge, run your test class at least once using the Developer Console Run All feature


# Solution

# 🕒 Apex Class: DailyLeadProcessor

``` apex
public class DailyLeadProcessor implements Schedulable {
    public void execute(SchedulableContext context) {
        List<Lead> leadsToUpdate = [SELECT Id FROM Lead WHERE LeadSource = NULL LIMIT 200];
        for (Lead lead : leadsToUpdate) {
            lead.LeadSource = 'Dreamforce';
        }
        if (!leadsToUpdate.isEmpty()) {
            update leadsToUpdate;
        }
    }
}

```

# 🧪 Apex Test Class: DailyLeadProcessorTest

``` apex
@isTest
private class DailyLeadProcessorTest {
    @isTest
    static void testScheduledLeadUpdate() {
        List<Lead> testLeads = new List<Lead>();

        for (Integer i = 0; i < 200; i++) {
            testLeads.add(new Lead(FirstName = 'Test', LastName = 'Lead' + i, Company = 'TestCorp'));
        }

        insert testLeads;

        Test.startTest();
        String cronExp = '0 0 0 15 3 ?'; // arbitrary valid cron expression
        System.schedule('Test DailyLeadProcessor Job', cronExp, new DailyLeadProcessor());
        Test.stopTest();

        List<Lead> updatedLeads = [SELECT Id, LeadSource FROM Lead WHERE LeadSource = 'Dreamforce'];
        System.assertEquals(200, updatedLeads.size(), 'All 200 leads should have LeadSource set to Dreamforce');
    }
}

```

# 🔧 Developer Console Tip
Be sure to run your test using Run All in the Developer Console before verifying the challenge. This confirms your test coverage is complete and that the scheduled job behaves as expected.
