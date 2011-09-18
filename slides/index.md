---
# Backbone.js on Rails

---
# Goals for this talk


# Presenter Notes
## After this talk, you will:
* Know why and how to use a client-side framework
* Be able to read up on a few of them
* Be able to follow along with Backbone tutorials
* Know how to add Backbone to a new or existing Rails app

---
# More client side

# Presenter Notes

These days, some web apps have more code on the client than on the server.

Learn how Backbone.js is put together, how to use it with Rails, and how to make building JavaScript-heavy apps a pleasure.

How much JS?

* Airbrake: Almost 0
* Copycopter: 30%
* Trajectory 41%
* IoraHealth: 62%
* Substance.io: 100%

---
# Organize your code

# Presenter Notes

* Hands up: Procedural apps? Tag-soup PHP/JSP/whatever-SP?  Now, framework?
* Patterns for organization.  MVC is one.  Good for GUI.
* MVC over HTTP is often stateless.  Some state maintained with session
* MVC in GUI is stateful.  Embrace this.

---
# But which one?

* Cappuccino
* SproutCore (1.x, 2.x)
* Knockout.js
* JavaScriptMVC
* Spine.js
* Backbone.js
* Angular, Coherent, PureMVC-js,  AFrameJS, TrimPath Junction, ...

# Presenter Notes

* [Decision Fatigue NY Times Mag article](http://www.nytimes.com/2011/08/21/magazine/do-you-suffer-from-decision-fatigue.html)
* Cappuccino/SproutCore: UI controls.  Desktop like.
* SC2: Similar, larger.  Less doc.  Declarative bindings, even in templates.
* Knockout: MVVM.  WCF, Silverlight.
* JavaScriptMVC: Larger, older, generators, dep mgmt, builds, testing, jQuery-based-and-like, JSON/REST transport
* Spine.js: Very similar.  Even smaller.  Coffee.  Fully async, client rules.
* Backbone: Small, pragmatic, extracted from DocumentCloud

---

# Moving parts

* History
* Router
* View
* Model
* Collection
* Sync
* Underscore
* $

# Presenter Notes

* History - Handles hashchange, pushstate, BB.history.start()
* Router - read fragment, dispatch to action
* View - Root DOM `el`, class/id/tagName, `this.$`, `events`, `$.delegate`, any templating
* Model - Conversions, computed properties, validations, access control, events change/change:attr,destroy,error
* Collection - Ordered set of models.  URL, fetch(), reset(json), _.methods, comparator, events reset/add/remove/all model events
* Sync - Encapsulation of persistence. Default `$.ajax` to RESTful JSON API.  Designed for override, global or per-class.
* Underscore -  FP (select, reduce), bind, template, deep isEqual, clone, tap
* $ - jQuery || Zepto


---
# Example

---

# Walk through a request

* GET

# Presenter Notes

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
    * asset pipeline

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
