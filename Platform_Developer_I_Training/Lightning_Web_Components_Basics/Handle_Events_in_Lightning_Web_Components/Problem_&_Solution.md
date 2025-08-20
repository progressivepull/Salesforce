# Problems & Solution

# 1 Which of the following nests one component inside another?

A ```<c-detail product-id={selectedProductId}></c-detail>```

B ```import { LightningComponent, api } from 'detail';```

C ```import { detail, api } from 'lwc';```

D ```<div class="detail">```


E ```<template if:true={product}>```


## ANSWER

# ✅ 1. Which of the following nests one component inside another?

**Answer: A**

```html
<c-detail product-id={selectedProductId}></c-detail>
```

* This is a classic example of **component nesting** in Lightning Web Components (LWC), where the **c-detail** component is used inside another component’s template.

* The **product-id** attribute passes data down via a public **@api** property.

# 2 Which of the following describes an event handling pattern in a complex component app?

A Properties are dispatched up from child to parent, then events are passed down from parent to child.

B Events are dispatched up from child to parent, then modules are passed down from parent to child.

C Events are dispatched up from child to parent, then properties are passed down from parent to child.

D Events are dispatched up from child to parent, then other children listen to the parent component.

E Events are dispatched down from parent to all the child components.

## ANSWER
 

 # ✅ 2. Which of the following describes an event handling pattern in a complex component app?

**Answer: C**

Events are dispatched up from child to parent, then properties are passed down from parent to child.

* This is the standard **unidirectional data flow** pattern in LWC:

    - Child components send information **upward** via custom events.

    - Parent components handle those events and update shared state, which is then passed **downward** via properties (**@api** bindings).

