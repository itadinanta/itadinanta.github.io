---
title: Spring Scala for Scala 2.11.x new official releases
---
Good news! Official development of spring-scala has resumed full steam thanks to [Paul Snively](mailto:psnively@mac.com). The official repository URL is [http://hub.darcs.net/psnively/spring-scala](http://hub.darcs.net/psnively/spring-scala)

From the horse's mouth:

> spring-scala snapshots and releases are publishes to the Sonatype snapshot and release repositories. As of this writing (August 2015), the following versions of Spring are supported:
>
> * Spring 3.2.10
> * Spring 3.2.14
> * Spring 4.0.9
> * Spring 4.1.7
> * Spring 4.2.0
>
> All artifacts are cross-published for Scala 2.10.x and 2.11.x, and digitally signed by Paul Snively,

You can reference the new libs in sbt following this template. Pick your favourite Spring flavour from an assortment of:

    libraryDependencies += "org.psnively" %% "spring_scala_3-2-10" % "1.0.0"

    libraryDependencies += "org.psnively" %% "spring_scala_3-2-14" % "1.0.0"

    libraryDependencies += "org.psnively" %% "spring_scala_4-0-9" % "1.0.0"

    libraryDependencies += "org.psnively" %% "spring_scala_4-1-7" % "1.0.0"

    libraryDependencies += "org.psnively" %% "spring_scala_4-2-0" % "1.0.0"

This means I no longer need to build unofficial releases and indeed I will not. However, I will keep the [net.itadinanta spring-scala](https://github.com/itadinanta/spring-scala) available for historical reasons. Please consider these deprecated.
