---
layout: blog
title: Scala World 2015 - day 2
---

GS

SecDb - highly interconnected

why Scala

- Type Safety
- Functional
- Expressivity
- JVM

- Case classes/pattern matching
- DSLs
- scope modifiers
- allows organizing sttack in diffferent way

Lawful Async Programming

- It's not about concurrency
- Never blocking, never sitting on a thread
- You don't wait, you register a callback
- Node.js

- Laws
- As in "math" laws, solve
	- error handling
	- components behaving differently together
	- aesthetic adjustments

scalaz-stream

- asynchrony as codata
	- concurrency compsition (merge)
	- transduction (pipe)
	- NIO (scalaz-netty)
	
Process[+F[_], +A]

Halt
Emit[+A]

Append

Process(1,2) ++ Process(3,4)

server onComplete shutdownApp

Finalizers are guaranteed to run (?)

Await node?

"Encoding of the Free Monad"


Referential Transparency

- If it works, it always works
	- no magical broken cases
	- no ordering constraints
	- no fear (NDE color me skeptic)
- real, actual composaility


Concurrency: stepAsyncs




Transduction

- state machine that modifies a stream
- extremely commoon
	- take
	- scan
	- parse (incdementally ?)
- implementable as streams

Parentheses matching



Process1[-I, +O] = Process[Env[I, Any]#Is, O]

SI-2712

Not afraid to say "it doesn't work"



Problems: False Freedom


*** Build the least powerful thing ***

Consequences

- Tail "flipping" problem

Is "Scalaz" broken?

Process is not a true Monad (not associative)

FS2


REBOOT of Scalaz-streams

New algebra
	- less-free Free
	- abstracts Task (can use Futures)
	
Lessons
	- Software is hard
	- Clever algebra undesirable outcome
	- Don't be too general
	- Don't be afrait to rewrite, learn from your errors
	
	WTF this thing is in production :|
	
	
A dance with tools

Iulian Dragos - Typesafe

Raise awareness
_ compared with Java
- decent IDEs (eclipse is kinda fading)

- Async debugger
	- reactive apps
	- Futures
	- Actors

- intercept new futures
- save call-stack and resume program

Actors?
- what was the state of the actor?
- who sent the message?
- follow the message!

Awesome! HOW DO I GET IT?

Testing frameworks?
- popular tools in GitHub
	- sbt
	- also maven and scala

- code coverage
	- SCoverage -> try this!
	- Jacoco -> look at this?
	- Cobertura

- scalastyle -> oooooh
	- wartremover
	- scapegoat
	- abide

- why not work on tools?
	- it's not glamour
	- not trust
	
- why work on tools?
	- working on languages
	- plenty of hard problems to crack
	- improve people's live

- the problem with tools
	- hard, impactful, fun, hard
	
- compiler is somehow immature
	- Scala.Meta (TASTY) will
	- 1-2 years away
	
- wishlist
	- a solid bug checker for scala
	- solid coverage
	- better compiler implementation
		- need a better spec
		
- Enxzyme (tool for Sublime/Emacs) could be integrate into IDE
	- 
	
- SBT integration for Eclipse probably in 4.3 \o/



JVM for big data - Spark

polyglotprogramming/talks
@deanwampler

Spark notebook

Lazy API looks like collections

Combines node steps into stages
Cache intermediate data

Resilient Distributed Dataset (RDD)

Example: Inverted Index

INVESTIGATE THIS ONE FOR SEARCH (elastic Search replacement?)

Mapreduce easy!

Spark Streaming (like Storm?) DStreams - Discretized stream (transforms a stream into a sequence of small batches)

Libs

- SQL/DataFrames
- MLlib (machine learning!)
- GraphX

Akka Breeze Agebird Spire & Cats Axle


JVM not perfect for big data

GC issues - it's ok with batching (which GC? tried different)
	- runs in 100+GB heaps
	- stuff goes in the OldGen
		- lots of cache misses
	- Garbage first (G1) improves a lot on garbage pauses
		- there is a good tuning set available
		
- Java objects overhead
- case classes
- hashmaps

- no unsigned types
- missing data libs (available in python and R)
- big data is killer app for functional

Why scala?

- pragmating OOP + FP
- scala big data sandwich (wut?)
- REPL + notebooks

Spark notebook - AWESOME (for Anna?)

- Collections API
- easy to understand (iffy implementation at times)
- Spark does fine without the Reader Monad (less pure, but "get a life!")

Are Java 8 lambdas enough?
- Tuples
- Pattern matching
- Type Inference (python is as easy to write but you are never sure what you may get)
- DSLs
- REPL + notebooks

DataFrame API
- is faster and has same performance in all languages

Project Tungsten
- initiative to performance of DataFrames
- Spark jobs are CPU bound (???) not bottlenecked on IO??
	- good HW
	- serialization, compression, hashing has CPU cost
	
- Java object model overhead
- GC expensive
- cache awareness

Tungsten
- custom memory management
- off-heap and on-heap
- compact rows
- hash code and equals on raw bytes
- compact off-heap structures
- bytecode generation

Reactive Streams
- robustnes?
- backpressure?

- Spark is driving Scala adoption
- Spark could be more pure
- Spark has lot of tech debt
- Scala should improve collections API interface - Scala could benefit from Spark's API?

Spark + Mesos?

Dotty

new "scala" compiler
is a rewrite

Written by Oderski and /darkdimius/ (previously ScalaBlitz) 

What is in Dotty:

- will have Union and Intersection types

- Intersection (like "with" but better)

Typedefs?

- Or-types: proper enumerations


- TESTY (type extension)
- re-compile from metadata (store intermediate code into class file). Can do reprocessing.
	- so we don't release multiple binaries for library X

- scalac is kinda messy


- SC-2712 is not solved


Still WIP, doesn't bootstrap



Idris

Pac-man Complete

Types as specs?

Type classes are more or less like Traits
Has Strict evaluation rules (but has Lazy type)

39brady


============
Typelevel

Shapeless

When Types are not enough

- What is correctness?
- Who defines correctness

- Implement a function which sort a list of numbers
	- what are numbers?
	- how do you order them?
	
Specifications don't exist or are often imprecise

Let's assume
	- there is a clear specification
	- only for a subystem
	- it makes sense
	- is not contradictory
	
Implementation is compliant if:
	- tests (scalacheck)
	- types
	- proofs "for all input, the output is correct"
	
What does it mean?

Curry-Howeard - here we are

Proof systems!

Idris
Coq
Isabelle

(Isabelle?) Proofs with no types

Generates scala code

leon - validates scala code

leon online
isabel prover

reactive streams & akka http

Spray guys, akka Http


CQRS?

Reactive streams: type safe, scalable, configurable
- Reactive streams is a PROTOCOL async, non blocking, bounded

Producer <==> Consumer (data -> and demand <-)

Backpressure = lack of demand
If producer a lot faster than consumer it blows up without backpressure

RS scale across the full stack
Scala scales well across the stack (functional high, procedural down - faster)

TCP maps well with RS

If you have multinodes each node has to behave correctly

RS are protocol + Jar
TCK compatibility toolkit

Java API is simple
all methods void (only tell, never ask)

Akka Streams *implements* RS Java API

Toy example for Akka Reactive Streams -- repo.spray.io

Repo log analyser most of lines are 404 as the repo is added to the resolver list

.buffer of Source[] large buffer, use kafka and bindings