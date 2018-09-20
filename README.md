# ReactDraggAndDrop
Drag &amp; Drop HOC implemented for both React (mobile and desktop) and React-Native.

## Concept
In a container component, provide draggable and droppable HOC function to convert any component into D&D  component.

### Draggable
ddComponent = draggable(component, config)

For React-Native, the HOC function creates a PanResponder with default implementation of onMoveShouldSetPanResponder(), onPanResponderMove() etc. User can put any ddComponent as the child of the container. Those event handler did not capture the touch so container also got the events for droppables.


For React, need to catch different event and default event handler implementation. Mobile and desktop web may need different event.

### Droppable
ddComponent = droppable(component, config)

For React-Native, the HOC function keep a list of all child droppable components. The HOC also creates a onLayout() function implementation and add it to the returned ddComponent. So the container know the position of the droppable child components (unless React-Native can provide the child components to parent container). Since container also get the touch move events, container will call the droppable callback (provided in the config) when the draggable is enter/leave/drop inside the droppables.

The config need to provide several callback functions to show UI cue to user
onDropEnter(): callback for droppable to show differently whether a drop is allowed or not, returning true for allowed.
onDropLeave():
onDrop():

React can provide the children info. Container may not need to keep the children list and their position info. 
