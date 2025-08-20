# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create relationships for the Offer object**

The object you created for the previous challenge is pretty handy. Imagine how much more useful it would be if brokers could specify which client made an offer and which property the client wants to buy. Add two relationships to the Offer object so brokers can capture this data in Salesforce. Create a Master-Detail relationship with the Property object and a Lookup relationship with the Contact object.

Even if you're completing this module as part of the Admin Beginner trail, be sure you use the new Trailhead Playground you created in the previous unit.

**Before You Start:**

* Create the Property object as described in the previous unit.

**Challenge Requirements:**

* Create a custom Master-Detail field on the Offer object
    - Data Type: Master-Detail
    - Related To: Property
    - Field Label: Property
    - Field Name: Property
* Create a custom Lookup Relationship field on the Offer object
    - Data Type: Lookup Relationship
    - Related To: Contact
    - Field Label: Contact
    - Field Name: Contact


# Solution

From Lesson (Must do before start below solution): Optimize Customer Data with Standard and Custom Objects

You're building out a great foundation for DreamHouse Realty's offer tracking! Here's how to complete the relationships for the Offer object in Salesforce:


## Create a Custom Object
Follow along as D’Angelo to see how he builds the Property object. You need this object later, so don’t skip these steps!

1. Scroll to the bottom of this page and create a trailhead playground. Don’t skip this step! You need to use a fresh and clean Trailhead Playground for this module.
**Note:** Even if you're completing this module as part of the Admin Beginner trail, be sure and create a new Trailhead Playground to complete these steps. You don't need to reinstall the Dreamhouse app in the new playground org.
2. Once your playground is created (it takes a minute!), press Launch.
3. Click the gear icon The setup gear. at the top of the page and launch setup.
4. Click the **Object Manager** tab.
5. Click **Create | Custom Object **in the top-right corner.
6. For Label, enter **Property**. Notice that the Object Name and Record Name fields auto-fill.
7. For Plural Label, enter **Properties**.
8. Prior to saving the custom object, scroll to the bottom of the page and select the checkbox **Launch New Custom Tab Wizard after saving this custom object**.
9. Leave the rest of the values as default and click **Save**.
10. On the New Custom Object Tab page, click the Tab Style field and select a style you like. The style sets the icon to display in the UI for the object.
11. Click Next, Next, and Save.

Great job! You just created your first custom object. Now, learn about adding fields to this object.


# 🔗 Step 1: Create Master-Detail Relationship (Offer → Property)

This connects the Offer to the Property it targets and ensures it's tied to the lifecycle of that Property record.

* Navigate to: Setup → Object Manager → Offer
* Go to: Fields & Relationships → Click New
* Choose Data Type: Master-Detail Relationship
* Related To: Property
* Field Label: Property
* Field Name: Property
* Field Settings:
    - Make this field required
    - Optionally add to page layouts
    - Enable reparenting if you want Offers to be reassigned to other Properties

🧠 Why Master-Detail? Because if the Property is deleted, the Offer disappears too — ensuring data integrity.

# 👤 Step 2: Create Lookup Relationship (Offer → Contact)

This links the Offer to the buyer (Contact), without tying its lifecycle to that record.

* Navigate to: Setup → Object Manager → Offer
* Go to: Fields & Relationships → Click New
* Choose Data Type: Lookup Relationship
* Related To: Contact
* Field Label: Contact
* Field Name: Contact

🎯 Use this to track which client (Contact) made the offer.