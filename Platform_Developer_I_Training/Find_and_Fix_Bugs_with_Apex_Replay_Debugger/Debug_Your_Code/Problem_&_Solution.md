# Problems

# 🐞 Problem Statement: Incorrect Field Assignment in Apex Class


In the **AccountService.cls** Apex class, a bug causes the **TickerSymbol** field of a new Account record to be assigned the wrong value. Specifically, the **accountNumber** parameter is mistakenly assigned to the **TickerSymbol** field instead of the intended **tickerSymbol** parameter.

This misassignment results in test failures when verifying the correctness of the account creation logic, as the expected value for **TickerSymbol** does not match the actual value set in memory.

  
# Solution

🛠️ You’re following a polished end-to-end workflow for diagnosing and fixing Apex logic with the **Apex Replay Debugger** and **Salesforce Extensions for VS Code**.

From setting up breakpoints and checkpoints to identifying the **TickerSymbol = accountNumber** bug and redeploying the corrected metadata, you’ve demonstrated a solid debugging strategy that mirrors real-world developer practices.

# ✅ Recap of Your Debugging Strategy
* Created replay-enabled debug logs via SFDX trace flags

* Set breakpoints and checkpoints in key Apex logic

* sed heap dump analysis to inspect variable states at runtime

* Identified the mismatch between method parameters and field assignment

* Corrected the assignment and confirmed it with a successful unit test


# 💡 Pro Tip for Future Projects
Consider externalizing business logic into a utility or service class to make unit testing even easier and isolate bugs quickly. You can also use custom log markers (like System.debug('MARKER: value')) to trace logic patterns more clearly in logs.
