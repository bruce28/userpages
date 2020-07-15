Synonyms - Go and JavaScript
############################

:date: 2017-12-07T21:47+08:00
:modified: 2020-07-15T08:48+08:00
:tags: Go, Golang, GopherJS, Go to JavaScript, DOM, JavaScript,
       Frontend Programming in Go
:category: Frontend Programming in Go
:summary: Synonyms - Go_/GopherJS_ idioms and snippets translated to JavaScript_
:og_image: https://pbs.twimg.com/profile_images/605816243870760960/4hP2sH_O.png
:adsu: yes


Inspired by [4]_, This post provides synonyms of Golang_ and JavaScript_ in
frontend programming, and served as references for developers who already have
basic understanding of JavaScript and GopherJS_/godom_.

.. contents:: **Table of Content**

.. adsu:: 2

----


import packages
+++++++++++++++

**JavaScript**: no need to import any packages

**GopherJS**

.. code-block:: go

  import (
  	"github.com/gopherjs/gopherjs/js"
  )

**GopherJS + godom**

.. code-block:: go

  import (
  	. "github.com/siongui/godom"
  )


----


window_ object
++++++++++++++

**JavaScript**

.. code-block:: javascript

  window

**GopherJS**

.. code-block:: go

  js.Global

**GopherJS + godom**

.. code-block:: go

  Window


----


`alert()`_ method
+++++++++++++++++

**JavaScript**

.. code-block:: javascript

  alert("Hello World");

**GopherJS**

.. code-block:: go

  js.Global.Call("alert", "Hello World")

**GopherJS + godom**

.. code-block:: go

  Window.Alert("Hello World")


----


`setTimeout()`_ method
++++++++++++++++++++++

**JavaScript**

.. code-block:: javascript

  setTimeout(function() {
    console.log("3 seconds timeout");
  }, 3000);


**Go (or GopherJS)**

.. code-block:: go

  import "time"

  time.AfterFunc(3*time.Second, func() {
  	println("3 seconds timeout")
  })

.. rubric:: `Run Code on GopherJS Playground <https://gopherjs.github.io/playground/#/LjCARICREZ>`__
   :class: align-center

.. adsu:: 3

----


JavaScript new Keyword
++++++++++++++++++++++

**JavaScript**

.. code-block:: javascript

  var d = new Date();
  console.log(d);


**GopherJS**

.. code-block:: go

  d := js.Global.Get("Date").New()
  println(d)


**GopherJS + godom**

.. code-block:: go

  d := Window.Get("Date").New()
  println(d)


new with Chain Dots
===================

**JavaScript**

.. code-block:: javascript

  var x = new joint.dia.Graph;


**GopherJS**

.. code-block:: go

  x := js.Global.Get("joint").Get("dia").Get("Graph").New()


**GopherJS + godom**

.. code-block:: go

  x := Window.Get("joint").Get("dia").Get("Graph").New()


new with option
===============

**JavaScript**

.. code-block:: javascript

  const ke = new KeyboardEvent("keyup", {keyCode: 13});
  document.body.dispatchEvent(ke);


**GopherJS**

.. code-block:: go

  option := js.Global.Get("Object").New()
  option.Set("keyCode", 13)
  ke := js.Global.Get("KeyboardEvent").New("keyup", option)
  js.Global.Get("document").Get("body").Call("dispatchEvent", ke)


**GopherJS + godom**

.. code-block:: go

  option := Window.Get("Object").New()
  option.Set("keyCode", 13)
  ke := Window.Get("KeyboardEvent").New("keyup", option)
  Document.Get("body").Call("dispatchEvent", ke)

.. adsu:: 4


----


querySelector
+++++++++++++

**JavaScript**

.. code-block:: javascript

  var elm = document.querySelector("#foo");


**GopherJS**

.. code-block:: go

  elm := js.Global.Get("document").Call("querySelector", "#foo")


**GopherJS + godom**

.. code-block:: go

  elm := Document.QuerySelector("#foo")


----


querySelectorAll
++++++++++++++++

**JavaScript**

.. code-block:: javascript

  var nodeList = document.querySelectorAll("div");
  for (var i = 0; i < nodeList.length; ++i) {
    var elm = nodeList[i];
    // do something with the element
  }


**GopherJS**

.. code-block:: go

  d := js.Global.Get("document")
  nodeList := d.Call("querySelectorAll", "div")
  length := nodeList.Get("length").Int()
  for i := 0; i < length; i++ {
  	elm := nodeList.Call("item", i)
  	// do something with the element
  }


**GopherJS + godom**

.. code-block:: go

  nodeList := Document.QuerySelectorAll("div")
  for _, elm := range nodeList {
  	// do something with the element
  }


