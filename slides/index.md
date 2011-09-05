# Introduction

.notes: You are Rails developers, with some JS experience (reading, maybe some jQuery).

# Presenter Notes

* Your Markdown source files must be suffixed by .md, .markdn, .mdown or .markdown
* To create a title slide, render a single h1 element (eg. # My Title)
* Separate your slides with a horizontal rule (--- in markdown) except at the end of md files
* Your other slides should have a heading that renders to an h1 element
* To highlight blocks of code, put !{lang} where {lang} is the pygment supported language identifier as the first indented lin
* https://github.com/adamzap/landslide

---

# My Goal

.notes: Motivate and discuss client-side MVC.   Introduce Backbone.js  Discuss Rails + Backbone integration

---

* what is backbone
** clientside mvc, what, why
** framework advantages: organization.  encourages modularity => testability, reuse.
* moving parts: model, collection, view, router, history (high level)

* other frameworks, compare/contrast
** sc2. less docu, strobe platform, more libs (what are they?)
** spine. extremely similar to backbone.  smaller community.
** knockout, mvvm.
* describe each component
* show an example

* code tour: client side.  back to front.
** routing
** view class
** models and collections
** templating
** underscore.js.  Mixed into collections.
* code tour: server side.  rails integration.  back to front.
** file organization
** JSON APIs
*** activerecord to_json
*** Model#as_json/presenter/rabl/etc
*** controller params in 3.1
** asset pipeline in 3.1 (or packager in 3.0)

* more advanced topics
** pushState for history.  look at github.  opt-in.  server-side support.
** testing
*** selenium integration testing.  capybara-webkit.
*** jasmine for isolation testing.
**** fixture html

* further reading
** non-rails backends: remote JSON APIs, localstorage, websocket sync, XML
** offline apps. html5 offline app manifest?  any plugins?
** websockets
** backbone on the server with node.js, now.js
** bone up on JS: short: good parts.  long: tddjs.

* wrapup
** slides url
** backbone google group
** backbone on rails ebook
** peepcode videos
** my contact info
