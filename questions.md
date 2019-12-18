### Q#1
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

### Q#2
```javascript
function calculate() {
  // some implementation...
}

calculate('+')(1)(2); // 3
calculate('*')(2)(3); // 6
```

### Q#3
```javascript
for (var i = 0; i < 5; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

### Q#4
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

...

### Q#5
```javascript
function Car(color) {
  this.color = color;
}

let lada = new Car("Black");
Car.prototype.currentGear = 1;

console.log(++lada.currentGear);
console.log(Car.prototype.currentGear);
```

### Q#6
```javascript
let User = function() {};

User.prototype.attributes = {
  isAdmin: false,
};

let admin = new User('Sam');
let guest = new User('Bob');

admin.attributes.isAdmin = true;

console.log(admin.attributes.isAdmin);
console.log(guest.attributes.isAdmin);
```

### Q#7
```javascript
let a = {};

(function b ( a ) {
    a.a = 10;
    a = null;
})( a );

console.log(a);
```

### Q#8
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

### Q#9
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
