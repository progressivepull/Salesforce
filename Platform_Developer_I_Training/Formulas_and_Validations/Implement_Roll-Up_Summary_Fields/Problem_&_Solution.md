# Problems

# Create a Rollup Summary Field
Add a custom field to the standard account object to provide a rollup summary of the total expected revenue from all related opportunities.

**Important:** If you have Advanced Currency Management enabled in your Trailhead Playground, disable it for this Hands-On Challenge.

* Create a roll-up summary field on the Account object:
    - Field Label: Potential Value
    - Field Name: Potential_Value
    - Calculate the total expected revenue of all the opportunities related to the account

  
# Solution

Here’s how to create the roll-up summary field “Potential Value” on the Account object to sum the expected revenue of related opportunities:

---

# How to Create a Roll-Up Summary Field for Potential Value in Salesforce

Follow these steps to create a roll-up summary field on the Account object that sums up the Expected Revenue from related Opportunities:

1. **Go to Setup > Object Manager.**
2. **Select Account.**
3. **Go to Fields & Relationships** and click **New**.
4. **Choose Roll-Up Summary** as the data type and click **Next**.
5. **Fill out the field details:**
   - **Field Label:** `Potential Value`
   - **Field Name:** `Potential_Value`
6. Click **Next**.
7. **Set up the roll-up summary:**
   - **Summarized Object:** `Opportunity`
   - **Roll-Up Type:** `SUM`
   - **Field to Aggregate:** `Opportunity: Expected Revenue`
   - **Filter Criteria:** All records (unless you want to filter for specific opportunities)
8. Click **Next**, set field-level security, and add to page layouts as needed.
9. Click **Save**.

## Result:
The “Potential Value” field on Account will automatically display the sum of the expected revenue from all related opportunities.

### Note:
Roll-up summary fields are only available for master-detail relationships. The standard Account–Opportunity relationship supports this because Opportunity has a standard lookup to Account that behaves like master-detail for roll-ups.
