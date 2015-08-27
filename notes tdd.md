BDD with TDD: Feature test to unit test

1. Outer loop: feature test -> Think about the user behavior

Cucumber
# Takes user stories and turns it into test

Capybara
# spec/features/
# feature: describe
# scenario: it
# expect(this).to
# context: successful, unsuccessful
# js:true option

Silenium
# Run the test in the browser in front of you

2. Inner loop: unit test -> Think about the code

Rspec
# describe
# it


*Edge case* - Test special cases, the not-happy path
Document bugs in your tests, by writing a test for your bug.

Model test
1. Validate (happy path)
2. Validate (bad path)
3. Class methods
4. Instance methods

Fat model, skinny controller.

Controller: routes requests, check for permissions/authorizations

# Memoize

# Feature specs
Test the same thing as controller, but from user's perspective.

