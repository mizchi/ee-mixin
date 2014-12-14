# ee-mixin - React EventEmitter Mixin

EventEmitter mixin for react

```
$ npm install mizchi/ee-mixin --save
```

## Rules

- If there is given events as EventEmitter, emit by it.
- else create internal event dispatcher

## Example

```coffee
eeMixin = requrie 'ee-mixin'

MyComponent = React.createClass
  mixins: [eeMixin]
	onClick: ->
		@emit 'clicked'

  render: ->
		React.createElement 'button', {onClick: @onClick}, 'onClick'

{EventEmitter} = require 'events'
ee = new EventEmitter

# if you give events as EventEmitter, use it in component
# else create internal eventemitter and can give it to child 
c = React.render MyComponent(emitter: ee), document.body

c.getEventEmitter() is ee #=> true in this context.given EventEmitter or global EventEmitter

ee.on 'clicked', ->
  console.log 'receive clicked event'
```

