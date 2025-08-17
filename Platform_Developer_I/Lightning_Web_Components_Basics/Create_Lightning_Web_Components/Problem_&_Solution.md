# Problems & Solution

# 1 Which of the following is true of the template tag?

* A The template tag imports a module.
* B The template tag is our version of a div tag.
* C The template tag replaces standard components.
* D The template tag contains the HTML for your component.
* E The template tag inserts pre-defined elements.

## ANSWER

# ✅ 1. Which of the following is true of the template tag?

**Answer: D The template tag contains the HTML for your component.**

* In Lightning Web Components (LWC), the <template> tag wraps all the HTML.

* It serves as the root for the component’s markup and enables you to use directives like if:true, for:each, etc.

# 2 What do you have to include in a component's JavaScript file?

* A @api
* B An import statement with the LightningElement wrapper and an export statement with your class name
* C A template tag
* D An import statement with a file path and an export statement with your class name
* E An import statement with the LightningElement wrapper and an export statement that defines your class with the same name as the JavaScript file

## ANSWER

# ✅ 2. What do you have to include in a component's JavaScript file?

**Answer: B An import statement with the LightningElement wrapper and an export statement with your class name**

* Standard format looks like this: 

``` js
import { LightningElement } from 'lwc';

export default class MyComponentName extends LightningElement {}
```
* Class name must match the JavaScript file name (e.g., myComponent.js should define class MyComponent).

