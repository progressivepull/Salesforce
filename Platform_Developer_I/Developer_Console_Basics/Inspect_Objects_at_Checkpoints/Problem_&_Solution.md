# Problems

**Set Checkpoints to Find Errors in Your Code**

Set a checkpoint in the EmailMissionSpecialist class. Then execute the class and analyze the objects logged at the checkpoint.

**Pre-Work**

Make sure that line 12 of your EmailMissionSpecialist Apex class contains this code:
**Messaging.SendEmailResult[] results = Messaging.sendEmail(**

If it doesn't, replace the contents of EmailMissionSpecialist.apxc with the EmailMissionSpecialist class code provided in Unit 2: Navigate and Edit Source Code.

* In the EmailMissionSpecialist class, set a checkpoint on line 12
* Using your own email address, execute the EmailMissionSpecialist class in the Execute Anonymous window
* Observe the checkpoint results and see the values of the objects in memory (we won’t check this)


# Solution

# ✅ Step 1: Verify Line 12 in Your EmailMissionSpecialist Class

Ensure this exact line exists:

``` apex
Messaging.SendEmailResult[] results = Messaging.sendEmail(new Messaging.Email[] { email });

```
If it’s missing or different, update your class with the version provided in Unit 2.

# 📍 Step 2: Set a Checkpoint on Line 12
1. Open Developer Console.

2. Navigate to EmailMissionSpecialist.apxc.

3. Right-click the line 12 (or click in the left margin) to Set Checkpoint.

You should now see a red check mark next to that line.

# 🚀 Step 3: Execute the Class in Anonymous Window

1. Open Execute Anonymous Window from Debug > Open Execute Anonymous Window.

2. Run:

```apex
EmailMissionSpecialist.sendEmail('your_email@example.com');
```
Replace 'your_email@example.com' with your actual address.

3. Click Execute.

# 🔎 Step 4: Analyze Objects Logged at Checkpoint
1. Go to the Checkpoints tab in the Developer Console.

2. Find the execution tied to your recent run.

3. Double-click the checkpoint entry to view memory state:

    - Inspect the Messaging.SendEmailResult[] results variable.

    - Look for values like isSuccess(), getErrors(), or other details about the email delivery outcome.


