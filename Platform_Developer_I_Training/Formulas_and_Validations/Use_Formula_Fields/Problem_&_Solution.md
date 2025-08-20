# Problems

## Create a Formula Field

Create a formula field that calculates the number of days remaining before a contract expires.

* Create a custom field:
    - Object: Contract
    - Data Type: Formula
    - Field Label: Days Remaining
    - Field Name: Days_Remaining
    - Formula Return Type: Number
    - Formula: Calculate the number of days between the contract end date and today

  
# Solution

To create a formula field "Days Remaining" on the Contract object in Salesforce that calculates the number of days before a contract expires, follow these steps:

1. Go to **Setup** > **Object Manager**.
2. Find and select **Contract**.
3. Go to **Fields & Relationships** and click **New**.
4. Select **Formula** as the data type and click **Next**.
5. Fill out the details:
   - **Field Label**: Days Remaining
   - **Field Name**: Days_Remaining
   - **Formula Return Type**: Number
6. Click **Next**.
7. In the formula editor, enter the following formula:

- Here, `EndDate` is the standard field for the contract end date. If you're using a custom field, use its API name.

8. Optionally, to prevent negative values (for expired contracts), use:

``` apex
EndDate - TODAY()
```

9. Click **Next**, set field-level security, add to page layouts as needed, and **Save**.

**Result:**  
The "Days Remaining" field will display the number of days until the contract’s end date (or 0 if already expired).

``` apex
MAX(EndDate - TODAY(), 0)
```
