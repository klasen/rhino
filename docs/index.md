---
layout: default
title: Home
nav_order: 1
---

# Rhino: JavaScript in Java

Rhino is an implementation of JavaScript in Java.

## License

Rhino is licensed under the [MPL 2.0](./LICENSE.txt).

## Releases

<table>

<tbody>

<tr>

<td>[Rhino 1.7R5](https://github.com/mozilla/rhino/releases/tag/Rhino1_7R5_RELEASE)</td>

<td>January 29, 2015</td>

</tr>

<tr>

<td>[Rhino 1.7.6](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_6_RELEASE)</td>

<td>April 15, 2015</td>

</tr>

<tr>

<td>[Rhino 1.7.7](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_7_RELEASE)</td>

<td>June 17, 2015</td>

</tr>

<tr>

<td>[Rhino 1.7.7.1](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_7_1_RELEASE)</td>

<td>February 2, 2016</td>

</tr>

<tr>

<td>[Rhino 1.7.7.2](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_7_2_Release)</td>

<td>August 24, 2017</td>

</tr>

<tr>

<td>[Rhino 1.7.8](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_8_Release)</td>

<td>January 22, 2018</td>

</tr>

<tr>

<td>[Rhino 1.7.9](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_9_Release)</td>

<td>March 15, 2018</td>

</tr>

<tr>

<td>[Rhino 1.7.10](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_10_Release)</td>

<td>April 9, 2018</td>

</tr>

<tr>

<td>[Rhino 1.7.11](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_11_Release)</td>

<td>May 30, 2019</td>

</tr>

<tr>

<td>[Rhino 1.7.11](https://github.com/mozilla/rhino/releases/tag/Rhino1_7_12_Release)</td>

<td>January 13, 2020</td>

</tr>

</tbody>

</table>

[Release Notes](./RELEASE-NOTES.md) for recent releases.

[Compatibility table](http://mozilla.github.io/rhino/compat/engines.html) which shows which advanced JavaScript features from ES6, and ES2016+ are implemented in Rhino.

## Documentation

Information for script builders and embedders:

[https://developer.mozilla.org/en-US/docs/Rhino_documentation](https://developer.mozilla.org/en-US/docs/Rhino_documentation)

JavaDoc for all the APIs:

[http://mozilla.github.io/rhino/javadoc/index.html](http://mozilla.github.io/rhino/javadoc/index.html)

More resources if you get stuck:

[https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/Community](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/Community)

## Building

### How to Build

Rhino builds with `Gradle`. Here are some useful tasks: `./gradlew jar` Build and create `Rhino` jar in the `buildGradle/libs` directory. `git submodule init git submodule update ./gradlew test` Build and run all the tests. `./gradlew testBenchmark` Build and run benchmark tests.

## Releasing and publishing new version

1.  Ensure all tests are passing
2.  Remove `-SNAPSHOT` from version in `gradle.properties` in project root folder
3.  Create file `gradle.properties` in `$HOME/.gradle` folder with following properties. Populate them with maven repo credentials and repo location. `mavenUser= mavenPassword= mavenSnapshotRepo= mavenReleaseRepo=`

4.  Run `Gradle` task to publish artifacts to Maven Central. `./gradlew publish`

5.  Increase version and add `-SNAPSHOT` to it in `gradle.properties` in project root folder.
6.  Push `gradle.properties` to `GitHub`

## Running

Rhino can run as a stand-alone interpreter from the command line: `java -jar buildGradle/libs/rhino-1.7.12.jar -debug -version 200 Rhino 1.7.9 2018 03 15 js> print('Hello, World!'); Hello, World! js>` There is also a "rhino" package for many Linux distributions as well as Homebrew for the Mac.

You can also embed it, as most people do. See below for more docs.

## Issues

Most issues are managed on GitHub:

[https://github.com/mozilla/rhino/issues](https://github.com/mozilla/rhino/issues)

## More Help

The Google group is the best place to go with questions:

[https://groups.google.com/forum/#!forum/mozilla-rhino](https://groups.google.com/forum/#!forum/mozilla-rhino)