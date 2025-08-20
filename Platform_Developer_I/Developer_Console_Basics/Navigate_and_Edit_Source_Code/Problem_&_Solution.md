# Problems

**Create a Visualforce Page**

Create a Visualforce page that your engineers can use to indicate that they’re at their stations and ready for takeoff. For now, just create the Visualforce page. Later, when you have some downtime in deep space, you can add an Apex controller and some more page components.


* Create the **EmailMissionSpecialist** class in your org according to the instructions in this unit
* Create a Visualforce page named **StationCheck**
* Copy the code for the **FlightSystemsChecklist** page and paste it into your new StationCheck page
* Change the contents of the heading (**<h1>**) from Checklist to **Station Status**


# Solution

Here's the updated Visualforce page code based on your instructions. Assuming the original **FlightSystemsChecklist** page has an **<h1>** element labeled "Checklist", this modified version renames it to **Station Status**.


# 🚀 Visualforce Page: StationCheck

``` html
<apex:page>
    <h1>Station Status</h1>

    <!-- Example content carried over from FlightSystemsChecklist -->
    <apex:form>
        <apex:pageBlock title="Ready for Takeoff">
            <apex:pageBlockSection>
                <apex:inputCheckbox title="Navigation System Online" />
                <apex:inputCheckbox title="Communications System Online" />
                <apex:inputCheckbox title="Life Support System Online" />
 		<apex:commandButton value="Save Checklist" action="{!save}" />
            </apex:pageBlockSection>
        </apex:pageBlock>
    </apex:form>
</apex:page>
```

# ✅ Next Steps
* Deploy the EmailMissionSpecialist class as instructed.

* Create this page as StationCheck in Setup > Visualforce Pages, and paste in the modified code.

* Later, you can bind these inputs to controller logic to track each engineer’s check-in and send mission updates.

ERROR:
In the StationCheck Visualforce page, we can’t find a commandButton that saves the checklist. Make sure the commandButton tag includes action="{!save}".
