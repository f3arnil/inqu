### Q#1
```javascript

const duration = 0;
const animationTime = duration || 400; 

console.log(animationTime);
```

### Q#2
```javascript

console.log(
  [‘1’, ‘7’, ‘11’].map(parseInt)
);

```

### Q#3
```javascript

const a = {};
const b = { key: 'b' };
const c = { key: 'c' };

a[b] = 123;
a[c] = 456;

console.log(a[b]);
```

### Q#4
```javascript

function someFunction (a) {
  if (!a) return false;
  return true;
};

test('some string data')
test(0);
test({ a: '1' });
test();

```

### Q#5
#### Put `a` value to `b` variable, and `b` value to `a` without creating additional variable
```javascript
const a = 1;
const b = 2;

// ...some code...

```

### Q#6
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

### Q#7
```javascript
function Car(color) {
  this.color = color;
}

let lada = new Car("Black");
Car.prototype.currentGear = 1;

console.log(++lada.currentGear);
console.log(Car.prototype.currentGear);
```

### Q#8
```javascript
function calculate() {
  // some implementation...
}

calculate('+')(1)(2); // 3
calculate('*')(2)(3); // 6
```

### Q#9
```javascript
for (var i = 0; i < 5; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

### Q#10
```javascript
(() => {
  console.log(inner);
  inner();

  var inner = () => {
    console.log('inner');
  };
})();

(() => {
  console.log(inner);
  inner();

  function inner() {
    console.log('inner');
  }
})();
```

### Q#11
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

...

### Q#12
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