----


getElementById
++++++++++++++

**JavaScript**

.. code-block:: javascript

  var element = document.getElementById("foo");


**GopherJS**

.. code-block:: go

  element := js.Global.Get("document").Call("getElementById", "foo")


**GopherJS + godom**

.. code-block:: go

  element := Document.GetElementById("foo")


----


innerHTML
+++++++++

**JavaScript**

.. code-block:: javascript

  // set innerHTML
  element.innerHTML = "<strong>Hello World</strong>";

  // get innerHTML
  console.log(element.innerHTML);


**GopherJS**

.. code-block:: go

  // set innerHTML
  element.Set("innerHTML", "<strong>Hello World</strong>")

  // get innerHTML
  println(element.Get("innerHTML").String())


**GopherJS + godom**

.. code-block:: go

  // set innerHTML
  element.SetInnerHTML("<strong>Hello World</strong>")

  // get innerHTML
  println(element.InnerHTML())


----


textContent
+++++++++++

**JavaScript**

.. code-block:: javascript

  // set textContent
  element.textContent = "Hello World";

  // get textContent
  console.log(element.textContent);


**GopherJS**

.. code-block:: go

  // set textContent
  element.Set("textContent", "Hello World")

  // get textContent
  println(element.Get("textContent").String())


**GopherJS + godom**

.. code-block:: go

  // set textContent
  element.SetTextContent("Hello World")

  // get textContent
  println(element.TextContent())


----


addEventListener
++++++++++++++++

**JavaScript**

.. code-block:: javascript

  element.addEventListener("click", function(e) {
    // do something here
  });


**GopherJS**

.. code-block:: go

  element.Call("addEventListener", "click", func(event *js.Object) {
  	// do something here
  })


**GopherJS + godom**

.. code-block:: go

  element.AddEventListener("click", func(e Event) {
  	// do something here
  })

.. adsu:: 5

----


createElement
+++++++++++++

**JavaScript**

.. code-block:: javascript

  document.createElement("span");


**GopherJS**

.. code-block:: go

  js.Global.Get("document").Call("createElement", "span")


**GopherJS + godom**

.. code-block:: go

  Document.CreateElement("span")

----


createTextNode
++++++++++++++

**JavaScript**

.. code-block:: javascript

  document.createTextNode("Hello World");


**GopherJS**

.. code-block:: go

  js.Global.Get("document").Call("createTextNode", "Hello World")


**GopherJS + godom**

.. code-block:: go

  Document.CreateTextNode("Hello World")

----


appendChild
+++++++++++

**JavaScript**

.. code-block:: javascript

  parentElement.appendChild(childElement);


**GopherJS**

.. code-block:: go

  parentElement.Call("appendChild", childElement)


**GopherJS + godom**

.. code-block:: go

  parentElement.AppendChild(childElement)

----


HTML data-* Attribute
+++++++++++++++++++++

**HTML**

.. code-block:: html

  <div id="foo" data-demo-value="hello world"></div>


**JavaScript**

.. code-block:: javascript

  var f = document.querySelector("#foo");

  // get value
  console.log(f.dataset.demoValue);

  // set value
  f.dataset.demoValue = "world hello";


**GopherJS**

.. code-block:: go

  f := js.Global.Get("document").Call("querySelector", "#foo")

  // get value
  println(f.Get("dataset").Get("demoValue").String())

  // set value
  f.Get("dataset").Set("demoValue", "world hello")


**GopherJS + godom**

.. code-block:: go

  f := Document.QuerySelector("#foo")

  // get value
  println(f.Dataset().Get("demoValue").String())

  // set value
  f.Dataset().Set("demoValue", "world hello")

----


Inline style Property
+++++++++++++++++++++


**JavaScript**

.. code-block:: javascript

  // set the color of element
  elm.style.color = "red";

  // get the color of element
  console.log(elm.style.color);


**GopherJS**

.. code-block:: go

  // set the color of element
  elm.Get("style").Set("color", "red")

  // get the color of element
  println(elm.Get("style").Get("color").String())


**GopherJS + godom**

.. code-block:: go

  // set the color of element
  elm.Style().SetColor("red")

  // get the color of element
  println(elm.Style().Color())

----


classList Property
++++++++++++++++++

**JavaScript**

.. code-block:: javascript

  // add class to element
  element.classList.add("invisible");

  // check if specified class value exists in class attribute of the element
  element.classList.contains("invisible");

**GopherJS**

.. code-block:: go

  // add class to element
  element.Get("classList").Call("add", "invisible")

  // check if specified class value exists in class attribute of the element
  element.Get("classList").Call("contains", "invisible").Bool()


