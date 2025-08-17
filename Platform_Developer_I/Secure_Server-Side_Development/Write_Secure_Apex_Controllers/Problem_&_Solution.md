# Problems & Solution

# 1 What does the “without sharing” keyword do in the context of Apex classes?

A Enforces sharing rules for the current user

B Bypasses sharing rules for the current user

C Specifies inherited sharing for the current user

D Enforces CRUD access

## ANSWER

# ✅ 1. What does the “without sharing” keyword do in the context of Apex classes?

**Answer: B – Bypasses sharing rules for the current user**

* When an Apex class is declared with **without sharing**, it **ignores org-wide defaults, role hierarchy, and sharing rules**.

* This allows access to all records the running user has permission to see via the profile or permission set, even if they wouldn't normally have record-level access.

# 2 When should developers use the "with sharing" keyword in Apex classes?

A When they want to bypass sharing rules for the current user

B When they want to enforce CRUD access

C When they want to specify inherited sharing for the current user

D When they want have sharing rules enforced on DML functions

## ANSWER

# ✅ 2. When should developers use the "with sharing" keyword in Apex classes?

**Answer: D – When they want to have sharing rules enforced on DML functions**

* The **with sharing** keyword ensures **record-level security** is respected based on the current user’s context.

* This is especially important for classes that expose data via DML operations or display sensitive records to avoid unintentional access.