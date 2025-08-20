# Problems & Solution

# 1 What is a key benefit of asynchronous processing?

* A Higher governor and execution limits
* B Unlimited number of external callouts
* C Override organization-wide sharing defaults
* D Enabling turbo mode for transactional processing

## ANSWER

# ✅ 1. What is a key benefit of asynchronous processing?

**Correct Answer: A Higher governor and execution limits**

* Asynchronous processes (like Batch Apex, Queueable Apex, and Future methods) benefit from higher limits compared to synchronous Apex.

* They’re designed for long-running operations such as processing large data volumes or making callouts, without blocking the user experience.


# 2 Batch Apex is typically the best type of asynchronous processing when you want to:

* A Make a callout to a web service when a user updates a record.
* B Schedule a task to run on a weekly basis.
* C Update all records in your org.
* D Send a rickroll email to a contact.

## ANSWER

# ✅ 2. Batch Apex is typically the best type of asynchronous processing when you want to:

**Correct Answer: C Update all records in your org**

* Batch Apex is optimized for handling massive datasets by breaking them into manageable chunks.

* It's ideal for operations like data cleansing, recalculating values across objects, or bulk updates.