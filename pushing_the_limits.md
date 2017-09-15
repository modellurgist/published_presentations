# Pushing the Limits

- Tom Calloway
  * engineer at HomeChef, a meal-kit delivery service in Chicago
  * [github.com/modellurgist/presentations/]()
  * modellurgist@gmail.com

## foundation of the Calculus
  - limit as epsilon -> 0

## extreme programming
  - if a little is good, a little more is better, what if we did it all the time?
  - pair programming is reviewing code continuously
  - test first and always
  - and other familiar Agile practices

## conference retros
  - Demeter
    * limited interface (number of public methods)
    * violating law/encapsulation costs due to coupling, forcing to make changes in n places instead of just 1
      - also n places to mock/stub, in your tests
  - Rails DB anti-patterns:  using multiple join models, instead of single polymorphic for separate distinct domain concepts
  - Strava / Reverb factoring out into many objects, thoughtfully, with few/single responsibilies for each

## independent variables in our control
  - number of methods per class
  - number of lines per method
  - number of dependencies per class (mixins, class/module requires)
  - number of side-effects per method (changes to inputs, state)
  - number of arguments
  - and more...

## additive cost function
  - number of lines of code to maintain
  - cognitive overhead to understand consequences of changes
  - dependency coupling and number of places to modify; risk of missing one
  - churn risk of a new bug due to a mistake in modifying a file/class/method
  - number of combinations of arguments/attributes encountered in method definitions
  - number of design patterns / anti-patterns to know and consider, in order to mitigate (but not reach theoretical minimum) the costs
  - argument nil and validation checks, and doing these multiple times
  - necessary context (other classes, state, execution trace) to understand one class
  - cost to do big, deep changes/refactorings
  - number of tests
  - mocking/stubbing overhead per test
  - number of dependencies loaded per test file
  - speed of tests
  - etc.

## many others have proposed many ideas over many years to address those costs, in OO, Ruby, Rails, and using functional programming

## dry-rb.org project is using an interesting, simple pattern for an FP-OO blend:  1-method objects
  - some of your objects are already like this:  Sidekiq jobs, some service objects, etc.

## experiment for you to try
  - if you take classes to this extreme/limit, almost all the time, unless a really good reason not to
    * what is the output value of the total cost function (now and over time) ?  Is it a big win ?
    * how much is this offset by any costs that actually go up as a result?
  - even if you "cheat" a little, does this take you to new and
    interesting places?

## form
    * code:
      - use a lamba or use #call in a single method class; lambdas great for test mocking
      - write as few lines of code in that method as possible
      - for arguments and return values, use a limited number, system-wide, of validated value objects
      - for immutability, output returns a new value of same type or some other type
      - no side-effects in function, unless for limited number of operation/transaction/action/service objects
    * db:
      - fewer attributes per table

## make conceptual distinctions, keep sub-dividing concerns (like an amoeba)
  - more classes, gems, tables

## separate concerns early and eagerly, since we won't recogize it until too late, cost will be higher, and we deem good ideas too costly to try

## leave behind a trail of objects with little/no need to change, only developing on the leading edge of new functionality/composition values

## editor/filesystem problems:  making object creation, discovery, namespacing, display cheap and pleasant

## interesting projects

  - FP-OO hybrid Ruby
    - Icelab Notes / presentations [icelab.com.au/notes]()
    - [dry-rb.org]()

  - more FP-style persistence and web framework
    - [rom-rb.org]()
    - [Hanami](hanamirb.com)

## influences
  - Clojure and Rich Hickey
  - Kent Beck and good OO programming lessons
  - Boundaries talk [destroyallsoftware.com]()
  - Redux
  - Dijkstra

