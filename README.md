React Battleship!
===================

Simple implementation of Battleship in React/ES6.  Uses [react-users-and-roles] as a boilerplate.

Usage:

```
npm install
npm start
```

For now, ships are placed using the arrays in `index.js` and have the following constraints:

 * Ships are always placed vertically
 * Ships are 3 spaces long

The following indicates that player 0 will have 3 ships, placed at `(0,0)`, `(1,1)`, and `(2,3)` and player 1 will have 3 ships, placed at `(0,0)`, `(1,1)`, and `(1,2)`.  If this isn't clear, take a look at the screenshot below.

    const ships = [[ 0, 1, -1, 2, -1 ],
                   [ 0, 1, 1, -1, -1 ]];



### Important details (things I learned while doing this):

React's [immutability helpers] aren't terrible, but Immutable.js is the better way to go for larger projects.  To update a (computed, non-constant) index in an array, use ES6 [computed property names]:

	update(board, { [row]: { [col]: { $set: types.MISS}}});

To toggle visibility between two React components, I rendered both onto the page and set the `display` property of each to be mutually exclusive of the other.  In this case, the performance gain was negligible, but this might be a useful pattern in the future.

`Object.freeze()` can be used to create frozen enumerables in JS.

Pushing state upwards in the component hierarchy is not just good design, it's sometimes necessary.  One of the implementation hurdles I encountered was trying to set a component's state *and* invoke a callback on the parent, both of which trigger a re-render.  For the time being, I'll consider that an anti-pattern.

### Screenshot

![Screenshot](http://mynnx.github.io/react-battleship/screenshot.png)

[react-users-and-roles]: https://github.com/mynnx/react-users-and-roles
[immutability helpers]: https://facebook.github.io/react/docs/update.html
[computed property names]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Computed_property_names
