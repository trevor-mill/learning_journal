#### Key takeaways
- There are no restrictions to the number of assertions allowed by a test; a test only passes when all assertions are satisfied.
- **Test-Driven Development (TDD)**: write a test that fails for a desired functionality, write the code that adds the desired functionality, ensure that test passes
- Use the test database when testing. _Please_.
- Don't forget `follow_redirect!` if there are subsequent requests after a redirect is followed in the test.

---
#### Key resources
- assertions that can be used with `Minitest`: [here](http://docs.seattlerb.org/minitest/Minitest/Assertions.html).

---
#### Introduction to testing
Rails testing support allows a programmer to:
- ensure code maintains desired functionality after refactoring or other changes
- simulate user browser requests to test application's response

Every Rails applicaiton has three environments by default: development, test, and production. Within the test environment, `test_helper.rb` is the default configuration for tests, and should be `require`d for every test written by the programmer (`require "test_helper"`). Rails also includes a `test` method that takes a test name and block of code, allowing for more easily-readable test definitions. Additionally, test assertions provide an optional message parameter to make failure messages more readable.

Tests can be run all at once using the `bin/rails test` command, or singularly by including the desired test file name after the command and/or appending a specific line number or test method name. By default, system tests are not included in `bin/rails test` and should instead be called with `bin/rails test:system` or `bin/rails test:all`.

---
#### The test database
Good tests require sample data, or "_fixtures,_" which are written in YAML formatting to make them more easily readable (these fixtures take the `.yml` extension). We can then use an ERB to embed a Ruby code block that creates _n_ number of fixtures for our sample data. Fixtures are instances of ActiveRecord, meaning that they can be accessed and stored in Arrays like databases in non-test environments.
