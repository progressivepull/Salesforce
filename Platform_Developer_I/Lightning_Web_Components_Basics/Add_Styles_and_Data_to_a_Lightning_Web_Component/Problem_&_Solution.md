# Problems

**Import the current user’s name into your Lightning app page**

Create a Lightning app page that uses the wire service to display the current user's name.

**Prework:** You need files created in the previous unit to complete this challenge. If you haven’t already completed the activities in the previous unit, do that now.

* Create a Lightning app page:
    - Label: Your Bike Selection
    - API Name: Your_Bike_Selection
* Add the current user's name to the app container:
    - Edit selector.js
    - Edit selector.html


# Solution

[Add Styles & Data to Lightning Web Component|Lightning Web Components Basics|Salesforce|Trailhead - 
Education Matters- YouTube](https://www.youtube.com/watch?v=iPi-5oJapJI)

Here's how to complete the challenge and wire up the current user's name to your Lightning App page titled **Your Bike Selection**.

# ⚙️ Step 1: Create the Lightning App Page
In Lightning App Builder, do the following:

* Label: Your Bike Selection

* API Name: Your_Bike_Selection

* Add your custom component (let’s say it’s called selector) to the page layout.

# 🧠 Step 2: Use Wire Service to Get Current User Info

## 📄 selector.js

Update the JavaScript file to import the current user’s data via Salesforce's wire service:

``` js
import { LightningElement, wire } from 'lwc';
import { getRecord } from 'lightning/uiRecordApi';
import USER_ID from '@salesforce/user/Id';

// Define the fields you want to pull
import NAME_FIELD from '@salesforce/schema/User.Name';

export default class Selector extends LightningElement {
    userName;

    @wire(getRecord, { recordId: USER_ID, fields: [NAME_FIELD] })
    wiredUser({ error, data }) {
        if (data) {
            this.userName = data.fields.Name.value;
        } else if (error) {
            console.error('Error fetching user data', error);
        }
    }
}

```

## 📄 selector.html 

Update the template to display the current user’s name:

``` html
<template>
    <lightning-card title="Your Bike Selection">
        <div class="slds-p-around_medium">
            <p>Welcome, {userName}!</p>
            <!-- Add any other page content here -->
        </div>
    </lightning-card>
</template>

```

# ✅ Checklist Recap

* [x] Page labeled Your Bike Selection

* [x] Wire service used to fetch logged-in user’s name

* [x] apex/schema/User.Name used for reference

* [x] Name displayed inside a Lightning Card