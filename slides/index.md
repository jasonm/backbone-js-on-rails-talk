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
# Tell them what youre going to tell tem
* and reiterate a few times, probably.
* especially before "moving parts" and "walk through a request"

---
# Backbone.js and Rails:

These days, some web apps have more code on the client than on the server.
Learn how Backbone.js is put together, how to use it with Rails, and how to
make building JavaScript-heavy apps a pleasure.

---

# My Goal

* ...

# Presenter Notes

notes: Motivate and discuss client-side MVC.   Introduce Backbone.js  Discuss Rails + Backbone integration

---

# what is backbone

* clientside mvc, what, why
* framework advantages: organization.  encourages modularity => testability, reuse.

---

# moving parts

*  model, collection, view, router, history (high level)

---

# other frameworks, compare/contrast

* sc2. less docu, strobe platform, more libs (what are they?)
* spine. extremely similar to backbone.  smaller community.
* knockout, mvvm.

---
# describe each component

* ...

---
# show an example
* trajectory

---

# walk through a request
* GET /accounts/thoughtbot/projects/opensource/stories#84245
* browser http request to rails
* rails router, controller, model, view
* response
** htmls
** javascripts tags
** json to be bootstrappin the datas
* browser fetches the javascripts
* initialize backbone
** bootstrap collections
** instantiate router (Stories or Discussions)
** .start()
* send hash '#84245' to backbone router
* router routes, dispatches to action
* action
* view(modelOrCollection)
* view calls template, returns htmls
* view calls the jquery
* dom is updated

---
# Code tour: client side

* back to front.
    * routing
    * view class
    * models and collections
    * templating
    * underscore.js.  Mixed into collections.

---
# Code tour: server side

* rails integration.  back to front.
    * file organization
    * JSON APIs
        * activerecord to_json
        * Model#as_json/presenter/rabl/etc
        * controller params in 3.1
    * asset pipeline in 3.1 (or packager in 3.0)

---
# More advanced topics
* pushState for history.  look at github.  opt-in.  server-side support.
* testing
    * selenium integration testing.  capybara-webkit.
    * jasmine for isolation testing.
        * fixture html

---
# Further reading

* todo app, simple to get started
* non-rails backends: remote JSON APIs, localstorage, websocket sync, XML
* offline apps. html5 offline app manifest?  any plugins?
* websockets
* backbone on the server with node.js, now.js
* bone up on JS: short: good parts.  long: tddjs.

---
# Links

* [These slides](http://jayunit.net/backbone-js-on-rails-talk)
* [Backbone Google Group](https://groups.google.com/group/backbonejs)
* [Backbone on Rails eBook by thoughtbot](http://workshops.thoughtbot.com/backbone-js-on-rails)
* [Peepcode episodes on Backbone](http://peepcode.com/products/backbone-js)
* [jason.p.morrison@gmail.com](mailto:jason.p.morrison@gmail.com)
* [http://jayunit.net](http://jayunit.net)
