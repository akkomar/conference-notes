### Day 1
## Keynote

* Scala binary incompatibilities between minor versions come also from the fact that they cannot change JVM implementation - compare this with Java: if some bug is found, they can fix it in JVM
* TASTY - serialization of typed AST - can be nice for static code analysis tools (Findbugs for Scala?), should also help with binary compatibility issues

### Day 2
## Keynote
* conflict free replicated data types

## ???
* Future.sequence
* don't use implicit methods, use implicit classes - language is going in this direction (you need to import implicits in order to create implicit method, but you don't need any imports in order to create implicit class)
* repl colors ($ scala color)
* handling exceptions - use either if you don't have exceptions - they are expensive to construct
* value classes - performance


## Type-Safe Off-heap memory for Scala


## Scala at Twitter
* interesting build system
* single repo
* Jenkins, Iron (git-aware Mesos framework), http://pantsbuild.github.io/ (similar to Google's Basel)
* git review sandbox - runs tests atom CI infrastructure
* git review submit - compile, populate buildcache, merge to master
* source repo layout:
** shared code: root/src/scala/...
** projects: root/project/src/scala/...
* Birdcage - single repo with all code:
** shorten deprecation cycles
** top-to bottom continuous integration testing
** git bisect across continuous history
* pants vs sbt: sbt doesn't support source steps (something that Basel introduced?), maybe it will in the future?
* right now pants uses zinc (http://benjyw.com/post/29540093638/zinc-and-pants) and zinc uses sbt directly
* want to use Abide (https://github.com/scala/scala-abide) - code checking and validation
* pants has incremental compilation overhead, they want to switch to sbt-server

## Hiring and onboarding for your Scala team
* design url shortener , scale it
* twitter scala school
* scala neophyte guide
* enforce compiler warnings
* scalastyle violation on Jenkins fails the build
* regular profiling using Gatling (on dedicated environment, checking if performance is not degrading, updating goals as they progress (get faster))
* use hipchat or slack for communication in the team

## Lambda architecture
* data locality webinar - datastax academy (Spark/Cassandra)
* joins (Spark Cassandra connector)
* user defined types (Cassandra)


### Day 3

## Deeplearning
* unsupervised feature detection
* netty off-heap allocation (used by Spark?)

## Types vs tests
* good book: working effectively with legacy code
* type signature is a theorem, function definition is a proof
* property based tests
* tests calculate what types are unable to prove
* if in property-based test you have `forall`, consider introducing a type
* tests == there exists
* types == forall
* mutation testing

## A purely functional approach to building large scale applications
* scalaz monad transformers
* shapeless-scalacheck generates arbitrary instances of case classes
* futures in for comprehension do not run in parallel - instead of starting them beforehand try using applicatives
* scalaz task
* capsicle

## Paypal's reflections on four years of Scala in practice
* Spray routes generated from specs with swagger codegen
* paypal scala style guide (on github), also scalastyle configuration which is enforced on every build with sbt plugin
* build tool strict dependency convergence

## Finagle
* threads are not free (JVM uses native threads, they consume memory, they introduce gc pressure (garbage collector has to know which objects are reachable, information about references is taken from stacktraces))
* has backpressure
* MUX gc avoidance (works well only on twitter's custom JVM, but nevertheless brings some interesting features)
* failure detector
* drawbacks:
** no Scala futures
** based on netty 3
** slow adoption of Scala versions
* pros:
** many protocols
** active community
** tested in high scale


### Random remarks
* Astyanax doesn't work with Cassandra 2?
* clojure agents vs new akka actors (project gambla)
* MDC (logging) doesn't work in non-blocking model (it's based on threadlocals)
