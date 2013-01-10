# batman-presentation

!SLIDE

![](images/batman_logo.png)

###Fighting Crime and Kicking Apps  

Twitter: **@RyanonRails**  
Email: **Ryan@System88.com**

!SLIDE left

# Why batman.js?  

* CoffeeScript
* Convention over Configuration
* UI and Bindings in HTML  
* Restful 
* Tested
* Fast

!SLIDE left

# Model

* Persistance (Local/Rest/Rails Storage)
* Validations (presence, numeric, min/max length, etc.)
* Associations (belongsTo, hasMany)

``` coffeescript
class MassCall.Recording extends Batman.Model
  @resourceName: 'recording'
  @persist Batman.RailsStorage
  
  @encode 'url', 'label'
  @validate 'url', presence: yes
  
  @belongsTo 'user'
```

!SLIDE left

# Controller

* index show new create update destroy

``` coffeescript
class MassCall.RecordingsController extends Batman.Controller
  routingKey: 'recordings'

  index: (params) ->
    MassCall.Recording.load (err,results) =>
      @set 'recordings', new Batman.Set(results...)
      
  show: (params) ->
 
  new: (params) ->
  
  create: (params) ->
  
  update: (params) ->

  destroy: (params) ->
```

!SLIDE left

# Views

* Partials
* View binding (2 way)
* Filters

``` html
  recordings/index.html  
  
  <div data-foreach-recording="recordings" data-mixin="animation">
      <div data-partial="recordings/_recording">
      </div>
  </div>
```

``` html
  recordings/_recording.html
  
  <span data-bind="recording.label"></span>
  <span data-bind="recording.url"></span>
```

``` html
  <span data-bind="recording.label | truncate 100 "/>
```

``` html
  <span data-showif="recording.valid">this is a valid recording</span></p>
```


!SLIDE left

# Routing  

* Restful  

``` coffeescript
window.MassCall = class MassCall extends Batman.App
  Batman.ViewStore.prefix = 'assets/views'

  @root 'app#index'
  @resources 'recordings'
```

``` html
  Mass Call App!
  <br/>
  View all recordings:
  
  <a data-route="routes.recordings">view all recordings</a>
  <a data-route="routes.recordings" href="/recordings"></a>
  
  <a data-route="routes.recordings[recording]">show a recording</a>
  <a data-route="routes.recordings[recording]" href="/recordings/1"></a>
```

!SLIDE left

# Other Good Stuff  

* Generators (model, controller, routes)
* Rails gem 
* npm & node.js for quick hacking
* jQuery or solo version
* gzipped to 45kb

!SLIDE left

# The bad

* No batman.js 1.0 (out whenever Shopify 2 launches)
* Version churn (breaking changes)
* Docs are constantly out of date
* Error messages not helpful/incorrect
* Examples out of date (partially rectified)
* No view generators/sub par controller generators (hopefully fixed in the next couple of weeks)
* npm packages randomly broken
* No websockets (yet)

!SLIDE left

# Examples

http://addyosmani.github.com/todomvc/labs/architecture-examples/batman/index.html


!SLIDE left

# Refs  

* http://devrates.com/project/show/79079/Batmanjs -- Intro batman logo
* https://github.com/infews/keydown -- Used to make presentation
