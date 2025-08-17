# Problems
## Create an Apex class that returns accounts
* Create an Apex class that returns a List of Account objects for a user-specified state.
  
* Create an Apex class that contains a static method:
    - Name: AccountUtils
    - Method name: accountsByState
    - The method must return the ID and name of all Account objects that match the BillingState for the state abbreviation passed to the method
  
# Solution

This Apex class AccountUtils provides the required static method accountsByState that returns a list of Account records (Id and Name only) for a given state abbreviation.

## AccountUtils.cls 

``` apex
public class AccountUtils {
    /**
     * Returns a list of Account objects (Id and Name only) matching the given state abbreviation.
     * @param stateAbbr The BillingState abbreviation to filter Accounts.
     * @return List<Account> with only Id and Name fields populated.
     */
    public static List<Account> accountsByState(String stateAbbr) {
        if (String.isBlank(stateAbbr)) {
            return new List<Account>();
        }
        // Query only Id and Name for accounts matching the BillingState
        return [
            SELECT Id, Name
            FROM Account
            WHERE BillingState = :stateAbbr
        ];
    }
}
```
In the **Developer Console** go to **Debug -> Open Execute Anonymous Window** and **Excute** the following code. 


## APEX 
``` apex
List<Account> caAccounts = AccountUtils.accountsByState('CA');
for (Account acc : caAccounts) {
    System.debug(acc.Id + ' - ' + acc.Name);
}
```

