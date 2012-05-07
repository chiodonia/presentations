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
   * How to run Dart
   * The Dart libraries
   * Conclusion
   * Discussion

---

<div align="center">
<img src="https://github.com/chiodonia/presentations/raw/master/dart/workinprogress.jpeg" alt="Work in progress" width="50%"; style="padding-top:10%"><img>
</div>

---

Introduction: Facts
===================

There is an increasing interest for complex modern Web applications:

   * Increasing customer requirements
   * HTML5 pushing the boundaries
   * Device diversification (mobile devices)

And the plug-in era is over!

---

Introduction: State of the Web
==============================

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

Introduction: JavaScript momentum
=================================

   * JavaScript is "better" than ever:
     * Frameworks (jQuery, MVC, ...)
     * Community adopting "best parts" 
     * Some good tools (JSLint)
     * Performance
     * API (HTML5 and Web API)
     * Virtual machine (Google V8)

   * … but can JavaScript play this role?
     * http://wtfjs.com/
     * https://www.destroyallsoftware.com/talks/wat
     * Allen Wirfs-Brock (Mozilla), http://www.infoq.com/presentations/JavaScript-Today-and-Tomorrow

---

Introduction: Google Dart
=========================

   * Improve the state of the art of Web programming:

        It would be easier! Dart: a new language and platform for web programming.
Source: http://www.dartlang.org/

   * Brand new: October 2011!
   * Lincese: Open Source, BSD
   * Developed "on the open": http://www.dartlang.org/docs/spec/
   * An entire platform: language, libraries and tools (<a href="http://www.dartlang.org/docs/getting-started/editor/">Dart Editor</a>)
   * Run on the **client** and the **server**
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

How to run Dart
===============

   * on the **Browser**
    * Dart-to-JavaScript compiler: http://www.dartlang.org/docs/getting-started/editor/
    * Chromium with the Dart VM: http://www.dartlang.org/dartium/ 
   * on the **Server**
    * Dart VM: http://www.dartlang.org/docs/getting-started/sdk/
     * High performance
     * V8 style
     * embeddable 

http://www.dartlang.org/docs/technical-overview/#howtouse

---

The Dart libraries
==================

    Libraries help you create a modular and shareable code base. Libraries not only provide APIs, but are a unit of privacy: they can hide implementation details such as private variables.
Source: http://www.dartlang.org/language-tour/#libraries

The goal is to provide a rich set of libs: 

   * http://api.dartlang.org/
   * http://dartwatch.com/index.php/dart-packages/

**Libraries and a module system (http://goo.gl/jml49) are a work in progress!**

---

The Dart libraries: dart:core
=============================

   * Defines:
     * Interfaces for the core types: num, Collection, Function, String,..
     * Exceptions
   * Imported by default
   * Both client and server
   * see http://api.dartlang.org/dart_core.html
    
---

The Dart libraries: dart:io
===========================

   * http://www.dartlang.org/articles/io/
   * Mainly (HttpClient available) for the server side 
   * Dart is a single-threaded programming language -> **non blocking I/O operations**, inspired by node.js
    * Dart VM runs in an event loop with an associated event queue of pending asynchronous operations
    * The VM terminates when it has executed the current code to completion and no more pending operations are in the queue
   * see http://api.dartlang.org/io.html

---

The Dart libraries: dart:html
=============================

   * A clean DOM API with:
     * Simpler names: 
       * HTMLElement -> Element
     * Better querying: 
       * elem.getElementById('foo'); -> elem.query('#foo');
       * elem.getElementsByTagName('div'); -> elem.queryAll('div');
   * Use real collections
       * elem.getAttribute('name'); -> elem.attributes['name'];
   * Use constructors
       * document.createElement('div'); -> new Element.tag('div');
   * Events
       * elem.addEventListener('click', (event) => print('click!'), false); -> elem.on.click.add((event) => print('click!'));

   * see http://api.dartlang.org/html.html, http://www.dartlang.org/articles/improving-the-dom/

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
Samples: 

   * https://github.com/syjer/weakdot
   * https://github.com/chiodonia/dartlang


