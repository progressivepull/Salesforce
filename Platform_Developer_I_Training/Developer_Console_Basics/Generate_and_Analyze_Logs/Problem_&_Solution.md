# Problems

**Create a Perspective to Generate and Analyze Logs**

Generate a debug log, and create a custom Perspective to analyze it.

* For the SFDC_DevConsole debug level, set the logging level for ApexCode to **FINEST**
* Use the Execute Anonymous window to execute the **EmailManager** Apex class that you created earlier, providing your own email address
* Create a Developer Console Perspective:
    - Panels:
        - Stack Tree
        - Execution Stack
        - Execution Log
        - Source
        - Execution Overview
    - Name: **Execution Details**


# Solution

[Generate and Analyze Logs || Developer Console Basics - wonder studies - YouTube](https://www.youtube.com/watch?v=B9LIIbRWguk)

# 🛠 Step 1: Set Apex Logging Level to FINEST
1. In Setup, search for Debug Log or go to Debug Logs directly.

2. Click Debug Levels.

3. Find or create a debug level named SFDC_DevConsole.

4. Set the Apex Code level to FINEST.

5. Save your changes.

# 🚀 Step 2: Execute the EmailManager Apex Class
1. Open the Developer Console.

2. Go to Debug > Open Execute Anonymous Window.

3. Enter and run:

``` apex
EmailManager.sendMail('your_email@example.com', 'Flight Path Change',
       'Mission control 123: Your flight path has been changed.');
```
Replace your_email@example.com with your real email address.

4. Make sure the log is generated — check Logs tab or use Debug > View Log Panels.

# 🧩 Step 3: Create Your Perspective
1. In Developer Console, go to Debug > Perspectives > Manage Perspectives.

2. Click New.

3. Name it: Execution Details.

4. Add the following panels:

    - Stack Tree

    - Execution Stack

    - Execution Log

    - Source

    - Execution Overview

5. Save the perspective.



