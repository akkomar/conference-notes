### Day 1
## Keynote

* Scala binary incompatibilities between minor versions come also from the fact that they cannot change JVM implementation - compare this with Java: if some bug is found, they can fix it in JVM
* TASTY - serialization of typed AST - can be nice for static code analysis tools (Findbugs for Scala?), should also help with binary compatibility issues

### Day 2
## Keynote
* conflict free replicated data types

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
* 
*
