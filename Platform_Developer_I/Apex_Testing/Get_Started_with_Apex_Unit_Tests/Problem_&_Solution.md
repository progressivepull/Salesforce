# Problems

**Create a Unit Test for a Simple Apex Class**

Create a simple Apex class to test if a date is within a proper range, and if not, returns a date that occurs at the end of the month within the range. You'll copy the code for the class from the Get Ready for the Hands-on Challenge section. Then write unit tests that achieve 100% code coverage.


* Create an Apex class:
    - Name: **VerifyDate**
    - Code: C**opy from Get Ready for the Hands-on Challenge section above**
* Place the unit tests in a separate test class:
    - Name: **TestVerifyDate**
    - Goal: 100% code coverage
* Run your test class at least once


# Solution

# 📄 Apex Class: VerifyDate

``` apex
public class VerifyDate {
    public static Date getValidDate(Date inputDate, Date startDate, Date endDate) {
        if (inputDate >= startDate && inputDate <= endDate) {
            return inputDate;
        } else {
            return Date.newInstance(endDate.year(), endDate.month(), endDate.daysInMonth());
        }
    }
}

```
This method checks whether inputDate is within the range defined by startDate and endDate. If it’s outside the range, it returns the last day of the endDate's month.

# 🧪 Test Class: TestVerifyDate

``` apex
@isTest
public class TestVerifyDate {
    @isTest
    static void testDateWithinRange() {
        Date input = Date.newInstance(2024, 5, 15);
        Date start = Date.newInstance(2024, 5, 1);
        Date end = Date.newInstance(2024, 5, 31);

        Date result = VerifyDate.getValidDate(input, start, end);
        System.assertEquals(input, result);
    }

    @isTest
    static void testDateOutsideRangeBefore() {
        Date input = Date.newInstance(2024, 4, 30);
        Date start = Date.newInstance(2024, 5, 1);
        Date end = Date.newInstance(2024, 5, 31);

        Date result = VerifyDate.getValidDate(input, start, end);
        System.assertEquals(Date.newInstance(2024, 5, 31), result);
    }

    @isTest
    static void testDateOutsideRangeAfter() {
        Date input = Date.newInstance(2024, 6, 1);
        Date start = Date.newInstance(2024, 5, 1);
        Date end = Date.newInstance(2024, 5, 31);

        Date result = VerifyDate.getValidDate(input, start, end);
        System.assertEquals(Date.newInstance(2024, 5, 31), result);
    }
}
```
# ✅ What You Achieve
* 100% test coverage across all branches of logic.

* Edge-case handling both before and after the range.

* You can now run this test class in the Developer Console or via CLI and verify the results in the debug log.

