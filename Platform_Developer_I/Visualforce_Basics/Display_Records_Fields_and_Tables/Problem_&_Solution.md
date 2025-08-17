# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Visualforce page that displays a variety of output fields**

Create a page that displays a subset of Opportunity fields using apex:outputField components. Bind the Name, Amount, Close Date and Account Name fields to the apex:outputField components.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **OppView**
    - Name: **OppView**
* Standard controller: **Opportunity**
* It must have four **apex:outputField** components bound to the following Opportunity fields:
    - **Opportunity Name**
    - **Amount**
    - **Close Date**
    - **Account Name of the Opportunity**


# Solution

Here’s a clean and functional **Visualforce** page named **OppView** that meets all your challenge requirements: 

# 📄 Visualforce Page: OppView

``` html
<apex:page standardController="Opportunity">
    <apex:form>
        <apex:pageBlock title="Opportunity Details">
            <apex:pageBlockSection>
                <apex:outputField value="{!Opportunity.Name}" label="Opportunity Name" />
                <apex:outputField value="{!Opportunity.Amount}" label="Amount" />
                <apex:outputField value="{!Opportunity.CloseDate}" label="Close Date" />
                <apex:outputField value="{!Opportunity.Account.Name}" label="Account Name" />
            </apex:pageBlockSection>
        </apex:pageBlock>
    </apex:form>
</apex:page>

```
# ✅ Key Features

* Uses the standard controller for Opportunity.

* Four apex:outputField components tied to:

    - Opportunity.Name

    - Opportunity.Amount

    - Opportunity.CloseDate

    - Opportunity.Account.Name (note the dot notation to access the parent Account name)

This page will automatically display the fields from an existing Opportunity when navigated to with its record ID in the URL (e.g., /apex/OppView?id=006XXXXXXXXXXXX). If you'd like to add styling or conditional logic, I can help you jazz it up a bit!