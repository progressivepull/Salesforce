# Problem

## Apex Specialist
### What You'll Be Doing to Earn This Superbadge
1. Automate record creation using Apex triggers
2. Synchronize Salesforce data with an external system using asynchronous REST callouts
3. Schedule synchronization using Apex code
4. Test automation logic to confirm Apex trigger side effects
5. Test integration logic using callout mocks
6. Test scheduling logic to confirm action gets queued

### Concepts Tested in This Superbadge
* Apex Triggers
* Asynchronous Apex
* Apex Integration
* Apex Testing
  
### Note
We're hard at work bringing you a reimagined superbadge experience. As part of that process, most of our long-format superbadges have been retired. However, this superbadge, along with the other long-format superbadges that are related to Salesforce certification exams, will remain available in their current format for now. To learn more about the next evolution of superbadges, check out the FAQ document.

### Pre-work and Notes
* Grab a pen and paper. You may want to jot down notes as you read the requirements.
* Refer to the Apex Specialist Superbadge: Trailhead Challenge Help document for detailed resources and documentation.
* Use the naming conventions specified in the requirements document to ensure a successful deployment.
* Review the data schema in your modified Salesforce org as you read the detailed requirements below.

### Set Up Development Org
1. Create a new Trailhead Playground or Developer Edition Org for this superbadge. Using this org for any other reason might create problems when validating the challenge.

2. Install this unlocked package (package ID: 04t6g000008av9iAAA). This package contains metadata you'll use to complete this challenge. If you have trouble installing this package, follow the steps in the Install a Package or App to Complete a Trailhead Challenge help article.

3. Add picklist values Repair and Routine Maintenance to the Type field on the Case object.

4. Update the Case page layout assignment to use the Case (HowWeRoll) Layout for your profile.

5. Rename the tab/label for the Case tab to Maintenance Request.

6. Update the Product page layout assignment to use the Product (HowWeRoll) Layout for your profile.

7. Rename the tab/label for the Product object to Equipment.

8. Use App Launcher to navigate to the Create Default Data tab of the How We Roll Maintenance app. Click Create Data to generate sample data for the application.

9. Review the newly created records to get acquainted with the data model.

### Notes
Before you begin the challenges, review the help article for this superbadge. This document will help you find useful resources to complete this superbadge and assist with frequently asked questions.

### Use Case
There are two kinds of people in this world: those who would travel in a recreational vehicle (RV) and those who wouldn’t. The RV community is increasing exponentially across the globe. Over the past few years, HowWeRoll Rentals, the world’s largest RV rental company, has increased its global footprint and camper fleet tenfold. HowWeRoll offers travelers superior RV rental and roadside assistance services. Their tagline is, “We have great service, because that’s How We Roll!” Their rental fleet includes every style of camper vehicle, from extra large, luxurious homes on wheels to bare bones, retro Winnebagos.

You have been hired as the lead Salesforce developer to automate and scale HowWeRoll’s reach. For travelers, not every journey goes according to plan. Unfortunately, there’s bound to be a bump in the road at some point along the way. Thankfully, HowWeRoll has an amazing RV repair squad who can attend to any maintenance request, no matter where you are. These repairs address a variety of technical difficulties, from a broken axle to a clogged septic tank.

As the company grows, so does HowWeRoll’s rental fleet. While it’s great for business, the current service and maintenance process is challenging to scale. In addition to service requests for broken or malfunctioning equipment, routine maintenance requests for vehicles have grown exponentially. Without routine maintenance checks, the rental fleet is susceptible to avoidable breakdowns.

That’s where you come in! HowWeRoll needs you to automate their Salesforce-based routine maintenance system. You’ll ensure that anything that might cause unnecessary damage to the vehicle, or worse, endanger the customer is flagged. You’ll also integrate Salesforce with HowWeRoll’s back-office system that keeps track of warehouse inventory. This completely separate system needs to sync on a regular basis with Salesforce. Synchronization ensures that HowWeRoll’s headquarters (HQ) knows exactly how much equipment is available when making a maintenance request, and alerts them when they need to order more equipment.


### Standard Objects
You’ll be working with the following standard objects:

* **Maintenance Request (renamed Case) —** Service requests for broken vehicles, malfunctions, and routine maintenance.
* **Equipment (renamed Product) —** Parts and items in the warehouse used to fix or maintain RVs.
 
