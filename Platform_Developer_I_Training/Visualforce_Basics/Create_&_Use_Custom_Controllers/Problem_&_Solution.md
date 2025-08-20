# Problems

**Create a Visualforce page that displays new cases**

Create a Visualforce page that uses a custom controller to display a list of cases with the status of New.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **NewCaseList**
    - Name: **NewCaseList**
* Create a custom Apex controller:
    - Name: NewCaseListController
    - Include a publicly scoped method named **getNewCases**
    - Use the return type of **List<Case>**
    - Return a list of case records that includes the **ID** and **CaseNumber** fields
    - Filter the results returned to only have a status of **New**
* The NewCaseList Visualforce page must use an apex:repeat component, which is:
    - Bound to **newCases**
    - Refers to the var attribute as case
    - With the component tags, bind an **apex:**component to the **ID** of the case. This will cause the the page to direct the user to the detail page of the respective case record.


# Solution

Here’s a complete solution for your NewCaseList Visualforce page and its corresponding NewCaseListController, meeting all challenge requirements:

# ⚙️ Apex Controller: NewCaseListController

``` apex
public class NewCaseListController {
    public List<Case> getNewCases() {
        return [SELECT Id, CaseNumber FROM Case WHERE Status = 'New'];
    }
}

```

# 🧾 Visualforce Page: NewCaseList

``` html
<apex:page controller="NewCaseListController" showHeader="true">
    <apex:repeat value="{!newCases}" var="case">
        <apex:outputLink value="/{!case.Id}">Case Number: {!case.CaseNumber}</apex:outputLink><br/>
    </apex:repeat>
</apex:page>

```

#✅ Highlights

* getNewCases() fetches only Case records with Status = 'New'.

* The page uses apex:repeat to iterate through each record.

* apex:outputLink directs users to each case's detail page using the Id.


