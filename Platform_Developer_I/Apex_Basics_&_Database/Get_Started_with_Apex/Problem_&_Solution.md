# Problems

**Get Ready**

You’ll be completing this unit in your own hands-on org. Click Launch to get started, or click the name of your org to choose a different one.

**Your Challenge**

**Create an Apex class with a method that returns a list of strings**

Create an Apex class with a method that returns a list of formatted strings. The length of the list is determined by an integer parameter.

* The Apex class must be called StringListTest and be in the public scope
* The Apex class must have a public static method called generateStringList
* The generateStringList method must return a list of strings
    - The method must accept an incoming Integer as a parameter, which will be used to determine the number of returned strings
    - The method must return a list of strings. Each element in the list must have the format Test n, where n is the index of the current string in the list. For example, if the input is 3, then the output should be ['Test 0', 'Test 1', 'Test 2']. Remember that in Apex, the index position of the first element in a list is always 0.


# Solution

Here's a complete Apex class that fulfills all the criteria you've outlined:

[Get Started with Apex || Apex Basics & Database](https://www.youtube.com/watch?v=JRWFhhl2_TM)

``` apex

public class StringListTest {
    public static List<String> generateStringList(Integer size) {
        List<String> result = new List<String>();
        for (Integer i = 0; i < size; i++) {
            result.add('Test ' + i);
        }
        return result;
    }
}

```

# ✨ Breakdown:
* public class StringListTest: Makes the class accessible across your org.

* public static List<String> generateStringList(Integer size): Declares the method with static scope for direct invocation and takes an integer to control the number of strings.

* Inside the loop: Each string is formatted as 'Test n' with n being the index, starting from 0.

This will return a list like ['Test 0', 'Test 1', 'Test 2'] when generateStringList(3) is called.
