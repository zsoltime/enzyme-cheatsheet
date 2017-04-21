# Enzyme Cheatsheet

A cheatsheet containing Enzyme code snippets.

Contributions are welcome!

## Testing State

**Get component state:**

```javascript
const wrapper = shallow(<MyComponent />);
expect(wrapper.state().foo).toBe(bar);
// or
expect(wrapper.state('foo').toBe(bar);
```
**Set component state:**

```javascript
const wrapper = shallow(<MyComponent />);

wrapper.setState({ name: 'bar' });
```

## Testing Component Methods

```javascript
const wrapper = shallow(<ButtonComponent />);

wrapper.instance().handleClick();
```

