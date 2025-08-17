# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create a method for inserting accounts.**

To pass this challenge, create an Apex class that inserts a new account named after an incoming parameter. If the account is successfully inserted, the method should return the account record. If a DML exception occurs, the method should return null.

* The Apex class must be called AccountHandler and be in the public scope
* The Apex class must have a public static method called insertNewAccount
    - The method must accept an incoming string as a parameter, which will be used to create the Account name
    - The method must insert the account into the system and then return the record
    - The method must also accept an empty string, catch the failed DML and then return null


# Solution

``` apex
public class AccountHandler {
    public static Account insertNewAccount(String accountName) {
        try {
            Account acc = new Account(Name = accountName);
            insert acc;
            return acc;
        } catch (DmlException e) {
            return null;
        }
    }
}

```

# 🔍 Breakdown:

* public class AccountHandler: Declares the class as accessible to other parts of your org.

* public static Account insertNewAccount(String accountName): Accepts a string to name the account.

* Inside the try block:

    - Creates an Account with the provided name.

    - Attempts a DML insert.

    - Returns the inserted record on success.

* The catch block handles any DML exception (including inserting with an empty name), returning null gracefully.
