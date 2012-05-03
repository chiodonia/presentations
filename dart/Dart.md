Introducing 
===========
<img src="http://www.dartlang.org/imgs/dart-logo.png" alt="DART"></img>
<a href="http://www.dartlang.org/">http://dartlang.org</a>

###Sylvain Jermini, Andrea Chiodoni

#####JUG Lugano, 9 May 2012

---

Agenda
======
   * Introduction
   * The Dart language
   * The Dart libraries
   * Conclusion
   * Discussion

---

Introduction
============

---

Facs
====

There is an increasing interest for complex modern Web applications:

   * HTML5 addressing application's requirements
   * Increasing customer requirements
   * Device diversification (mobile devices)

---
State of the Web
================

   * Good parts
     * Easy to write small-medium apps
     * Platform independent
     * No app installation
     * Support incremental development
     * Platform improving fast
     * Everywhere

	* Bad parts
       * Development of large apps is challenging:
 		  * Lack of structure
		  * No static types
		  * No support for libs (modularity)
		  * Poor IDE support
       * Slow startup (see http://stevesouders.com/)

---
JavaScript momentum
===================

   * JavaScript is "better" than ever:
     * Frameworks (jQuery, MVC, ...)
     * Community adopting "best parts" 
     * Some good tools (JSLint)
     * Performance
     * API (HTML5 and Web API)
     * Virtual machine (Google V8)

   * … but the language still have some issues
     * http://wtfjs.com/
     * https://www.destroyallsoftware.com/talks/wat
     * http://www.infoq.com/presentations/JavaScript-Today-and-Tomorrow

---

Google Dart
===========

   * Improve the state of the art of Web programming:

        It would be easier! Dart: a new language and platform for web programming.

   * Brand new: October 2011!
   * Lincese: Open Source, BSD
   * Developed "on the open": http://www.dartlang.org/docs/spec/
   * An entire platform: language, libraries and tools (<a href="http://www.dartlang.org/docs/getting-started/editor/">Dart Editor</a>)
   * Lear from the part: GWT, V8, speed
   * Make it available to the entire modern Web

---

The Dart language
=================

   * Constraint:
     * familiar to the mainstream programmers
     * efficiently compile to JS (GWT )
   * http://www.dartlang.org/articles/style-guide/
---

The Dart libraries
==================


    Libraries help you create a modular and shareable code base. Libraries not only provide APIs, but are a unit of privacy: they can hide implementation details such as private variables.
From http://www.dartlang.org/language-tour/#libraries

### Libraries and the module system (http://goo.gl/jml49) is a work in progress!

<img src="workinprogress.jpeg" alt="Work in progress"><img>

The goal is to provide a rich set of libs: 

   * http://api.dartlang.org/
   * http://dartwatch.com/index.php/dart-packages/

---

dart:core
=========
---

dart:html
=========
---

dart:json
=========

  * http://www.dartlang.org/articles/improving-the-dom/

---

dart:uri
========
---

dart:io
=======

  * http://www.dartlang.org/articles/io/

  * Execution: http://www.dartlang.org/docs/technical-overview/#howtouse
   * Dart-to-JavaScript compiler: http://www.dartlang.org/docs/getting-started/editor/
   * Chromium with the Dart VM: http://www.dartlang.org/dartium/ 
   * Dart VM: http://www.dartlang.org/docs/getting-started/sdk/
     * High performance
     * V8 style
     * embeddable 

---

dart:isolate
============
---


Conclusion
==========

   * Promising 
   * State: **currently only a technology preview!**
   * The question: **Will Dart be adopted?**

---

Discussion
==========

   * Matter of choice:
     * JavaScript as a "First language"
     * JavaScript as the assembler of the Web: "to JavaScript" **transpilers** like GWT, Dart, CoffeeScript, Closure compiler
   * What's the future for JavaScript?
   * Same language on both client and server (GWT, Node.js, Dart)
   * How Dart compares to CoffeeScript?
   * What's happen to GWT?
   * Is Dart solving the famous Java puzzlers? See http://www.dartlang.org/articles/puzzlers/chapter-1.html

#### What Google says: http://www.dartlang.org/support/faq.html

---

Tanks for you attention
=======================

---
