# Problems & Solution

# 1 What is a manifest file (package.xml)?

* A A .zip file that contains all the objects and components to deploy to an org.
* B An XML file that lists the metadata components to deploy to (or retrieve from) an org.
* C A package version of the changes that the development team has made in this release.
* D The inbound change set that Juan deploys to the production environment.

## ANSWER

# ✅ 1. What is a manifest file (package.xml)?
**Answer: B – An XML file that lists the metadata components to deploy to (or retrieve from) an org.**

* The package.xml file is like a manifest or recipe for Salesforce Metadata API deployments.

* It tells the system which components (Apex classes, custom objects, page layouts, etc.) to include when deploying or retrieving metadata.

* It does not contain code itself, and it is not a zip file — it’s the index inside one.


# 2 What is a benefit of using the 'project deploy validate' command?

* A It sets up a quick deploy to your production org, which minimizes disruption to users.
* B It verifies the results of tests that would be executed in a deployment without actually committing any changes to the org.
* C You feel validated that your CLI command knowledge is excellent.
* D A and B.

## ANSWER

# ✅ 2. What is a benefit of using the project deploy validate command?
**Answer: D – A and B**

* A: It prepares a quick deployment, meaning if the validation passes, you can deploy without repeating all the tests.

* B: It verifies your deployment logic and run tests in a staging step — without committing changes to your org.

This is especially helpful for high-stakes deployments where you want to confirm everything will succeed before “pulling the trigger.”