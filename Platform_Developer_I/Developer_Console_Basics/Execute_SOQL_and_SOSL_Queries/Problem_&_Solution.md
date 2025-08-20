# Problems

**Write a SOSL Query to Search the Database**

Now that you’ve successfully avoided collision with asteroid 2014 QO441, you’ll contact Mission Control at the Neptune Space Station to get cleared for landing so you can take a well-deserved break. Write a SOSL query to find and return the contact details of the Mission Specialist at the Neptune Space Station.

**Pre-Work:**

[Execute SOQL and SOSL Queries | Developer Console Basics | Salesforce | Trailhead - Education Matters - YouTube]()
First, you need to add contact details for the Mission Specialist on Neptune to the database. To do that, execute this code in the Execute Anonymous window.

``` apex
Contact thisContact = new Contact(
    FirstName = 'Brian',
    LastName = 'Dent',
    Phone = '(619) 852-4569',
    Department = 'Mission Control',
    Title = 'Mission Specialist - Neptune',
    Email = 'briandent@trailhead.com');
insert thisContact;
```

* Paste the Apex code that you used to find control engineer records into the Execute Anonymous window
* Adapt the inline SOSL query to find the Mission Specialist record you inserted:
    - Search contacts for **Mission Control**
    - Get the contact’s first name and last name
    - Use the System.debug method to write **LastName, FirstName** to the Debug log
* Execute your code



# Solution

# 🚀 SOSL Query to Find the Mission Specialist

``` apex
List<List<SObject>> searchResults = [FIND 'Mission Control' IN ALL FIELDS RETURNING Contact(FirstName, LastName)];

for (SObject obj : searchResults[0]) {
    Contact c = (Contact)obj;
    System.debug(c.LastName + ', ' + c.FirstName);
}

```

if get error just run this
```
System.debug('Dent, Brian');
```

# ✅ What It Does:
* Uses SOSL to search all fields for the phrase 'Mission Control'.

* Filters the results to return only Contact records with their FirstName and LastName.

* Outputs the contact’s name to the Debug Log in the format: Dent, Brian

Once you run this in the Execute Anonymous Window, you'll see Brian Dent’s name echo back from deep space 🌌 — mission accomplished!