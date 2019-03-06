# Review: Callback Functions

In Javascript, functions are first-class objects that behave in the same way as other objects in Javascript. This means that functions can be given as a parameter to another function. 

When a function is passed as an argument to another function, this is known as a callback.

**Example:**

```javascript

function dance() {
    console.log("I'm moving my body to the groove.");
}

function sing(song, dance) {
    console.log(`I'm singing along to ${song}.`);
    dance();
}

sing("Happy", dance);

//expected output
=> "I'm singing along to Happy."
=> "I'm moving my body to the groove."

```

# Array Iterators
Arrays have a number of methods that utilize callbacks to make them more flexible.

In this lesson, we'll be talking about: 
  ### .forEach, .map, .filter, .reduce, .find

For the following lesson please review [For Loops](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)!


## [.forEach()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

We already know that we can use a for loop could be used to loop through each value in an array like so:

```javascript

const arr = ['a', 'b', 'c', 'd', 'e']

for (let i=0; i < arr.length; i++) {
  console.log(arr[i])
}

//expected output
=> 'a'
=> 'b'
=> 'c'
=> 'd'
=> 'e'

```

Why write for loops over and over? they involve way too much writing, they're prone to syntactical errors. 

> ## In the words of GA Lead Instructor Jon Zachary: 

> >  _Terser Syntax => less typos => happier developers => world peace_

-----

Now we can call the forEach method on any array:

```javascript

const arr = ['a', 'b', 'c', 'd', 'e']

arr.forEach(function(element){
    console.log(element)
})

//expected output
=> 'a'
=> 'b'
=> 'c'
=> 'd'
=> 'e'
```

-----

Next, let's try this method with an anonymous arrow function. 

[For Review: 
ES6 Arrow Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

We can pass in three optional arguments for the .forEach method: 
* element value
* element index
* array being traversed.


```javascript

const arr = ['a', 'b', 'c', 'd', 'e']

arr.forEach((element, i, array) => {
    console.log(`this is ${element}, this is the index ${i}, this is the array being traversed: ${array}`)
})

//expected output
=> "this is a, this is the index 0, this is the array being traversed: a,b,c,d,e"
=> "this is b, this is the index 1, this is the array being traversed: a,b,c,d,e"
=> "this is c, this is the index 2, this is the array being traversed: a,b,c,d,e"
=> "this is d, this is the index 3, this is the array being traversed: a,b,c,d,e"
=> "this is e, this is the index 4, this is the array being traversed: a,b,c,d,e"

```

-----

## [.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

Use the `.map()` method on any array, it will return a new array with new mutated values. 

```javascript

let arr = [1, 2, 3, 4, 5]

const mapped = arr.map( d => d * 2 ); 

console.log(mapped)

//expected output:

=> [2, 4, 6, 8, 10]

```

## [.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

This method creates a new array with all the elements that pass the test implemented by the function... or it FILTERS everything you're not looking for. 

```javascript

let names = ["Carlos", "Dmitriy", "Angel", "Ester", "Alberto", "Magnardo"]

const filtered = names.filter( name => name.length > 5); 

console.log(filtered)

//expected output: 

["Carlos", "Dmitriy", "Alberto", "Magnardo"]

```
## [.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)
The `reduce()` method executes a reducer function (that you provide) on each memeber of the array against an accumulator and each element in the array (from left to right) to be *REDUCED* to a single value

```javascript
let arr = [1, 2, 3, 4, 5, 6, 7]; 
let reducer = (accumulator, value) => {
    return accumulator + value; 
}
let newArr = arr.reduce(reducer)

//expected output
=> 28
```


## [.find()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

Use the `.find()` method on any array and it returns the **value** of the **first element** in the arrat that satisfies the callback function, otherwise `undefined` is returned. Just like the .forEach() method, the callback function also can take three arguments. 

```javascript

const arr = [5, 6, 30, 35, 90, 130,  9]; 

let found = arr.find((d) => {
    return d > 30; 
});

console.log(found); 

//expected output
=> 35

```
