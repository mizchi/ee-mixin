# React EventEmitter

EventEmitter mixin for react

```
npm install mizchi/react-event-emitter
```

## Example

```coffee
EventEmitterMixin = requrie 'react-event-emitter'

MyComponent = React.createClass
  mixins: [EventEmittermixin()]
	onClick: ->
		@emit 'foo'

  render: ->
		React.createElement 'button', {onClick: @onClick}, 'onClick'

EventEmitter = require 'event-emitter'
ee = new EventEmitter
React.render MyClass(events: ee), document.body

ee.on 'foo', ->
  console.log 'receive foo'
```
