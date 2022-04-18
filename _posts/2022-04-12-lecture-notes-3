---

layout: post
title: Lecture3 notes from 2App2Dev

---


## Git branching

Never re-write the history of `main`! Use `$ git revert` to create a new commit onto `main` that reverses any changes pushed in the last `commit` (rather than deleting that commit).

---

## Rails Scaffold generator

This generator will replace `draft:resource` for us. 
- Automatically calls `resources :books` into `routes.rb`, which gives the seven golden routes.
- Adds JSON functionality and view templates
- For partial view templates (like what is generated for the `new` and `update` pages' form by the scaffold generator), begin the name with an underscore to differentiate it from our primary view template.

---

## Rails Devise generator

This generator will replace `draft:account` for us, rather than trying to write all of the user code ourselves (password reset emails, etc). Now we just need to use the `current_user` method to filter actions based on access permissions (general users vs admins, for example).

---

## Rails syntax
Some interesting ways to shorthand Arrays:
- %i[ symbol1 symbol2 symbol3 ] yields an array of symbols
- %w[ string1 string2 string3 ] yields an array of strings



---

## Quick intro to HTML vs JSON
The `respond_to` block introduced by the scaffold generator calls `format.html` and `format.json` 
- server-rendered response: server renders HTML and returns it to the browser (what we did in AppDev1, link-based apps)
    - **renders a resource from the app database**

- client-rendered response: HTML is rendered on the client by reading and parsing the JSON template and drawing the screen with JavaScript
    - **very reactive, single webpage apps**



