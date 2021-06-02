# Chips-n-Salsa - A Java library of customizable, hybridizable, iterative, parallel, stochastic, and self-adaptive local search algorithms

[<img alt="Chips-n-Salsa - A Java library of customizable, hybridizable, iterative, parallel, stochastic, and self-adaptive local search algorithms" 
     src="docs/images/chips-n-salsa.png" width="640">](#chips-n-salsa---a-java-library-of-customizable-hybridizable-iterative-parallel-stochastic-and-self-adaptive-local-search-algorithms)

Copyright (C) 2002-2021 [Vincent A. Cicirello](https://www.cicirello.org/).

Website: https://chips-n-salsa.cicirello.org/

| __Publications About the Library__ | [![DOI](https://joss.theoj.org/papers/10.21105/joss.02448/status.svg)](https://doi.org/10.21105/joss.02448) |
| :--- | :--- |
| __Packages and Releases__ | [![Maven Central](https://img.shields.io/maven-central/v/org.cicirello/chips-n-salsa.svg?label=Maven%20Central)](https://search.maven.org/artifact/org.cicirello/chips-n-salsa) [![GitHub release (latest by date)](https://img.shields.io/github/v/release/cicirello/Chips-n-Salsa?logo=GitHub)](https://github.com/cicirello/Chips-n-Salsa/releases) [![DOI](https://zenodo.org/badge/273074441.svg)](https://zenodo.org/badge/latestdoi/273074441) |
| __Build Status__ | [![build](https://github.com/cicirello/Chips-n-Salsa/workflows/build/badge.svg)](https://github.com/cicirello/Chips-n-Salsa/actions/workflows/build.yml) [![docs](https://github.com/cicirello/Chips-n-Salsa/workflows/docs/badge.svg)](https://chips-n-salsa.cicirello.org/api/) [![CodeQL](https://github.com/cicirello/Chips-n-Salsa/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/cicirello/Chips-n-Salsa/actions/workflows/codeql-analysis.yml) |
| __JaCoCo Test Coverage__ | [![coverage](https://github.com/cicirello/Chips-n-Salsa/blob/master/.github/badges/jacoco.svg)](https://github.com/cicirello/Chips-n-Salsa/actions/workflows/build.yml) [![branches coverage](https://github.com/cicirello/Chips-n-Salsa/blob/master/.github/badges/branches.svg)](https://github.com/cicirello/Chips-n-Salsa/actions/workflows/build.yml) |
| __License__ | [![GitHub](https://img.shields.io/github/license/cicirello/Chips-n-Salsa)](https://github.com/cicirello/Chips-n-Salsa/blob/master/LICENSE) |

## How to Cite

If you use this library in your research, please cite the following paper:

> Cicirello, V. A., (2020). Chips-n-Salsa: A Java Library of Customizable, Hybridizable, Iterative, Parallel, Stochastic, and Self-Adaptive Local Search Algorithms. *Journal of Open Source Software*, 5(52), 2448, https://doi.org/10.21105/joss.02448 .

## Overview

Chips-n-Salsa is a Java library of customizable, hybridizable, iterative, parallel, stochastic, and self-adaptive local search algorithms. The library includes implementations of several stochastic local search algorithms, including simulated annealing, hill climbers, as well as constructive search algorithms such as stochastic sampling. The library most extensively supports simulated annealing. It includes several classes for representing solutions to a variety of optimization problems. For example, the library includes a BitVector class that implements vectors of bits, as well as classes for representing solutions to problems where we are searching for an optimal vector of integers or reals. For each of the built-in representations, the library provides the most common mutation operators for generating random neighbors of candidate solutions. Additionally, the library provides extensive support for permutation optimization problems, including implementations of many different mutation operators for permutations, and utilizing the efficiently implemented Permutation class of the [JavaPermutationTools (JPT)](https://jpt.cicirello.org/) library.

Chips-n-Salsa is customizable, making extensive use of Java's generic types, enabling using the library to optimize other types of representations beyond what is provided in the library. It is hybridizable, providing support for integrating multiple forms of local search (e.g., using a hill climber on a solution generated by simulated annealing), creating hybrid mutation operators (e.g., local search using multiple mutation operators), as well as support for running more than one type of search for the same problem concurrently using multiple threads as a form of algorithm portfolio. Chips-n-Salsa is iterative, with support for multistart metaheuristics, including implementations of several restart schedules for varying the run lengths across the restarts. It also supports parallel execution of multiple instances of the same, or different, stochastic local search algorithms for an instance of a problem to accelerate the search process. The library supports self-adaptive search in a variety of ways, such as including implementations of adaptive annealing schedules for simulated annealing, such as the Modified Lam schedule, implementations of the simpler annealing schedules but which self-tune the initial temperature and other parameters, and restart schedules that adapt to run length.

## Repository Organization

The GitHub repository is organized as follows:
* The [/src](src) directory contains all of the source code for Chips-n-Salsa.
* The [/tests](tests) directory contains JUnit test cases for all functionality of the library.
* The [/docs](docs) directory contains the javadoc documentation in a sub-directory /docs/api. The /docs directory is also the location of the website for the project hosted via GitHub pages at https://chips-n-salsa.cicirello.org/.

## Java 8+

The library supports Java 8 or higher.  Our build process currently builds the library using OpenJDK 11, but with a Java 8 target.

## Building the Library (with Maven)

The Chips-n-Salsa library is built using Maven. The root of the
repository contains a Maven `pom.xml`.  To build the library, 
execute `mvn package` at the root of the repository, which
will compile all classes, run all tests, run javadoc, and generate 
jar files of the library, the sources, and the javadocs.  In addition
to the jar of the library itself, this will also generate a
jar of the library that includes all dependencies.  The file names
make this distinction explicit.  All build outputs will then
be found in the directory `target`.

To include generation of a code coverage report during the build,
execute `mvn package -Pcoverage` at the root of the repository to 
enable a Maven profile that executes JaCoCo during the test phase.

## Example Programs

There are several example programs available in a separate repository:
[cicirello/chips-n-salsa-examples](https://github.com/cicirello/chips-n-salsa-examples).
The examples repository contains example usage of several of the 
classes of the library. Each of the examples contains detailed
comments within the source code explaining the example. Running the 
examples without reading the source comments is not advised.  

## Versioning Scheme

Chips-n-Salsa uses [Semantic Versioning](https://semver.org/) with 
version numbers of the form: MAJOR.MINOR.PATCH, where differences 
in MAJOR correspond to incompatible API changes, differences in MINOR 
correspond to introduction of backwards compatible new functionality, 
and PATCH corresponds to backwards compatible bug fixes. 

## Importing the Library from Maven Central

Add this to the dependencies section of your pom.xml, replacing 
the version number with the version that you want to use (note that the 
library has been available in Maven Central since version 2.0.0).

```XML
<dependency>
  <groupId>org.cicirello</groupId>
  <artifactId>chips-n-salsa</artifactId>
  <version>2.0.0</version>
</dependency>
```

## Importing the Library from GitHub Packages

If you'd prefer to import from GitHub Packages, rather than Maven Central, or
if you need a version that is unavailable in Maven Central (versions prior to 2.0.0),
then: (1) add the dependency as indicated in previous section above, and (2) add 
the following to the repositories section of your pom.xml:

```XML
<repository>
  <id>github</id>
  <name>GitHub cicirello Apache Maven Packages</name>
  <url>https://maven.pkg.github.com/cicirello/Chips-n-Salsa</url>
  <releases><enabled>true</enabled></releases>
  <snapshots><enabled>true</enabled></snapshots>
</repository>
```

## Downloading Jar Files

If you don't use a dependency manager that supports importing from Maven Central,
or if you simply prefer to download manually, prebuilt jars are also attached to 
each [GitHub Release](https://github.com/cicirello/Chips-n-Salsa/releases).

## License

The Chips-n-Salsa library is licensed under the [GNU General Public License 3.0](https://www.gnu.org/licenses/gpl-3.0.en.html).

## Contribute

If you would like to contribute to Chips-n-Salsa in any way, such 
as reporting bugs, suggesting new functionality, or code contributions 
such as bug fixes or implementations of new functionality, then start 
by reading 
the [contribution guidelines](https://github.com/cicirello/.github/blob/main/CONTRIBUTING.md).
This project has adopted 
the [Contributor Covenant Code of Conduct](https://github.com/cicirello/.github/blob/main/CODE_OF_CONDUCT.md).
