### Q#1
```javascript
for (var i = 0; i < 5; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

### Q#2
```javascript
let person = {
  name: 'Sam',
  hello() {
    console.log(this.name);
  },
};

let hello = person.hello;
hello(); // Make it to output "Sam"
```

### Q#3
```javascript
function Car(color) {
  this.color = color;
}

let lada = new Car("Black");
Car.prototype.currentGear = 1;

console.log(++lada.currentGear);
console.log(Car.prototype.currentGear);
```

### Q#4
```javascript
function calculate() {
  // some implementation...
}

calculate('+')(1)(2); // 3
calculate('*')(2)(3); // 6
```

### Q#5
```javascript

const duration = 0;
const animationTime = duration || 400; 

console.log(animationTime);
```

### Q#6
```javascript
(() => {
  console.log(inner);
  inner();

  var inner = () => {
    console.log('inner');
  };
})();
```

### Q#7
```javascript
(() => {
  try {
    setTimeout(() => {
      throw new Error('Awesome error!');
    }, 0);
  } catch(e) {
    console.log('An error: ', e)
  }
})();
```

### Q#8
```javascript
(() => {
  console.log(1);
 
  setTimeout(() => console.log(2), 0);

  Promise.resolve(true)
    .then(() => console.log(3))
    .then(() => console.log(4));
 
  console.log(5);
})();
```

### Q#9
```javascript

function someFunction (a) {
  if (!a) {
    ...
    return false;
  }
  ...
  return true;
};

someFunction('some string data')
someFunction(0);
someFunction({ a: '1' });
someFunction();

```

### Q#10
```javascript

console.log(
  [‘1’, ‘7’, ‘11’].map(parseInt)
);

```

### Q#11
```javascript

const a = {};
const b = { key: 'b' };
const c = { key: 'c' };

a[b] = 123;
a[c] = 456;

console.log(a[b]);
```

### Q#12
#### Put `a` value to `b` variable, and `b` value to `a` without creating additional variable
```javascript
let a = 1;
let b = 2;

// ...some code...

```

### R1
```javascript

...
  return(
    <ul>
      {data.map(title => (<li>{title}</li>))}
    </ul>
...

Data set:

1.
  a) data = ['1', '2'];
  b) data = ['1', '2', '3'];

2.
  a) data = ['2', '3'];
  b) data = ['1', '2', '3'];

```

### R2
```javascript
...
render() {
  const { loaded, data = [] } = this.props;
  
  if (!loaded) return <Loader />;
  
  return (
    <div className="results">
      {data.map(
        itemId => (<Item id={itemId} />)
      )}
    </div>
  )
}
...

// Item component
...
const Item = ({ id, title, description, onClick }) => {
  const onItemClick = () => onClick(id);
  
  return (
    <div className="item" onClick={onItemClick}>
      <div className="title">{title}</div>
      <div className="description">{description}</div>
    </div>
  );
}

const ConnectedItem = connect(
  (state, props) => {
    const { id } = props;
    
    return {
      id,
      title: getTitle(state)(id),
      description: getDescription(state)(id),
    }
    ...
  },
  {
    ...
    onClick: handleItemClick,
    ...
  }
)(Item)

export default ConnectedItem;
...
```

### R3
```javascript
...
render() {
  const { a, b, c } = this.props;
  return (
    <MyComponent value1={a} value2={b} value3={c}>
      <Title /> // Should receive a,b,c (from this component props)
      <Description /> // Should receive a,b,c (from this component props)
      ({ v1, v2, v3 }) => <Content value1={v1} value2={v2} value3={v3}/>
    </MyComponent>
  )
}
...
```

### R4
```javascript

// url:
// https://mywebsite.com/search?searchTerm=search%20request&itemsPerPage=15&page=2

const MyComponent = ({
  searchTerm,
  requestData,
  loading,
  data,
  onSearch,
  trackOnItemClick,
 }) => {
  useEffect(
    () => requestData(searchTerm),
    []
  );
  
  const handleClick = (itemId) => {
    const item = data[itemId];
    
    trackOnItemClick(item);
  }
  
  const handleSearchClick = searchterm => {
    // onSearch callback will change url searchTerm query param only via history.push
    onSearch(searchterm); 
  };
  
  if (loading) return (<Loader />);
  
  return (
    <>
      <SomeSearchPanelComponent searchTerm={searchTerm} onSearch={handleSearchClick} />
      <SomeListComponent list={data} onItemClick={handleClick} />
    </>
   );
}

export default MyComponent;

```


### Big O - 1
```javascript
const foo = array => {
  let totalItems = 0;
  let totalPrice = 0;
  
  for (let i = 0; i< array.length; i++) {
    if (array[i].active) totalItems += 1;
  }
  
  ...
  
  for (let index = 0; index < array.length; index++) {
    if (array[i].active) totalPrice += array[i].price;
  }
  ...
}
```

### Big O - 2
```javascript
const foo = array => {
  let totalItems = 0;
  let totalPrice = 0;
  
  for (let i = 0; i< array.length; i++) {
    if (array[i].active) totalItems += 1;
    ...
    for (let index = 0; index < array.length; index++) {
      if (array[i].active) totalPrice += array[i].price;
    }
    ...
  }
  ...
}
```

### Big O - 3
```javascript
const foo = (a = [], b =[]) => {
  let totalItems = 0;
  let totalPrice = 0;
  
  for (let i = 0; i< a.length; i++) {
    if (a[i].active) totalItems += 1;
    ...
    for (let index = 0; index < b.length; index++) {
      if (b[i].active) totalPrice += array[i].price;
    }
    ...
  }
  ...
}
```
