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
* Performance

!SLIDE left

# Model

* Persistance (Local/Rest/Rails Storage)
* Validations (presence, numeric, min/max length, etc.)
* Associations (belongsTo, hasMany, )

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

* index show new edit create destroy

``` coffeescript
class MassCall.RecordingsController extends Batman.Controller
  routingKey: 'recordings'

  index: (params) ->
    MassCall.Recording.load (err,results) =>
      @set 'recordings', new Batman.Set(results...)
      
  show: (params) ->
 
  new: (params) ->
  
  edit: (params) ->
  
  create: (params) ->
  
  update: (params) ->
```

!SLIDE left

# Views

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

!SLIDE left

# Routing

``` coffeescript
window.MassCall = class MassCall extends Batman.App
  Batman.ViewStore.prefix = 'assets/views'

  @root 'app#index'
  @resources 'recordings'
```




!SLIDE

# The bad
No batman.js 1.0 (whenever Shopify 2 launches)
Docs are terrible



!SLIDE

# Refs
http://devrates.com/project/show/79079/Batmanjs -- Intro batman logo
https://github.com/infews/keydown -- Used to make presentation
