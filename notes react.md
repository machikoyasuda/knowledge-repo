Creating components

# React.createClass()

# properties: IMMUTABLE.

- defined when components are created.
- can validate presence.
- this.props.name to read the name property passed into the creation of the class

# state: MUTABLE.
- internal data-set that affects the rendering of the components.
- cannot validate presence.
- private data

 
# render()

- render() *required - returns a single child component and also null/false to indicate you don't want anything rendered. 
- render() should be pure: it does not modify component state
- render() should return the same result each/every time it is invoked. 
- render() does not read from or write to the DOM or otherwise interact with the browser. 

Methods
===

# getInitialState() 
- invoked once before the component is mounted
- return value will be used as the initial value of this.state

# getDefaultProps()
- invoked once and cached when the class is created

# propTypes()

# mixins[]

Lifecycle Methods
===

Methods executed at specific points in a component lifecycle: 

# componentWillMount()
- invoked once
- immediately before initial rendering

# componentDidMount()
- invoked once
- on the client
- immediately after initial rendering occurs
- the component has a DOM representation which you can access via this.getDOMNode()

# Updating - componentWillReceiveProps()
- React to a prop transition before render() is called by using this.setState()

# Updating - shouldComponentUpdate()


# DOM Events
- onClick onDoubleClick onDrag onDragEnd onDragEnter onDragExit onDragLeave
onDragOver onDragStart onDrop onMouseDown onMouseEnter onMouseLeave
onMouseMove onMouseOut onMouseOver onMouseUp
- onScroll


# State Machine
 •	Component lifestyle has three distinct states:
	 ◦	Components are breathed into life by being mounted
	 ◦	Components are placed in an update state when setState or setProps is called
	 ◦	Components are unmounted when they no longer are generated from render

# API

c.setState({ x: y });
c.setProps({ .. });

c.replaceProps({ .. });
c.replaceState({ .. });

c.getDOMNode()

c.forceUpdate()
c.isMounted()

# Lifecycle

render: function()
getInitialState: function()
getDefaultProps: function()
propTypes: {}
mixins: []
statics: { .. } /* static methods */
displayName: '..'

componentWillMount
componentWillUpdate
componentWillUnmount

componentDidMount
componentDidUpdate
componentDidUnmount