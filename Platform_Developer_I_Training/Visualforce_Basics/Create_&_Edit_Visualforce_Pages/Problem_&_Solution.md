# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a simple Visualforce page that displays an image**

Create a Visualforce page without the standard Salesforce header and display an image using the Visualforce image component. Assume that you're in Salesforce Classic.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **DisplayImage**
    - Name: **DisplayImage**
* It must not display the standard Salesforce header
* It must use a Visualforce **apex:image** component to display this image: https://developer.salesforce.com/files/salesforce-developer-network-logo.png


# Solution

# 🖼️ Visualforce Page: DisplayImage

``` html
<apex:page showHeader="false">
    <apex:image url="https://developer.salesforce.com/files/salesforce-developer-network-logo.png" />
</apex:page>
```

# ✅ Key Features
* showHeader="false" removes the standard Salesforce header.

* apex:image component loads the specified image from the external URL.

**To verify:**

1. Navigate to Setup > Visualforce Pages.

2. Create a new page named DisplayImage.

3. Paste in the code above.

4. Preview the page in Salesforce Classic—no header, clean image display!