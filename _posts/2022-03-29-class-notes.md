---

layout: post
title: AppDev2 notes from lecture 1
___
#### Quick notes

- Generators give us a head start on boiler plate code. There are many available through various GEMs.
- `Post` vs. `get` methods for routes:
  - `get` is the default routing method for `routes.rb`
  - a look into the server log reveals that `get` stores the request in a query string, whereas `post` stores in the headers
  - the tradeoff is that `get` supports text only (because the query string must fit into the URL), and there is therefore a length limit

- RESTful routes:
 - widely accepted naming convention for routes that we should adopt
 - **never** use CRUD function names in URLs:
     - `post("/movies")` vs `post("/insert_movies")`
     - `post("/movies")` is a distinct route from `get("/movies")`
 - **HTTP verbs indicate what we want to do with the resource**
     - `get`, `post`, `patch`, `delete`, etc

---
#### Rails shortcuts
- `.html.erb` is a default file type and we do not need to specify it in our view templates or routes
- the `render` method does not require a Hash literal
    - `render("movies/new")` rather than `render({ :template => "movies/new.html.erb" })`
- if the name of the view template folder matches the name of the controller exactly, we can omit it in the file path
- if the name of the template matches the name of the action, we do not need the render statement at all
- the golden 7 routes

---
#### Rails resources
 - we no longer need to write out routes for our 7 standard RESTful routes (!!!)
     - `resources(:directors)` will populate our 7 conventional routes automatically for the resource / data table in question (`directors` in this instance)
     - do this in the `routes.rb` file
 - most of our routes will just involve these **resource declarations**, but we will still need to create one-off routes here and there for specific actions we need to perform outside of the golden 7, basic CRUD functions

---
#### Rails `render` vs `redirect`
 - use and abuse instance variables when multiple actions are using the same view template
     - `@the_movie = Movie.new` is a hack for a view template that inserts a new movie into the database, for instance
 - rather than redirecting on a form submission error, a more friendly UX is to re-render the form with the user's inputs pre-filled into the form fields so that they may make whichever adjustments are needed to pass the validation requirements to be created into the database with our CRUD flow
     - we need to display our error messages on the appropriate view template for the user so they know what to edit...

---
#### Next steps
 - Ruby Koans assignment

