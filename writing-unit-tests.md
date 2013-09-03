# Writing Fast and Efficient Unit Tests for Django

_Speaker: Casey Kinsey_


You should care about the speed of unit tests because if you're serious about
testing you should be serious about having lots of tests and running those
tests frequently. Slow test suites get in the way of testing goals because
your developers won't run the tests, especially for perceived small changes.


## The first step

Write unit tests. The Django test client is an integration test. Don't use
the test client if you are trying to write a unit test. So establish a good
ratio of unit tests to integration tests. For every method that contains
business logic there should be a unit test. For each page/view/user path
there should be an integration test.

Set up tests cautiously. Only include stuff you really need for every test
in this case. Don't put stuff in setUp just to be lazy. Take advantage of
setUpClass and tearDownClass instead, which run once per test case instead
of once per test in the test case.


## The database is hot lava!

Work whenever possible with read-only non persisted data. Use in-memory model
instances.

    # instead of this
    car = Car.objects.create(make='Scion', model='tC')
    # do this
    car = Car(make='Scion', model='tC')
    # and don't save the car

Avoid fixtures, because they are loaded/purged between each test case. They
don't adapt with your data-model and schema changes will result in test failures.

When you do write, use in-memory sqlite. (just don't provide a name for the db
in your test settings and it will be in-memory)

Try to live without django.test.TestCase.


## Use Mock

Use mock to emulate model instances. Set the attributes you need for testing
directly. Use the "spec" argument to give guidelines. Then you'll have no
model/ORM overhead. "spec" is a reference to the real class.


## It's okay to engineer when testing

Don't be afraid to invest engineering efor into your test suite. Write tools
to help you test. Leverage 3rd party tools. Use decorators, custom test
runners, if you need to.

And if you can't test the code efficiently, refactor the code. If the code
is difficult to write tests for, your code probably needs to be refactored
anyway.


## Reference

### Speaker

Developer consultant who works for Celerity.  
@cordiskinsey

### Slides

http://www.slideshare.net/cordiskinsey/djangocon-2013-how-to-write-fast-and-efficient-unit-tests-in-django
