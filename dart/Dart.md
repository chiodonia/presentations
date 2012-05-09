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

And the **plug-in** era is over!

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

---

Introduction: State of the Web (cont.)
======================================

   * Bad parts, Development of large apps is challenging:

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

---

Introduction: Can JavaScript play the role?
===========================================

   * ... but can JavaScript play this role?

     * http://wtfjs.com/
     * https://www.destroyallsoftware.com/talks/wat
     * Allen Wirfs-Brock (Mozilla), http://www.infoq.com/presentations/JavaScript-Today-and-Tomorrow

---

Introduction: Google Dart
=========================

 >  Improve the state of the art of Web programming!

   * Brand new: October 2011!
   * License: Open Source, BSD
   * Developed "on the open": http://www.dartlang.org/docs/spec/
   * An entire platform: language, libraries and tools
   * Run on the **client** and the **server**
   * Lear from the part: GWT, V8, speed
   * Make it available to the entire modern Web

---

The Dart language
=================

  * In one phrase: optionally typed dynamic single inheritance class based purely object oriented programming language.
  * Concurrent programming through "isolates"
  * Familiar to the mainstream programmers
  * Efficiently compile to JS
  * With some twists and a sizable amount of syntactic sugar (I'm looking at you, anonymous inner classes in java).
  * An unsound type system: as described by Gilad Bracha: *a static analysis tool based on heuristics, coupled to a type assertion system*

---

The Dart language: optional typing
==================================

  * Optionally typed as in:

      * the types are annotations
      * they don't change the runtime semantics
      * not for decoration: help catching error (by the compiler and the runtime in checked mode), documentation purpose.

---


The Dart language: familiarity
==============================

 - classes, interfaces (with some twist) and in a future release, abtract classes &#x2714;
 - `static` keyword variable/methods &#x2714;
 - `final` keyword for constants &#x2714;
 - exceptions: `try catch finally` &#x2714; with a sane default (unchecked) and a twist: you can throw any object.
 - same keyword for control flow as you know (skipping the details).
 - generics (a simpler but unsound version, maybe more pragmatic? :) )

---

The Dart language: unfamiliarity for a java programmer
======================================================

 - operator overriding
 - first class function
 - optional parameters: default value, named 
 - closures
 - no void, all functions return something. `return null` is added implicitly if there is no return statement.

---

The Dart language: Functions
============================

    String say(String from, String msg) {
      return "$from says $msg";//string interpolation
    }

Short one line version:

    String say(String from, String msg) => "$from says $msg"; //implicit return


Without type annotation:

    say(from, msg) => "$from says $msg";

---

The Dart language: Functions: optional parameters
=================================================

Optional:

    say(from, msg, [device]) {
      //default value will be null
    }

Optional with default value:

    say(from, msg, [device = "blah"]) {
      //default value will be "blah"
    }

Use of named parameter:

    say("Bob", "Howdy", device: "tin can and string")

---

The Dart language: First class functions
========================================

Classic:

    List ages = [1,4,5,7,10,14,21];
    List oddAges = ages.filter((i) => i % 2 == 1);

Assign to a variable:

    var loudify = (msg) => '!!! ${msg.toUpperCase()} !!!';
    print(loudify('hello'));

---

The Dart language: Function, closures
=====================================

As you would expect:

    Function makeAdder(num n) {
      return (num i) => n + i;
    }

    main() {
      var add2 = makeAdder(2);
      print(add2(3)); // 5
    }

---

The Dart language: Strings with sugar
=====================================

By the way, like js, ' and " are both valid identifier:

Interpolation:

    var s = 'string interpolation';
    
    print('Dart has $s, which is very handy.');
    print('That deserves all caps. ${s.toUpperCase()}'
          ' is very handy!'); //adjacent string literals
                              //are concatenated


Multiline:

    var s1 = '''
      You can create
      multi-line strings like this one.
    ''';

----


The Dart language: Collections
==============================

Literals for collections (and they are fully mutable, unlike some proposal that floated for java7):

List:

    var list = [1,2,3];


Maps:

    var gifts = {// a map literal
    // keys       values
      "first"  : "partridge",
      "second" : "turtledoves",
      "fifth"  : "golden rings"};
---

The Dart language: Classes
==========================

Familiar single inheritance class system:

    class Point {
       num x, y;
       // syntactic sugar for this.x = x and this.y = y
       Point(this.x, this.y);
    }

Named constructors:

    class Point {
      num x, y;
      
      // named constructor
      Point.fromJson(Map json) : x = json['x'], y = json['y'];
      Point(this.x, this.y);
    }
    
    var jsonData = JSON.parse('{"x":1, "y":2}');
    var point = new Point.fromJson(jsonData); 

---


The Dart language: Classes (cnt)
================================

No surprises at all:

    class Television {    
      turnOn() {
        _illuminateDisplay();
        _activeIrSensor();
      }
    }

You declare a member private with an underscore.

    class SmartTelevision extends Television {
      turnOn() {
        super.turnOn();
        _bootNetworkInterface();
        _initializeMemory();
        _upgradeApps();
      }
    }


