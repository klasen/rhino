---
layout: default
title: Small footprint
---
# Small footprint
{: .no_toc }

{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

**Warning:** **The content of this article may be out of date.**


A few changes can be made to reduce the footprint of Rhino for embeddings where space is at a premium. On a recent build, the length of cite: <cite>js.jar</cite> was 603,127 bytes corresponding to 1,171,708 bytes of all uncompressed Rhino classes with debug information included. With various changes cite: <cite>js.jar</cite> size can be reduced to 204,689 bytes corresponding to 424,774 bytes of uncompressed classes.

## Tools

Most embeddings won't need any of the classes in cite: <cite>org.mozilla.javascript.tools</cite> or any of its sub-packages.

## Optimizer

It is possible to run Rhino with interpreter mode only, allowing you to remove code for classfile generation that include all the classes from cite: <cite>org.mozilla.javascript.optimizer</cite> package.

## JavaAdapter

Implementing the JavaAdapter functionality requires the ability to generate classes on the fly. Removing cite: <cite>org.mozilla.javascript.JavaAdapter</cite> will disable this functionality, but Rhino will otherwise run correctly.

## Class generation library

If you do not include `Optimizer` or `JavaAdapter`, nor do you use `PolicySecurityController` then you do not need Rhino library for class file generation and you can remove all the classes from in cite: <cite>org.mozilla.classfile</cite> package.

## Regular Expressions

The package cite: <cite>org.mozilla.javascript.regexp</cite> can be removed. Rhino will continue to run, although it will not be able to execute any regular expression matches. This change saves 47,984 bytes of class files.

## Debug information

Debug information in Rhino classes consumes about 25% of code size and if you can live without that, you can recompile Rhino to remove it.

## smalljs.jar

Ant build script in Rhino supports smalljar target that will generate cite: <cite>smalljs.jar</cite> that does not include `Tools`, `Optimizer`, `JavaAdapter` and class generation library, eegular expressions, E4X implementation and deprecated files. To build such minimalist jar without debug information, run the following command from the top directory of Rhino distribution:

```
`ant clean``ant -Ddebug=off -Dno-regexp=true -Dno-e4x=true smalljar`
```

If you omit `-Dno-regexp=true`, then the resulting cite: <cite>smalljs.jar</cite> will include regular expression support. Similarly omitting `-Dno-e4x=true` results in cite: <cite>smalljs.jar</cite> that includes runtime support for E4X.

## Original Document Information- Author: (Norris Boyd)[mailto:norrisboyd@gmail.com]- Last Updated Date: November 16, 2006- Copyright Information: Portions of this content are � 1998�2006 by individual mozilla.org contributors; content available under a Creative Commons license | (Details)[http://www.mozilla.org/foundation/licensing/website-content.html].