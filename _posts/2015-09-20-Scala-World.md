---
layout: blog
title: Scala World 2015
---

It's Sunday. I'm on the train to Penrith and I'm almost on time for the Unconference. With such a packed schedule and two tracks I haven't yet made my mind about which talks I'll inevitably have to let go of. Claudia kindly suggested I could use a cloning device or, failing that, a time machine. Sour grapes as it sounds, weather is glum and solidly overcast so I'm not too ashamed I've slacked on the hiking shenanigans. Anachronistically for 2015, Vodafone reminded me I'm halfway through the month but almost through my data allowance; as a result I am dreading an inordinate surcharge on next month's phone bill, but alas I can't give 3G up right now, not as long as I need Google Maps to make my way to the hotel.

I'm still wrapping my head around new paradigms. It reminds me of the switch from procedural to OOP in the late nineties. Also a bit of switching from C++ to Java a few years later. While I have no difficulty writing code that mostly works, my Scala code looks as if it had __flat tyres__. It has no personality and I am not even able to tell whether I'm on track to putting together the right idioms. Hopefully after the expected two days of __full immersion__ into the bleeding edge of the Scala industry some sense will stick and I'll start to get rid of the sense of "lostchildiness".

Jon Pretty

Welcome to Scala World

- Sabbatical
- Rapture (OSS Libraries)
- People from all over the world
- Gitter for Scala
- Face to Face is  good
- WiFi is broken
- Use Gitter for questions
- Propensive is now a training + consultancy enterprise



Power vs expressiveness

- Example: printing on a dot matrix printer
- Initial version: direct command through LPT:
- Composition - like dealing with explosions. Compose the explosive, not the explosion!
- Concretisizng too early
- Using algeraic and function is dealing with the explosive, side effects are the explosions
- compile scala to TASTY trees (contains AST + compiled binary?)
- "Stringly typed" programming (embedded SQL)
- Abstraction vs power -> abstraction allows precision in a "higher space"

If you compare
- def foo(a: Int): Int
- def foo[A](a: A): A

second one is more precise BECAUSE it is constrained

- flatMap is flat * join

Futures are more constrained than actors, so they're composable better

join Future[Future[A]] => Future[A]

But actors are more powerful (unconstraned side effects), and this has a cost.

Cost  of side effect:

- compositionality
- moudularity
- concurrency
- parametricity
...

Principle of least privileges

Minimal privileges => max compositionality, max modularity





F -| G

F[A] *> B <=> A :> G[B]

F -| G

F[A] => B <=> A => G[B]


- A constraint at one level is freedom on another
- composition is good
- Don't reach for maximum expressive power

Adjunction between existential and universal

- dependent method types

trait Mode {type Return}
def fn(m: Mode): m.Return

- type constructor

List[_]


- implicits

Specify a parameter grabbing from scope matching its type


- Type intersections

sometimes referencing a type doesn't entail instantiation
phantom times get erased
used to enforce constraints

class Map[T] {
def get [V :> T] = ... (v supertype)
}
val m = new Map[Int with String]  // Int is a supertype of Int with String

Yes, but... How about runtime?


(AreaParam | WitdhParam & HeightParam).parse(somethingFromTheUser)

Product A B C => all
Coproduct A B C => exactly ond

- Trick to use the compiler to pre-empty combinations bad casese
- Handle all failures together up-front

Rapture CLI

- using this technique, you get tab completion for free :)
- Looking for contributors - perhaps it's worth a shot






Joe Barnes

- Practical type programming
- Used Lift
- Little type Programming
- Shapeless none
- Has a blog

Subspace like in Mario

implicitly[TrueType =:= TrueType]


Ace tip, can test for "does not compile"
scalatest shapeless.test.illTyped // can test if it doesn't compile

illTyped("something that does not compile")

type with two parameters can be written as infix!

Utility: can easily replace runtime exceptions with compile time checks

Type lambda WTF

It's on GitHub

implemented Natural Numbers, map, reduce and fold

The trick is recurse and find a decent zero

Shit Wifi!

=====
ScalaC compiler talk #1

Re-Engineering legacy software @cbirchall cb372
ScalaCache

Debugging
Optimizing compilation
Writing bug reports

Compiler stages: output

parser: Tree
namer: Tree + SymbolTable
typer: Typed Tree + SymbolTable

20+ transformations: Typed Tree + SymbolTable <---- Dragons

icode: Intermediate (2.12 will skip this)
Intermediate: bytecode

stages scalax -Xshow-phases

examples: pattern matching, tailcalls

-Yshow-trees

Scalac bootstrapped at v 2.0 (from Java)
Scala.js is done with plugins


Scalac architecure: layer cake


Kinda messy codebase

Shoemaker has no shoes :) - phases only do side effects, transform tree in place

scalac-plugin-basic

====

\#yolo demo :)


Another Compiler talk

Live coding?

"Deprecating view bounds"




Collections Pretty Slow

- Scalactic collections
- Attempt to overtake the standard collection
- Removing deprecated things is good
- But take care
- Otherwise you get Python3
- Use needles not machetes
- Incremental changes across time

val ci: Collections[String](....)
ci.Set[String]("this works")

Set[+T] why covariant?

Because it's intuitive

Intensional sets (defined by a membership predicate)

Focus design on user experience, not implementer experisnce

Test (use Table for scala test)


Levelling UP Scala

- Types with Implicits is low

typeclasses vs the world

SIP-23


TextMate

(more of a discussion... open)


================
Scodec

Serialization library

Uses shapeless

.as[T]

(also look at typelevel)

HList: "generic tuple" (any length)

Seen in XML? Akka HTT for headers?

flatPrepend

Generic: case class <=> generic representation

Coproducts: N-wide "Either"

Binary Union: "C uniod"
Discriminated Binary Union: like pascal case records (there is a discriminator value)
	with explicit discriminator

Records, Unions

Comcast -> practical usage, ported to C++11



====================

Milos Barbaman - Miles Sabin (big name!) @milessabin

from Underscore

Shapeless?

Kittens
shapeless type class derivation for Cats


Was not intended as a "real" project

Cats ?????

Typeclasses for Cats

Based on stuff that breaks

Mappage, Functorage and so on

Pure[_] ? only has a value... What is it for?

Zero or Empty

Monoid, Additive[Zero, Unit]
Monoid, Unit ???? Multiplicative ????? append with Unit? WTF perhaps it's Append and Zero

...Lots of typeclass fluff...

alleykats
milessabin/export-hook

Kinda typelevel astronaut

macro-compat

Library doesn't build ^^;;;;;;

Grabbed from GHC generics

Making a Functor[Tree[A]] structure which can be mapped trhough to get a Functor[Tree[B]] - automatically

Weird "magic" "continuation-style passing"