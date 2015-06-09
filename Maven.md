


## Introduction ##

This section explains how to use Maven with HeidelTime.

Maven, as a method of managing and getting packages, is in theory an ideal tool to build HeidelTime in a uniform manner. However, since there are dependencies that none of the public Maven repositories can satisfy, we unfortunately cannot offer a fully integrated Maven solution, or can supply a package downloadable from a central repository. Hence, to use Maven with HeidelTime, we need a few extra steps before we can build.

## Dependencies ##

HeidelTime's source code includes references to the JVnTextPro tool for Vietnamese tokenization. This piece of software does not feature any Maven support, so for an error-free compilation of HeidelTime with Maven, we first need to build JVnTextPro with Maven. We do this by:
  1. Grabbing and extracting a copy of [JVnTextPro](http://jvntextpro.sourceforge.net/)
  1. Moving `$HEIDELTIME_HOME/metadata/jvntextpro-pom.xml` to JVnTextPro's root folder and renaming it into `pom.xml`
  1. Building JVnTextPro: `mvn install`
  1. Installing the resulting .jar file into HeidelTime's local repository: `mvn org.apache.maven.plugins:maven-install-plugin:2.3.1:install-file -Dfile=target/jvntextpro-2.0.jar -DgroupId=jvntextpro -DartifactId=jvntextpro -Dversion=2.0 -Dpackaging=jar -DlocalRepositoryPath=$HEIDELTIME_HOME/repo/`
  1. Compiling HeidelTime from within the kit folder: `mvn install`