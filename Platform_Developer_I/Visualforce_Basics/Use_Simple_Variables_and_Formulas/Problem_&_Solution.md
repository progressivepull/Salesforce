# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a Visualforce page that shows user information**

Create a Visualforce page that displays the first name of the currently logged-in user.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **DisplayUserInfo**
    - Name: **DisplayUserInfo**
* The displayed user information must be generated dynamically from the logged-in user

# Solution

You got it! Here's a simple Visualforce page called **DisplayUserInfo** that dynamically displays the first name of the currently logged-in user:

# 👤 Visualforce Page: DisplayUserInfo

``` html
<apex:page>
    <apex:outputText value="Hello, {!$User.FirstName}!" />
</apex:page>

``` 
# ✅ Key Details
* The magic lies in the **$User global variable**, which gives access to fields from the user who's currently logged in.

* The page doesn’t need a controller because it's using a built-in global variable.

* You’ll see something like **"Hello, Maria!"** on screen, depending on the active user.

Want to expand this to show their full name, profile, or even a fun avatar image? I’d be happy to help you level it up!