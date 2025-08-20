# Problems

**Set Checkpoints to Find Errors in Your Code**

Set a checkpoint in the EmailManager class. Then execute the class and analyze the objects logged at the checkpoint.


[Inspect Objects at Checkpoints | Developer Console Basics - Saurabh Infotech Solutions - YouTube](https://www.youtube.com/watch?v=y69GaZsztEk)

**Pre-Work**

Make sure that line 12 of your EmailManager Apex class contains this code:
**Messaging.SendEmailResult[] results = Messaging.sendEmail(**

If it doesn't, replace the contents of EmailManager.apxc with the EmailManager class code provided in Unit 2: Navigate and Edit Source Code.

* In the EmailManagert class, set a checkpoint on line 12
* Using your own email address, execute the EmailManager class in the Execute Anonymous window

* Observe the checkpoint results and see the values of the objects in memory (we won’t check this)


# Solution

# ✅ Step 1: Verify Line 12 in Your EmailManager Class

Ensure this exact line exists:

``` apex
Messaging.SendEmailResult[] results = Messaging.sendEmail(new Messaging.Email[] { email });

```
If it’s missing or different, update your class with the version provided in Unit 2.

# 📍 Step 2: Set a Checkpoint on Line 12
1. Open Developer Console.

2. Navigate to EmailManager.apxc.

3. Right-click the line 12 (or click in the left margin) to Set Checkpoint.

You should now see a red check mark next to that line.

# 🚀 Step 3: Execute the Class in Anonymous Window

1. Open Execute Anonymous Window from Debug > Open Execute Anonymous Window.

2. Run:

add this class

```apex
public class EmailMissionSpecialist {
    // Public method
    public static void sendMail(String address, String subject, String body) {
        // Create an email message object
        Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
        String[] toAddresses = new String[] {address};
        mail.setToAddresses(toAddresses);
        mail.setSubject(subject);
        mail.setPlainTextBody(body);
        // Pass this email message to the built-in sendEmail method
        // of the Messaging class
        Messaging.SendEmailResult[] results = Messaging.sendEmail(
            new Messaging.SingleEmailMessage[] { mail });
        // Call a helper method to inspect the returned results.
        inspectResults(results);
    }
    // Helper method
    private static Boolean inspectResults(Messaging.SendEmailResult[] results) {
        Boolean sendResult = true;
        // sendEmail returns an array of result objects.
        // Iterate through the list to inspect results.
        // In this class, the methods send only one email,
        // so we should have only one result.
        for(Messaging.SendEmailResult res : results) {
            if(res.isSuccess()) {
                System.debug('Email sent successfully');
            } else {
                sendResult = false;
                System.debug('The following errors occurred: ' + res.getErrors());
            }
        }
        return sendResult;
    }

}
```


```apex
EmailMissionSpecialist.sendMail('your_email@example.com', 'Flight Path Change',
       'Mission control 123: Your flight path has been changed.');
```

Replace 'your_email@example.com' with your actual address.

3. Click Execute.

# 🔎 Step 4: Analyze Objects Logged at Checkpoint
1. Go to the Checkpoints tab in the Developer Console.

2. Find the execution tied to your recent run.

3. Double-click the checkpoint entry to view memory state:

    - Inspect the Messaging.SendEmailResult[] results variable.

    - Look for values like isSuccess(), getErrors(), or other details about the email delivery outcome.


