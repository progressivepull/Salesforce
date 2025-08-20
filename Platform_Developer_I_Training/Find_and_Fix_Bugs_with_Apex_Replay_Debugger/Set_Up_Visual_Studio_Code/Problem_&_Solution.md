# Problems

# 🐞 Problem Statement: Environment Setup Required to Enable Apex Replay Debugging
To use the Apex Replay Debugger effectively within Visual Studio Code, a proper development environment must be configured. The current machine lacks one or more of the following components:

* A supported version of Salesforce CLI

* Visual Studio Code configured with Salesforce Extension Pack

* A compatible Java Development Kit (JDK), such as JDK 21

* A properly set JAVA_HOME or VS Code Apex Java Home configuration pointing to the correct JDK path

Without this setup, features like Apex code debugging, syntax highlighting, and test execution through Salesforce DX cannot be accessed. The goal is to establish and verify a complete development setup, ensuring Apex Replay Debugger runs smoothly in support of Salesforce application testing and debugging workflows.

  
# Solution

Here's a complete solution summary for setting up Visual Studio Code and configuring Apex Replay Debugger for Salesforce development:

# ✅ Solution: Set Up Apex Replay Debugger in Visual Studio Code

# 🧰 1. Install and Update Salesforce CLI
* Download from Salesforce CLI.

* Open Terminal or Command Prompt and run:

``` bash
sf update
```
* Confirm output includes: Updating CLI...

# 💻 2. Install and Launch Visual Studio Code
* Download from https://code.visualstudio.com/Download

* Install and open Visual Studio Code after setup.

# 🧩 3. Install Salesforce Extension Pack
* In VS Code, go to View > Extensions

* Search for: salesforce extension pack

* Click Install or Update

* Restart VS Code to activate changes

# ☕ 4. Install Java Development Kit (JDK)
* Download and install JDK 21 (Recommended) Acceptable versions: 21, 17, or 11

* Confirm default installation path:

    - Windows: C:\Program Files\Java\jdk-21

    - MacOS: /Library/Java/JavaVirtualMachines/jdk-21.0.1.jdk/Contents/Home

# 🔧 5. Configure Java Home in VS Code
* Go to:

    - Windows/Linux: File > Preferences > Settings

    - MacOS: Code > Settings > Settings

* Search: apex java

* Set the value for:

```
salesforcedx-vscode-apex.java.home
```
➜ Enter the full JDK directory path

* Relaunch VS Code
* Run:
  
``` bash
java -version

```
➜ Confirm it reflects the JDK version you installed
