# Problems & Solution

# 1 Once a project is underway, what important step must a developer do before making changes?

A Create a new GitHub repo for their code, then create a branch.
B Deploy any changes from the repository into their Developer sandbox.
C Create their own Salesforce DX project.
D Refactor all the code provided by other developers.

## ANSWER

# ✅ 1. Once a project is underway, what important step must a developer do before making changes?
**Answer: B – Deploy any changes from the repository into their Developer sandbox.**

* A Salesforce DX project is the foundation for source-driven development. It organizes code, metadata, tests, and configuration into a structured directory that works seamlessly with Salesforce CLI and source control.

* Before making changes, a developer should set up their own DX project to ensure all future changes are trackable, modular, and deployable.


# 2 After a developer makes a change in a sandbox org, what step is required to share it with others?

A Create a new branch in the source control system and a new DX project.
B Test the changes after pushing them to a clean testing org.
C Deploy the changes to every teammate's sandbox.
D Retrieve the changes from their sandbox to the project in the source repository.

## ANSWER

# ✅ 2. After a developer makes a change in a sandbox org, what step is required to share it with others?

**Answer: D – Retrieve the changes from their sandbox to the project in the source repository**

* Changes made in a sandbox need to be pulled into the local DX project, then committed to the shared source repository. That’s how version control and collaboration are maintained.
