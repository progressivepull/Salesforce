# Problems

# 🐞 Problem Statement: Incorrect Field Assignment in Apex Method

The **AccountService** class includes a method named **createAccount** designed to initialize and return an **Account** record using three parameters: **accountName**, **accountNumber**, and **tickerSymbol**. However, the method incorrectly assigns the **accountNumbe**r value to the **TickerSymbol** field instead of the intended **tickerSymbol** parameter.

This logic error causes the unit test **should_create_account()** in **AccountServiceTest.cls** to fail. The test expects the **TickerSymbol** to match the value **"CRM"**, but the code mistakenly sets it to **"SFDC"**, the account number. The bug needs to be diagnosed and resolved using Apex Replay Debugger in Visual Studio Code.

  
# Solution

Here’s your complete solution summary for setting up Apex Replay Debugger in Visual Studio Code and preparing the debugging environment:

# 🛠️ 1. Create the Salesforce DX Project
* Open Visual Studio Code.

* Launch the Command Palette: Ctrl+Shift+P (Windows/Linux) or Cmd+Shift+P (macOS)

* Run: SFDX: Create Project

* Choose: Standard template

* Name the project: debugger-project

* Choose a local folder to create the project.

VS Code will reload with the new project opened. Check force-app/main/default/classes — it’ll be empty for now.

# ✍️ 2. Create the Apex Class
* Right-click the classes folder → SFDX: Create Apex Class

* Enter name: AccountService

* Replace contents of AccountService.cls with:

``` apex
public with sharing class AccountService {
  public Account createAccount(String accountName, String accountNumber, String tickerSymbol) {
    Account newAcct = new Account(
      Name = accountName,
      AccountNumber = accountNumber,
      TickerSymbol = accountNumber // intentional bug 🐞
    );
    return newAcct;
  }
}

```
Don't fix the bug yet — it's there for debugging practice!

# 🧪 3. Create the Apex Test Class
* Again, right-click the classes folder → SFDX: Create Apex Class

* Name: AccountServiceTest

* Replace contents of AccountServiceTest.cls with:

``` apex
@IsTest
private class AccountServiceTest {
  @IsTest
  static void should_create_account() {
    String acctName = 'Salesforce';
    String acctNumber = 'SFDC';
    String tickerSymbol = 'CRM';
    Test.startTest();
      AccountService service = new AccountService();
      Account newAcct = service.createAccount(acctName, acctNumber, tickerSymbol);
      insert newAcct;
    Test.stopTest();
    List<Account> accts = [SELECT Id, Name, AccountNumber, TickerSymbol FROM Account WHERE Id = :newAcct.Id];
    Assert.areEqual(1, accts.size(), 'should have found new account');
    Assert.areEqual(acctName, accts[0].Name, 'incorrect name');
    Assert.areEqual(acctNumber, accts[0].AccountNumber, 'incorrect account number');
    Assert.areEqual(tickerSymbol, accts[0].TickerSymbol, 'incorrect ticker symbol');
  }
}

```
# 🔐 4. Authorize Your Org
* Open Command Palette → SFDX: Authorize an Org

* Choose login URL (Production or Project Default).

* Enter alias: debuggerOrg

* Log in to your Trailhead Playground in the browser.

* After logging in, you’ll see output: Successfully authorized <username> with org ID <orgid>