### Custom Objects
* **Vehicle —** Vehicles in HowWeRoll’s rental fleet.
* **Equipment Maintenance Item —** Joins an Equipment record with a Maintenance Request record, indicating the equipment needed for the maintenance request.

### Entity Diagram

<img src="./IMAGES/Entity_Diagram.png" alt="Entity Diagram">

### Business Requirements
This section represents the culmination of your meetings with key HowWeRoll stakeholders. It’s your blueprint to programmatically automate the support and maintenance side of their business.

### Automate Maintenance Requests
With the exponential increase in RV popularity worldwide, HowWeRoll is supplying hundreds more luxury and economy vehicles around the globe. Along with this increase in their rental stock comes an inevitable increase in equipment failure. HowWeRoll has an existing process to handle these failures, but they want you to build an automation for their routine maintenance. You’ll build a programmatic process that automatically schedules regular checkups on the equipment based on the date that the equipment was installed.

### Notes
Use the help article for this superbadge to reference the API names of the objects and fields. This accelerates your development process by not going back and forth between Setup and your development tool.

When an existing maintenance request of type Repair or Routine Maintenance is closed, create a new maintenance request for a future routine checkup. This new maintenance request is tied to the same Vehicle and Equipment Records as the original closed request. For record keeping purposes the existing equipment maintenance items must remain tied to the original close request so new records must be created. This new request's Type should be set as Routine Maintenance. The Subject should not be null and the Report Date field reflects the day the request was created. Remember, all equipment has maintenance cycles.

Calculate the maintenance request due dates by using the maintenance cycle defined on the related equipment records. If multiple pieces of equipment are used in the maintenance request, define the due date by applying the shortest maintenance cycle to today’s date.

Design the code to work for both single and bulk maintenance requests. Bulkify the system to successfully process approximately 300 records of offline maintenance requests that are scheduled to import together. For now, don’t worry about changes that occur on the equipment record itself.

Also expose the logic for other uses in the org. Separate the trigger (named MaintenanceRequest) from the application logic in the handler (named MaintenanceRequestHelper). This setup makes it simpler to delegate actions and extend the app in the future.

### Synchronize Inventory Management
In addition to equipment maintenance, design HowWeRoll’s inventory data synchronization with the external system in the equipment warehouse. Although the entire HQ office uses Salesforce, the warehouse team still works on a separate legacy system. With this integration, the inventory in Salesforce updates after the equipment is taken from the warehouse to service a vehicle.

Write a class that makes a REST callout to an external warehouse system to get a list of equipment that needs to be updated. The callout’s JSON response returns the equipment records that you upsert in Salesforce. Beyond inventory, ensure that other potential warehouse changes carry over to Salesforce. Your class maps the following fields:

* Replacement part (this should be set to true for all records that come in from the warehouse system)

* Cost

* Current inventory

* Lifespan

* Maintenance cycle

* Warehouse SKU

Use the warehouse SKU as the external ID to identify which equipment records to update within Salesforce.

Although HowWeRoll is an international company, the remote offices follow the lead of the HQ’s work schedule. Therefore, all maintenance requests are processed during HQ’s normal business hours. You need to update Salesforce data during off hours (at 1:00 AM). This logic runs daily so that the inventory is up to date every morning at HQ.

### Create Unit Tests

Test your code to ensure that it executes correctly before deploying it to production.

First, test the trigger to ensure that it works as expected. Follow best practices by testing for both positive use cases (when the trigger needs to fire) and negative use cases (when the trigger must not fire). Of course, passing a test doesn’t necessarily mean you got everything correct. So add assertions into your code to ensure you don’t get false positives. For your positive test, assert that everything was created correctly, including the relationships to the vehicle and equipment, as well as the due date. For your negative test, assert that no work orders were created.

As mentioned previously, the huge wave of maintenance requests could potentially be loaded at once. The number will probably be around 200, but to account for potential spikes, pad your class to successfully handle at least 300 records. To test this, include a positive use case for 300 maintenance requests and assert that your test ran as expected.

When you have 100% code coverage on your trigger and handler, write test cases for your callout and scheduled Apex classes. You need to have 100% code coverage for all Apex in your org.

Ensure that your code operates as expected in the scheduled context by validating that it executes after Test.stopTest() without exception. Also assert that a scheduled asynchronous job is in the queue. The test classes for the callout service and scheduled test must also have 100% test coverage.