---

The Dart language: Classes (some differences)
=============================================

Initializer list for final variables (as they must be assigned before:

    class Button {
      final Collection handlers;
      final String domId;
      final Element elem;
  
                // what follows the : is the initializer list
      Button(domId) : domId = domId,
                      handlers = [],
                      elem = document.query(domId) {

        bindHandlers();
      }

      bindHandlers() {
       // ...
      }
    }


---


The Dart language: Classes (some sugar)
=======================================

Getter/Setter:

    class Rectangle {
      num left, top, width, height;
      
      Rectangle(this.left, this.top, this.width, this.height);
      
      num get right()           => left + width;
          set right(num value)  => left = value - width;
      num get bottom()          => top + height;
          set bottom(num value) => top = value - height;
    }

Appear as a property:

    var rect = new Rectangle(3, 4, 20, 15);
    print(rect.left); // 3
    rect.right = 12;
    print(rect.left); // -8


---

The Dart language: Interfaces
=============================

Like java:

    interface Hashable {
      int hashCode();
    }

Not exactly like java:

    interface HashablePoint extends Hashable {
      num x, y;
    }


    class Point implements HashablePoint {
      num x, y; // required by HashablePoint
    
      // required by Hashable
      int hashCode() {
        ...
      }
    }

---

The Dart language: Interfaces (cnt)
===================================

Not java at all: constructors in interface with a `default` specified concrete class:

    interface ObjectCache default MemoryCache {
      ObjectCache();
      ...
    }
    
    class MemoryCache implements ObjectCache {
      ...
    }

Then you can do:

    var cache = new ObjectCache();// same as: new MemoryCache()

---

The Dart language: Isolates
===========================

 - Concurrency done right: shared nothing approach. (no need for a concurrent GC)
 - Comunication through message passing. Messages are deep copied.

Limitation for the message content:

 - A primitive value (null, num, bool, double, String)
 - An instance of SendPort
 - A list or map whose elements are any of the above, including other lists and maps
 - In special circumstances (like spawning a function), an object of any type

---


The Dart language: Isolates cnt.
================================

Send (not blocking) and receive.


    #import('dart:isolate');

    echo() {
      port.receive((msg, SendPort reply) {
        print("I received: $msg");
      });
    }

When any isolate starts (even the main script of the application), a default ReceivePort is created for it. 
This port is available from the top-level getter `port` defined in this library.
    
    main() {
      SendPort sendPort = spawnFunction(echo);
      sendPort.send("Hello from main");
    }


---


The Dart language: Isolates cnt.
================================

`call()` (which return a Future object) and `receive()`:

    #import('dart:isolate');

    echo() {
      port.receive((msg, SendPort reply) {
        reply.send("I received: $msg");
      });
    }

    main() {
      SendPort sendPort = spawnFunction(echo);
      sendPort.call("Hello from main").then((reply) {
        print(reply);    // I received: Hello from main
      });
    }


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

---

The Dart libraries
==================

>Libraries help you create a modular and shareable code base. Libraries not only provide APIs, 
>but are a unit of privacy: they can hide implementation details such as private variables.
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

   * Mainly (HttpClient available) for the server side 
   * HttpServer, HttpClient, File, Timer, Sockets, WebSockets, InputStream, OutputStream
   * Dart is a single-threaded programming language -> **non blocking I/O operations** (inspired by Node.js)

    * Dart VM runs in an event loop with an associated event queue of pending asynchronous operations
    * The VM terminates when it has executed the current code to completion and no more pending operations are in the queue
   * see http://api.dartlang.org/io.html

---

The Dart libraries: dart:html
=============================

   * A clean DOM API

     * **Simpler names**: HTMLElement -> Element
     * **Better querying**: elem.getElementById('foo'); -> elem.query('#foo');
     * **Use real collections**: elem.getAttribute('name'); -> elem.attributes['name'];
     * **Use constructors**: document.createElement('div'); -> new Element.tag('div');
     * **Events**: elem.addEventListener('click', (event) => print('click!'), false); -> elem.on.click.add((event) => print('click!'));

   * see http://api.dartlang.org/html.html

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

     * What about JavaScript as a "First language"?
     * And JavaScript as the assembler of the Web ("to JavaScript" **transpilers** )? Things like GWT, Dart, CoffeeScript, Closure compiler...
   * Same language on both client and server (GWT, Node.js, Dart)
   * What's happen to GWT?

---

Thanks for you attention
========================
Samples: 

   * https://github.com/syjer/weakdot
   * https://github.com/chiodonia/dartlang

---

Resources
=========

   * http://dartlang.org
   * Specifications: http://www.dartlang.org/docs/spec/
   * Is Dart solving the famous Java puzzlers? See http://www.dartlang.org/articles/puzzlers/chapter-1.html
   * Style guides: http://www.dartlang.org/articles/style-guide/
   * FAQ: http://www.dartlang.org/support/faq.html
  

