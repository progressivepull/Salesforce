# Problems

Get Ready
You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Build a custom Offer object**


When a homebuyer makes an offer to buy a property, the brokers at DreamHouse Realty need to track the details in Salesforce. Create a custom object they can use to record the offer amount and target close date for the sale. Use auto numbering to generate the name of each offer record.

* Create a custom object
    - Label: Offer
    - Object Name: Offer
    - Record Name: Offer Name
    - Data Type: Auto Number
    - Display Format: OF-{0000}
    - Starting Number: 1
* Create a custom currency field on the Offer object
    - Data Type: Currency
    - Field Label: Offer Amount
    - Field Name: Offer_Amount
* Create a custom date field on the Offer object
    - Data Type: Date
    - Field Label: Target Close Date
    - Field Name: Target_Close_Date


# Solution

Here's how you'd build the custom Offer object in Salesforce step by step:

# 🏠 Step 1: Create the Custom Object

* Label: Offer
* Object Name: Offer
* Record Name:
    - Field Label: Offer Name
    - Data Type: Auto Number
    - Display Format: OF-{0000}
    - Starting Number: 1

📌 This setup ensures every Offer record automatically gets a unique identifier like OF-0001, OF-0002, etc.

# 💵 Step 2: Add Custom Currency Field
* Field Label: Offer Amount
* Field Name: Offer_Amount
* Data Type: Currency

🎯 Use this to capture the amount the homebuyer is offering for the property.

# 📅 Step 3: Add Custom Date Field
* Field Label: Target Close Date
* Field Name: Target_Close_Date
* Data Type: Date

🗓️ This helps brokers track the desired closing date for each offer.