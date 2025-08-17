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

You're building out a great foundation for DreamHouse Realty's offer tracking! Here's how to complete the relationships for the Offer object in Salesforce:

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