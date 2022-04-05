---

layout: post
title: AppDev2 notes from lecture 2

---
##### CSRF protection in Rails
- `Rails` includes protection from "cross-site request forgery" attack vectors
    - for a `form`, create a hidden input with `name` = `authenticity_token` and `value` = `<% form_authenticity_token %>`
    - include on all forms that use a `post` or `patch` method; allows for authenticated user to execute desired action

---

##### A few loose ends
###### ActiveRecord_Relations
- use `[]` to index arrays and ActiveRecord_Relations rather than `.at()` (which is not a method natively supported for Relations)
    - can also use with a Hash with desired key in the brackets, though `.fetch` is still optimal for handling `nil` situations  
- the `find_by` method called on an ActiveRecord returns the first matching instance for the input parameter
    - replaces the old `.where` and `.at` method chain used in AppDev1
    - returns a `nil` if there is no record matching the specified criteria
    - use the `raise` keyword to throw an error with a descriptive name and generate a 404 for the user in the case of `nil` records 
- alternately, use the `find` method to raise a `RecordNotFound` exception in the instance of no matching records and have Rails automatically generate a 404 for the user
    - this method only searches by `id`, so we are guaranteed a unique record if one exists matching the criteria

###### RESTful syntax
- must use `data-method="patch"` or `data-method="delete"` in links
    - `_method="patch"` etc for forms 
- the `link_to` method will be used rather than hand-writing HTML `<a>` tags
    -  more concise and less error-prone way of generating links
    -  similar with `form_with` for automating writing forms 
