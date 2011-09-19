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
# Apps shifting client-side

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
# Organize your JavaScript

# Presenter Notes

* Hands up: Procedural apps? Tag-soup PHP/JSP/whatever-SP?  Now, framework?
* Patterns for organization.  MVC is one.  Good for GUI.
* MVC over HTTP is often stateless.  Some state maintained with session
* MVC in GUI is stateful.  Embrace this.

---
# But which framework?

* Cappuccino
* SproutCore (1.x, 2.x)
* Knockout.js
* Batman.js
* JavaScriptMVC
* Spine.js
* Backbone.js
* Angular, Coherent, PureMVC-js,  AFrameJS, TrimPath Junction, ...

# Presenter Notes

* [Decision Fatigue NY Times Mag article](http://www.nytimes.com/2011/08/21/magazine/do-you-suffer-from-decision-fatigue.html)
* Cappuccino/SproutCore: UI controls.  Desktop like.
* SC2: Similar, larger.  Less doc.  Declarative bindings, even in templates.
* Knockout: MVVM.  WCF, Silverlight.
* Batman: Node server, share models, data-bind templates
* JavaScriptMVC: Larger, older, generators, dep mgmt, builds, testing, jQuery-based-and-like, JSON/REST transport
* Spine.js: Very similar.  Even smaller.  Coffee.  Fully async, client rules.
* Backbone: Small, pragmatic, extracted from DocumentCloud

---
# Backbone.js

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

# Presenter Notes

* Trajectory on local
* stories#index

---
# Walk through a request

* URI: `/projects/oss/stories#84245`
* `GET /projects/oss/stories`
* Rails response: HTML, `<script>`s, JSON

---
# Walk through a request

* Bootstrap collections
* Instantiate router
* `Backbone.history.start()`

---
# Walk through a request

* Route `'#84245'` fragment
* Dispatch to action
* `new View(modelOrCollection)`
* event and data bindings
* `view.render()`
* `_.template()`
* `$('#app').html(theViewHtmls)`

---
# Code tour: client side

# Presenter Notes

* Back to front.
    * Script load
    * JSON collection bootstrapping
    * Init -> Backbone.history.start()
    * Routing
    * View class
    * Models and collections
    * Templating
    * Underscore.js.  Mixed into collections.

---
# Code tour: server side

# Presenter Notes

* Rails integration.  Back to front.
    * File organization for 3.0: JS, JST, Jammit
    * File organization for 3.1: Asset pipeline, [`rails-backbone` gem](https://github.com/codebrew/backbone-rails)
    * JSON APIs
        * [`ActiveRecord.include_root_in_json`](https://github.com/jasonm/wizards/blob/master/config/initializers/wrap_parameters.rb)
        * Rails 3.1 [Params Wrapper](https://github.com/rails/rails/blob/master/actionpack/lib/action_controller/metal/params_wrapper.rb)
        * Model#as_json probably isnt the best place for presentation: Presenter object, [rabl](https://github.com/nesquena/rabl)
    * [CSRF Token](https://github.com/codebrew/backbone-rails/blob/master/vendor/assets/javascripts/backbone_rails_sync.js#L26-27)

---
# Bonus stuff!

# Presenter Notes

* What is left?
    * Testing
    * pushState
    * push sync (WebSocket)

---
# Testing

--- 
# Testing
* It's just JavaScript!
# Presenter Notes
* Yes it's just JavaScript.
* But...

--- 
# Testing
* It's just **stateful and asynchronous business and presentation logic written in** JavaScript!
# Presenter Notes
* Luckily...

--- 
# Testing
* It's just stateful and asynchronous business and presentation logic written in **modular, decoupled** JavaScript!

---
# Testing
* Isolation: Jasmine
* Integration: capybara-webkit, selenium

# Presenter Notes

* [Jasmine](http://pivotal.github.com/jasmine/) goodies!  Get these.
    * Spy/stub/mock, even your HTTP, with [sinon.js](http://sinonjs.org/)
    * If you're looking for factory_girl.js, it's called [Rosie](https://github.com/bkeepers/rosie)
    * [guard-jasmine](https://github.com/netzpirat/guard-jasmine) autotest your Jasmine with headless webkit ([phantomjs](http://www.phantomjs.org/))
    * Write in CoffeeScript and use the 3.1 asset pipeline with [jasminerice](https://github.com/bradphelan/jasminerice)
    * Get started with James Newbery's excellent blog posts on [testing Backbone with Jasmine](http://tinnedfruit.com/2011/03/03/testing-backbone-apps-with-jasmine-sinon.html)
    * Check out his [examples on GitHub](https://github.com/froots/backbone-jasmine-examples)
* Integration test with:
    * [capybara-webkit](https://github.com/thoughtbot/capybara-webkit) for fast, headless, accurate WebKit testing
    * Selenium for other browsers, or if capybara-webkit has issues.

---
# pushState

# Presenter Notes

* Look at github.
* Opt-in.
* `Backbone.history.start({pushState: true});`
* Server-side support.

---
# Push synchronization

# Presenter Notes

* Rails `Model#save` cascades to clients: [backbone_sync-rails](https://github.com/jasonm/backbone_sync-rails) over pubsub bus [Faye](http://faye.jcoglan.com/)
* Work-in-progress [Software transactional memory](http://en.wikipedia.org/wiki/Software_transactional_memory) sync: [https://github.com/codeparty/racer](https://github.com/codeparty/racer)
    * Future plans: [diff-match-patch](http://code.google.com/p/google-diff-match-patch/), [Operational transform](http://en.wikipedia.org/wiki/Operational_transformation)
* [Now.js](http://nowjs.org/)
* [Substack DNode](https://github.com/substack/dnode)
* [Data.js](http://substance.io/michael/data-js): Data Manipulation and Graph Persistence for Node.js and the Browser.  Can ride now.js transport.
    * substance.io, above, is written with Backbone.js, and is open source [https://github.com/michael/substance](https://github.com/michael/substance)
* [Backbone on the server with node.js](http://andyet.net/blog/2011/feb/15/re-using-backbonejs-models-on-the-server-with-node/)... with DNode or NowJS (?!)

---
# Get your code on

* [Todo App example](http://documentcloud.github.com/backbone/#examples-todos)
* [James Newbery's jasmine examples](https://github.com/froots/backbone-jasmine-examples/tree/master/public/javascripts)

---
# Further reading: Books on JavaScript

* [JavaScript: The Good Parts](http://shop.oreilly.com/product/9780596517748.do) by Douglas Crockford
* [JavaScript Web Applications](http://shop.oreilly.com/product/0636920018421.do) by Alex MacCaw (Spine.js author)
* [Test-Driven JavaScript Development](http://tddjs.com/) by Christian Johansen
* [JavaScript Patterns](http://shop.oreilly.com/product/9780596806767.do) by Stoyan Stefanov
* [JavaScript: The Definitive Guide](http://shop.oreilly.com/product/9780596805531.do) by David Flanagan

---
# Further reading: Online resources

* [Official Backbone docs](http://documentcloud.github.com/backbone/) - they're excellent!
* [Backbone Google Group](https://groups.google.com/group/backbonejs)
* [Backbone on Rails eBook](http://workshops.thoughtbot.com/backbone-js-on-rails)
* [Peepcode episodes on Backbone](http://peepcode.com/products/backbone-js)

---
# Thanks!

* Me:
    * [jason.p.morrison@gmail.com](mailto:jason.p.morrison@gmail.com)
    * [@jayunit](http://twitter.com/jayunit)
    * [http://jayunit.net](http://jayunit.net)
* Slides:
    * [View slides online](http://jayunit.net/backbone-js-on-rails-talk)
    * [View slides source on GitHub](http://github.com/jasonm/backbone-js-on-rails-talk)
