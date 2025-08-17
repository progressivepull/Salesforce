# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Visualforce form which inserts a basic Contact record**

Using the Visualforce apex:form component, create a page that inserts a Contact record based on First Name, Last Name and Email. After submitting the form, the user should be redirected to the detail page of the new Contact record.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **CreateContact**
    - Name: **CreateContact**
* Standard controller: Contact
* Your page must use a Visualforce **apex:form** component
* Your page must have three **apex:inputField** components bound to the following Contact fields:
**First Name**
**Last Name**
**Email**
* Your page must have an **apex:commandButton** component that uses the **save** method from the standard controller


# Solution

# 📄 Visualforce Page: CreateContact

``` html
<apex:page standardController="Contact">
    <apex:form>
        <apex:pageBlock title="Create a New Contact">
            <apex:pageBlockSection>
                <apex:inputField value="{!Contact.FirstName}" label="First Name"/>
                <apex:inputField value="{!Contact.LastName}" label="Last Name"/>
                <apex:inputField value="{!Contact.Email}" label="Email"/>
            </apex:pageBlockSection>
            <apex:pageBlockButtons>
                <apex:commandButton action="{!save}" value="Save" />
            </apex:pageBlockButtons>
        </apex:pageBlock>
    </apex:form>
</apex:page>

```
# ✅ Key Behaviors

* Uses the **standard controller** for **Contact**, so no custom Apex is required.

* Displays a form with **three input fields** bound to **FirstName**, **LastName**, and **Email**.

* The **save button** automatically inserts the record and redirects to the detail page of the newly created **Contact**.

This is a textbook use of **apex:form** and **inputField**, and it gives you a super clean UI in Salesforce Classic. Want to add field validation or error messaging next? I’ve got just the code snippet for that