**GopherJS + godom**

.. code-block:: go

  // add class to element
  element.ClassList().Add("invisible")

  // check if specified class value exists in class attribute of the element
  element.ClassList().Contains("invisible")


.. adsu:: 6


Navigator Language API
++++++++++++++++++++++

**JavaScript**

.. code-block:: javascript

  // preferred language of the user, string type
  console.log(navigator.language);

  // languages known to the user, array type
  console.log(navigator.languages);


**GopherJS**

.. code-block:: go

  // preferred language of the user, cast as string
  println(js.Global.Get("navigator").Get("language").String())

  // languages known to the user, also cast as string
  println(js.Global.Get("navigator").Get("languages").String())


**GopherJS + godom**

.. code-block:: go

  // preferred language of the user, string type
  println(Window.Navigator().Language())

  // languages known to the user, string type
  println(Window.Navigator().Languages())


null Check
++++++++++

**JavaScript**

.. code-block:: javascript

  if (value === null) {
      // do something
  }


**GopherJS**

.. code-block:: go

  if value == nil {
  	// do something
  }

.. rubric:: `Run Code on GopherJS Playground <https://gopherjs.github.io/playground/#/59HcuBcHOk>`__
   :class: align-center


undefined Check
+++++++++++++++

**JavaScript**

.. code-block:: javascript

  if (something === undefined) {
      // do something
  }


**GopherJS**

.. code-block:: go

  if something == js.Undefined {
  	// do something
  }

.. rubric:: `Run Code on GopherJS Playground <http://www.gopherjs.org/playground/#/Kxr4h5nxBQ>`__
   :class: align-center


----

References:

.. [1] `GopherJS - A compiler from Go to JavaScript <http://www.gopherjs.org/>`_
       (`GitHub <https://github.com/gopherjs/gopherjs>`__,
       `GopherJS Playground <http://www.gopherjs.org/playground/>`_,
       |godoc|)
.. [2] `Bindings · gopherjs/gopherjs Wiki · GitHub <https://github.com/gopherjs/gopherjs/wiki/bindings>`_
.. [3] `GitHub - siongui/godom: Make DOM manipulation in Go as similar to JavaScript as possible. (via GopherJS) <https://github.com/siongui/godom>`_
.. [4] `Synonyms - Dart, JavaScript, C#, Python | Dart <https://www.dartlang.org/resources/synonyms>`_
.. [5] `[Golang] GopherJS Synonyms with JavaScript <{filename}../../../2016/01/29/go-gopherjs-synonyms-with-javascript%en.rst>`_

.. _GopherJS: http://www.gopherjs.org/
.. _DOM binding: https://godoc.org/honnef.co/go/js/dom
.. _JavaScript: https://en.wikipedia.org/wiki/JavaScript
.. _Go: https://golang.org/
.. _Golang: https://golang.org/
.. _window: http://www.w3schools.com/jsref/obj_window.asp
.. _Object: https://godoc.org/github.com/gopherjs/gopherjs/js#Object
.. _GetWindow(): https://godoc.org/honnef.co/go/js/dom#GetWindow
.. _document: http://www.w3schools.com/jsref/dom_obj_document.asp
.. _GopherJS bindings for the JavaScript DOM APIs: https://godoc.org/honnef.co/go/js/dom
.. _DOM: https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model
.. _alert(): http://www.w3schools.com/jsref/met_win_alert.asp
.. _setTimeout(): https://www.google.com/search?q=setTimeout
.. _navigator: https://developer.mozilla.org/en-US/docs/Web/API/Navigator
.. _NavigatorLanguage: https://developer.mozilla.org/en-US/docs/Web/API/NavigatorLanguage
.. _getElementById(): https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById
.. _innerHTML: http://www.w3schools.com/jsref/prop_html_innerhtml.asp
.. _textContent: http://www.w3schools.com/jsref/prop_node_textcontent.asp
.. _addEventListener(): https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener
.. _Remove all child nodes: https://www.google.com/search?q=javascript+remove+all+child+nodes
.. _createElement: https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement
.. _createTextNode: https://developer.mozilla.org/en-US/docs/Web/API/Document/createTextNode
.. _location: http://www.w3schools.com/jsref/obj_location.asp
.. _querySelector: https://www.google.com/search?q=querySelector
.. _querySelectorAll: https://www.google.com/search?q=querySelectorAll
.. _NodeList: https://developer.mozilla.org/en-US/docs/Web/API/NodeList
.. _godom: https://github.com/siongui/godom

.. |godoc| image:: https://godoc.org/github.com/gopherjs/gopherjs/js?status.png
   :target: https://godoc.org/github.com/gopherjs/gopherjs/js
