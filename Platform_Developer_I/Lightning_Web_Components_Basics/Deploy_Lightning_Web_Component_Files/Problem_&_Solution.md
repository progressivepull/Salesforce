# Problems

**Create an app page for the bike card component**

Deploy your files to your Trailhead Playground or Developer Edition org and then use Lightning App Builder to create an app page.

**Prework:** If you haven't already completed the activities in the What You Need section of this unit, do that now, or this challenge won't pass. Make sure that Dev Hub is enabled in your org and that the org is authorized with Visual Studio Code.


* Create an SFDX project in Visual Studio Code:
    - Template: **Standard**
    - Project name: **bikeCard**
* Add a Lightning Web Component to the project:
    - Folder: **lwc**
    - Component name: **bikeCard**
* Copy the content for the component files from this unit into your files in Visual Studio Code:
    - bikeCard.html
    - bikeCard.js
    - bikeCard.js-meta.xml
* Deploy the bikeCard component files to your org
* Create a Lightning app page:
    - Label: **Bike Card**
    - Developer Name: **Bike_Card**
    - Add your bikeCard component to the page
    - Activate the page for all users

# Solution

# ⚙️ Step 1: Create the SFDX Project

In Visual Studio Code, open the Command Palette (⇧⌘P or Ctrl+Shift+P) and run:

```
SFDX: Create Project
```

* Choose the Standard template.

* Enter project name: bikeCard

* Choose or create a folder to store your project.

# 🧩 Step 2: Add Your Lightning Web Component

Use the Command Palette again:

```
SFDX: Create Lightning Web Component
```
* Name: bikeCard

* Folder: force-app/main/default/lwc

Replace the contents of the following files with what’s provided in the unit:

* bikeCard.html

* bikeCard.js

* bikeCard.js-meta.xml

Ensure your meta file includes:

``` xml
<targets>
    <target>lightning__AppPage</target>
</targets>

```
This makes your component eligible to be added to an App Page.

# 🚀 Step 3: Deploy the Component

Use:

```
SFDX: Deploy Source to Org

```
Make sure your org is authorized (via SFDX: Authorize an Org) and Dev Hub is enabled.

# 🧱 Step 4: Create a Lightning App Page
Head to **Setup > Lightning App Builder** in your org:

* Create a new App Page

* Label: Bike Card

* Developer Name: Bike_Card

* Add your bikeCard component to the page layout

* Save and Activate for All Users

# 🏁 Final Step: Test It!
* Preview the page to confirm your component displays correctly.

* If you'd like, I can help you build a dynamic version of the card, maybe based on data from a custom Bike__c object or a wire service.

