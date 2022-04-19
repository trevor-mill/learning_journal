---

layout: post
title: Notes from working through Photogram-industrial

---

This exercise entailed building an industrial-grade version of Photogram from scratch, making ample use of **helper methods**, **partial templates**, and good **RESTful naming conventions**. Here are a few notes I captured while working through the process, either useful links for future use or various friction points I ran into:

### Data prep and migration

- Already built your database and need to change a default value for a column (or add a column, etc)? _No problem!_ Generate a migration and follow the steps from [this helpful blog post](https://blog.arkency.com/how-to-add-a-default-value-to-an-existing-column-in-a-rails-migration/)!

- `ActiveRecord::Enum` can be used to formally declare the possible values for a given column (like follow request status in Photogram!). Enum stores either strings or integers for column values, assigned to specified keys. This also allows for `?` and `!` instance methods, and automatically defines positive and negative scopes that can later be used to help filter lists of records.

- Ruby Faker is a helpful gem to use for data rake tasks! Check it out [here](https://github.com/faker-ruby/faker).

---

### Routing, partial templates, and ActiveRecord queries
- Word to the wise: the more we use partial templates, the more coupled our code becomes. Ensure that changes to a partial have no unintended consequences to others' code (use automated tests, ideally).

- For routes where we intend for the user to return to the page they were just interacting with (posting comments, adding likes, etc), use the `redirect_back` method rather than `redirect` in the route controller. This method takes a `fallback_location` in case there is an error and Rails cannot determine the user's previous page, as well as any `notice` we want to pass along.

- Routes are executed sequentially top-to-bottom in the routes controller; place the most ambiguous routes at the very bottom of the controller to prevent Rails from misinterpreting the desired route (`get "/:username"` near the top of the controller might try to take us to a user profile called "photos" when we try to follow the route for `"/photos"`, for instance).

- When querying for records, use the `.find_by!` method to throw a 404 error if there is no record found, rather than a 500 error for a `nil` value getting passed from the `params` hash further down into the code.

---
### Questions
1. What if we make a commit to the wrong `git` branch? (Committed front end changes to back end git, for example). Safest and most efficient way to assign commit to proper branch?
2. Purpose of `as: :XYZ` in `routes.rb`?
3. Using partials for followers / following? 
