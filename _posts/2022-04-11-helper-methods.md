---

layout: post
title: Helper methods for routes and forms

---

## Route helper methods

#### Route prefixes
We can now name routes with a `prefix`, which can then be called with the `_path` or `_url` helper methods. **Only refer to URLs with this name elsewhere in the codebase**, as this allows us to go back and change the path once from the `routes.rb` file rather than every single time the path appears in the code. This adds a high degree of robustness to the codebase.

Prefixes can be viewed using the `rails routes` rake task, or by navigating from the `bin/server` webpage to the `/rails/info` URL to see all routes (names will be in the first column under "Prefix/URL"). A named route looks like this (on `routes.rb`, "details" is the desired path prefix):

```
get "/movies/:id" => "movies#show", as: :movie
```


#### Streamlining controller codebase syntax
To further streamline the codebase, we can abbreviate controller syntax to omit `render` arguments wherever the view template folder name matches the controller Class name **and** the view template name and controller method name match. If the view template name and defined method name do not match, a simple `render "template name"` argument still helps to streamline the syntax.

#### `link_to` helper method
This helper method allows us to avoid writing `<a>` elements within embedded Ruby templates. Before and after:

```
<a href="<%= new_movie_path %>">Add a new movie</a>   #before
<%= link_to "Add a new movie", new_movie_path %>   #after
```

This can be streamlined if we have a named route helper method for the Class in question, where an ActiveRecord object can be passed into the argument instead:

```
<%= link_to "Add a new movie", a_movie %>
```

As long as RESTful routes are created and everything has been built conventionally, _voila_! This adds a lot of flexibility when working with new team members, for example; they don't need to know our URLs as long as we have followed convention in setting up the routes.

---
## Form helper methods

#### `form_with`
This helper method creates a robust form that automatically includes the CSRF-protection we normally need to manually add to the form (the authenticity token). This helper method does require a code block, with the form HTML inside the block.

Rather than passing a `url` argument into the method, we can insert a `:method @instance_variable` argument for forms responsible for creating new Records. _Wow_! (P.S. RESTful routes are very useful here...). **Using `form_with` in this fashion takes a `|form|` block variable and returns nicely nested params hashes**, making it ideal for our "create" actions.

#### Others
- `label_tag`
- `text_field_tag`
- `text_area_tag`
- `button_tag`

These methods take the title of the form field as the first argument (as a symbol), and then any copy you might want in the second argument (as a string or variable). Any additional HTML attributes we want included (an id for the form field, for instance) can be passed into the helper method as a hash after the other arguments.

For working with ActiveRecords, we can use the `find_by` helper method to streamline code in the controller (removes the `.where`, `.first`, etc). If we're just trying to match by an id, we can simply use the `find` helper method, which takes an integer as its lone argument. Of note: `find_by` returns `nil` if a record does not exist, whereas `find` raises an exception, which can be handy in production (exceptions reroute the user to a 404 rather than a 500).

To further play with forms, we can append `[]` to the name of an `input`, and the param is then passed into an Array. Multiple inputs with the same name return to the same Array, which allows some interesting functionality such as looping through parameters, nested hashes, implementing check boxes, etc. This can be particularly helpful in creating new Records, as we can use a Hash that matches the database columns and pass it into the `.new` argument. This process is called **mass assignment**, and we need to specify which attributes we will permit to be mass assigned. This is known as _whitelisting_. 

---
## Bonus
`resources :model_name` will generate all seven "golden routes" for the new model, when generating a model from scratch.

---
## Questions
1. How to use `link_to` method to re-write an `<a>` tag with `data-method="delete"`, etc? (movies show template, line ~17)
    - _Add them to the helper method with a `method: :argument` at the end._ 
