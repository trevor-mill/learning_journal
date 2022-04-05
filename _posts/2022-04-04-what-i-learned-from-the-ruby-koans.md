---
layout: post
title: Three things I learned from The Ruby Koans
---

Here are some things I learned from working through [The Ruby Koans](http://rubykoans.com/):

 - test `nil` is treated as `false`
 - incorporate a backslash into strings with quotes: `"Don\'t"` ; alternately, `%(flexible quotes)` work well
 - the shovel operator (`<<`) can also be used to append content to a `string`, but it also modifies the original string, unlike the `+=` concatenation operator
 - escape characters such as `\n` are only reliably interpreted when in double quotes
 - identical symbols are a single internal object, whereas identical variables are unique internal objects
 - object IDs for small integers follow the pattern of `2 * n + 1` 
 - private methods are always called within the context of `self`
 - top-level constants are referenced via double colons (`::C` rather than `C`)
 - subclasses inherit constants from parent classes
 - _every_ statement in `Ruby` returns a value, not just `if` statements
 - `inject` takes as its argument a default value and iterates through a block until the end of the loop
 - a `method` can take a `block` as its argument; this `block` can affect input variables in-line
 - all defined classes ultimately inherit from `Object`, and can invoke parent behavior via `super`
 

---

#### Questions / further study
1. `<<` operator
2. `next` statement
3. using the `?` and `:` to create in-line binary arguments rather than using if-else block



