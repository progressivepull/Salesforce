# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Visualforce page that shows a list of Accounts linked to their record pages**

Use a standard list controller to display a list of account names that link to their respective record pages.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **AccountList**
    - Name: **AccountList**
* CStandard controller: **Account**
* C page must have a **recordSetVar** attribute equal to **accounts**
* CYour page must have a Visualforce **apex:repeat** component, with the following:
    - Set the var attribute of the **apex:repeat** component to a.
    - Nest a <li> list item HTML element inside the apex:repeat component.
    - Nest an **apex:outputLink** component inside the <li> element.
* Hint: To link the URL of an account’s record detail page, set the **value** attribute of the **apex:outputLink to /{!a.id}**.


# Solution

Certainly! Here's a Visualforce page named **AccountList** that meets all your specified challenge requirements:

# 📄 Visualforce Page: AccountList

``` html
<apex:page standardController="Account" recordSetVar="accounts">
    <h2>Account Directory</h2>
    <ul>
        <apex:repeat value="{!accounts}" var="a">
            <li>
                <apex:outputLink value="/{!a.Id}">{!a.Name}</apex:outputLink>
            </li>
        </apex:repeat>
    </ul>
</apex:page>

```
# ✅ Breakdown of Requirements Met

* Standard controller: Account

* recordSetVar set to accounts to handle a list of Account records

* Uses apex:repeat to iterate through accounts, with var="a"

* Each <li> contains an apex:outputLink that references /​{!a.Id} to navigate to the account's record detail page

* Displays each account’s Name as the link text