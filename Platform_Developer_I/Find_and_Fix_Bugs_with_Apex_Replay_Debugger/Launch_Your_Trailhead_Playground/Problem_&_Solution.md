# Problems

# 🐞 Problem Statement: Misassignment Bug in Apex Class
The **AccountService.cls** Apex class contains a bug in its **createAccount** method. Specifically, the method incorrectly assigns the **accountNumber** parameter to the TickerSymbol field of a new **Account** record, rather than assigning the intended **tickerSymbol** parameter. This results in failed unit tests when validating the correctness of the account creation logic.

The objective is to identify and resolve this bug using Salesforce DX tools in Visual Studio Code—leveraging Apex Replay Debugger, breakpoints, and checkpoints to inspect variable values during test execution.

  
# Solution

Here's a condensed summary of the solution process you’d follow in this Trailhead project, focusing on using Apex Replay Debugger and Visual Studio Code:


# 🛠️ Project Solution Summary: Apex Replay Debugger Workflow
1. Launch Your Trailhead Playground
* Create a new Trailhead Playground to work in a safe Salesforce environment.

2. Prepare Your Codebase
* Open Visual Studio Code.

* Load your Apex classes into a Salesforce DX (SFDX) project.

* Ensure the buggy class (e.g., AccountService.cls) is present and deployed.

3. Run Apex Tests and Trigger Debug Logs
* Use Command Palette: SFDX: Run Apex Tests → Choose AccountServiceTest

* Note the failure and collect the debug log.

4. Set Breakpoints and Checkpoints
* In AccountService.cls:

    - Set a breakpoint on a key execution line (newAcct = new Account(...))

    - Set a checkpoint on a return line to capture variable values.

* Run: SFDX: Toggle Checkpoint and SFDX: Update Checkpoints in Org

5. Enable Replay Debugging
* Run: SFDX: Turn On Apex Debug Log for Replay Debugger

* Re-execute tests to generate new logs.

6. Analyze the Bug with Apex Replay Debugger
* Download debug logs: SFDX: Get Apex Debug Logs

* Launch debugger: SFDX: Launch Apex Replay Debugger with Current File

* Step through code using breakpoints, watch variable states

* Identify mismatch (e.g., TickerSymbol = accountNumber instead of TickerSymbol = tickerSymbol)

7. Fix and Redeploy the Bug
* Update Apex class with correct assignment.

* Deploy: SFDX: Deploy This Source to Org

8. Verify Fix
* Rerun Apex tests: SFDX: Run Apex Tests → Confirm passing result

# 🎯 Learning Outcomes
* Hands-on experience with Apex testing and debugging

* Using Visual Studio Code with Salesforce CLI tools

* Applying breakpoints, checkpoints, and Replay Debugger effectively