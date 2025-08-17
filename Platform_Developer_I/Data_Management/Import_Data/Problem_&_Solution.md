# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Import data using the Data Import Wizard.**

Download a CSV file that contains contact data, and import it using the Data Import Wizard.

* Download this CSV file by right-clicking and selecting "Save Link As". Make sure you save it as a CSV (.csv) file, and not a text (.txt) file. You don't need to use Excel.
* Use the Data Import Wizard to import the file:
    - Kind of data: Accounts and Contacts
    - Type of import: Add new records
        - Match Contact by: Name
    - Where is your data located?: CSV
        - File: Choose File
        - Character Code: ISO-8859-1 (the default)
        - Values Separated by: Comma
    - Map all fields:
        - FNAME to Contact: First Name
        - LNAME to Contact: Last Name
        - CELL to Contact: Mobile

  
# Solution

# 🧭 Step-by-Step: Import Contacts with the Data Import Wizard

1. Prepare Your File:
* Right-click the download link and select Save Link As
* Save the file with a .csv extension (not .txt)
* Confirm the file includes columns like FNAME, LNAME, and CELL

2. Open Data Import Wizard:
* Go to Setup
* Type “Data Import Wizard” in the Quick Find box
* Click Launch Wizard

3. Choose Object Type:
* Scroll down to Accounts and Contacts
* Click Standard Objects → Contacts → Launch Wizard for this object

4. Select Import Options:
* Type of Import: Add new records
* Match Contact by: Name
* Where is your data located? CSV

5. Upload File:
* Click Choose a CSV File
* Select your file
* Character Encoding: ISO-8859-1 (should be default)
* Values Separated By: Comma

6.  Your Fields:
* Map FNAME to → Contact: First Name
* Map LNAME to → Contact: Last Name
* Map CELL to → Contact: Mobile
  
7. Review & Start Import:
* Confirm field mappings
* Click Start Import