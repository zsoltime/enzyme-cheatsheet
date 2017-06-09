# Enzyme Cheatsheet

A cheatsheet containing Enzyme code snippets.

Contributions are welcome!

## Finding Elements

You can use `find` in place of [ReactTestUtils](https://facebook.github.io/react/docs/test-utils.html)' `scryRenderedDOMComponentsWithTag`, `scryRenderedDOMComponentsWithClass` and `scryRenderedComponentsWithType`.

**Find element(s) using CSS selectors:**

```javascript
const wrapper = shallow(<MyComponent />);

wrapper.find('.by-classname');
wrapper.find('#by-id');
wrapper.find('div');
wrapper.find('[htmlFor="input"]');
```

**Find element(s) by constructor or display name:**

```javascript
const wrapper = shallow(<MyComponent />);

wrapper.find(Button);
wrapper.find('Button');
```

**Find element with object properties:**

```javascript
const wrapper = shallow(<MyComponent />);
const img = wrapper.find({src: '/image.png'});

expect(img.length).toBe(1);
```

**Find the first/last element:**

```javascript
const wrapper = shallow(<MyComponent />);
const firstElement = wrapper.find(Element).first();
const lastElement = wrapper.find(Element).last();

expect(firstElement.text()).toBe('First Element');
expect(lastElement.text()).toBe('Last Element');
```

**Find the nth element:**

```javascript
const wrapper = shallow(<MyComponent />);
const thirdElement = wrapper.find(Element).at(2); // zero-based index

expect(thirdElement.text()).toBe('Third Element');
```

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

**Check if element has className:**

```javascript
const wrapper = shallow(<MyComponent />);
const button = wrapper.find(Button).first();

expect(button.hasClass('btn')).toBe(true);
```

**Setting input field to test form submit:**

```javascript
wrapper.find('#my-input').node.value = 'abc';
form.simulate('submit');

expect(spy).toHaveBeenCalledWith('abc');
```
