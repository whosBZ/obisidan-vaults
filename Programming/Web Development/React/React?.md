- A modern frontend framework for building modern user interfaces
- Splits a user interface into small, self contained, reusable items.
- It is a declarative programming paradigm where you describe the desired results instead of explicitly listing all steps to create it

## Reactive Components

- Reacts user interface components are reactive
- This means they handle their own isolated sattes and update the pages HTML as soon as state changes
- Changes to the react code instantly affect a browser document object model (DOM)

## The DOM

- A document object model represents a website as a tree in which each HTML element is a node
- IT also provides an API for each node and for the website in general allowing scripts to modify a whole website, or specific node.
- Updates to the DOM are expensive so React uses a virtual DOM 

## Virtual DOM

- React keeps an in memory copy of the actual browser DOM which is later synced with the real thing
- This allows calculation of the differences between the real DOM and virtual DOM allowing a choice in what to update, allowing for things such as batch updates.

