# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Visualforce page that shows a basic Contact record**

Using the Contact standard controller, create a Visualforce page that displays a Contact's First Name, Last Name and the Email address of the Contact's Owner.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **ContactView**
    - Name: **ContactView**
* Standard controller: Contact
* Your page must include three bind variables that use the standard controller to display the following Contact record information:
* **First Name**
* **Last Name**
* **Owner Email**



# Solution

Here's a Visualforce page named **ContactView** that uses the standard controller for **Contact** and displays the requested fields:

``` html
<apex:page standardController="Contact">
    <apex:pageBlock title="Contact Details">
        <apex:pageBlockSection>
            <apex:outputText value="First Name: {!Contact.FirstName}" /><br/>
            <apex:outputText value="Last Name: {!Contact.LastName}" /><br/>
            <apex:outputText value="Owner Email: {!Contact.Owner.Email}" />
        </apex:pageBlockSection>
    </apex:pageBlock>
</apex:page>

```
# ✅ Key Points

* Uses the built-in **standard controller**, no need for a custom Apex class.

* Accesses the **Owner** relationship via **Contact.Owner.Email**.

* Displays each field as plain text using **apex:outputText**.

If you’d like to style this or add a conditional message like “This contact has no owner email,” I can help you enhance it next!