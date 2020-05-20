# Scala and sbt for Docker
[![](https://images.microbadger.com/badges/image/ramsvidor/sbt.svg)](https://microbadger.com/images/ramsvidor/sbt "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/ramsvidor/sbt.svg)](http://microbadger.com/images/ramsvidor/sbt "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/commit/ramsvidor/sbt.svg)](http://microbadger.com/images/ramsvidor/sbt "Get your own commit badge on microbadger.com")
[![](https://images.microbadger.com/badges/license/ramsvidor/sbt.svg)](http://microbadger.com/images/ramsvidor/sbt "Get your own license badge on microbadger.com")

Image for building and running sbt and Scala projects.

**@see** [Dockerfile](https://github.com/ramsvidor/docker-graalvm/blob/master/sbt/Dockerfile)

## Base image
* [ramsvidor/graalvm](https://hub.docker.com/ramsvidor/graalvm) (GraalVM 20.1.0 / JDK 11 / Debian Stretch Slim)

## JRE and JDK included - for production, see how to build native images
Default versions are intended to run [Scala](http://www.scala-lang.org) and [sbt](http://www.scala-sbt.org) applications. If you want to compile and build Scala applications, use the JDK version instead.
JDK is built with the required dependencies for building and packaging Scala and Java applications with sbt.

## License
This code is open source software licensed under the [Apache 2.0 License]("http://www.apache.org/licenses/LICENSE-2.0.html").
