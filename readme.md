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

## Testing Props

**Get prop value:**

```javascript
const wrapper = shallow(<MyComponent foo={10} />);

expect(wrapper.prop('foo')).to.equal(10);
// or
expect(wrapper.props().foo).to.equal(10);
```

## Testing Component Methods

```javascript
const wrapper = shallow(<ButtonComponent />);

wrapper.instance().handleClick();
```

**Get the nth element:**

```javascript
const wrapper = shallow(<MyComponent />);
const element = wrapper.find(Element);

expect(element.at(3).text()).toBe('My Text');
```

**Check if element has className:**

```javascript
const wrapper = shallow(<MyComponent />);
const button = wrapper.find(Button).first();

expect(button.hasClass('btn')).toBe(true);
```

**Find element with object properties:**

```javascript
const wrapper = shallow(<MyComponent />);
const img = wrapper.find({src: '/image.png'});

expect(img.length).toBe(1);
```

**Setting input field to test form submit:**

```javascript
wrapper.find('#my-input').node.value = 'abc';
form.simulate('submit');

expect(spy).toHaveBeenCalledWith('abc');
```
