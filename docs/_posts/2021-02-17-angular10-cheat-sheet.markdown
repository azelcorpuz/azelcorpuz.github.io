---
layout: post
title:  "Angular 10 Cheat Sheet"
date:   2021-02-15 23:14:00 +0800
categories: tools
---

## Reactive vs Template forms
Reactive (model driven):
1. Modeling your form in objects of
   * FormGroup - composed of 1 or form control
   * FormControl - field
2. More advance, more control
   * like you can validate/reset all at once - because of grouping
3. Easier to test as everthing is in javascript code - including validations
4. No need to use `ngModel` to bind - just use `formControlName` and `formGroup` name
    * though it can be used together with `ngModel`
    * need to confirm if `[formGroup]` kind of 2 way binded because as per my testing, it seems the data i put in the view is binded to the `FormControl` object, and if i set a data on the `FormControl` object, i can see it reflecting to the view
5. Recommended for new applications

Template (template driven):
1. Old way - you need to use `[(ngModel)]`

## Objects
### Modules
* Way of grouping the components - good for lazy loading, if other module is not needed - it will not be loaded
* `Declarations` is to declare member components - to be able to use within the module (??)
* `Import` is to be able to use member components of other module
* `Export` is to export member components so that once module is imported by other module so the exported component can be use by other module   

## Bindings
1. `[]` - Property binding - one-way from data source to view target
   * can use `bind-` instead of `[]`
2. `()` - Event binding - one-way from view target to data source
   * can use `on-` instead of `()`
3. `[()]` - Two way Binding - banana in a box
   * can use `bindon-` instead of `[()]`

