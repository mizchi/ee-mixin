# React EventEmitter

EventEmitter mixin for react

```
npm install mizchi/react-event-emitter
```

## Rules

- If there is given events as EventEmitter, emit by it.
- else create internal event dispatcher

## Example

```coffee
EventEmitterMixin = requrie 'react-event-emitter'

MyComponent = React.createClass
  mixins: [EventEmitterMixin()]
	onClick: ->
		@emit 'clicked'

  render: ->
		React.createElement 'button', {onClick: @onClick}, 'onClick'

EventEmitter = require 'event-emitter'
ee = new EventEmitter

# if you give events as EventEmitter, use it in component
# else create internal eventemitter and can give it to child 
c = React.render MyComponent(events: ee), document.body

c.getEventEmitter() is ee #=> true in this context. local EventEmitter or given EventEmitter

ee.on 'clicked', ->
  console.log 'receive clicked event'
```

