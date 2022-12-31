# Difference between null and undefined?

When null is assigned to a variable .

    var name = null

    console.log(typeof(name)) ------logs object on console

When a variable is declared but not assigned any value.

    var age

    console.log(age) ------logs undefined on console

    console.log(typeof(age)) ------logs undefined on console

---

# Precedence of Operators:

- U = UNARY (x+,x-,x\*,x/,pre/post increment/decrement)
- A = ARITHMETIC
- R = RELATIONAL (>,<,>=,<=,==,!=)
- B = BITWISE
- L = LOGICAL
- N = NULLISH COALESCING (??)
- T = TERNARY ( a ? true : false)
- A = ASSIGNMENT

---

# Falsy value in javascript:

- 0
- ""
- undefined
- null
- NaN
- false

---

# Functions (DRY)

### Definition:

```
function function_name (parameters) {
code here
}
```

- Function parameters: the values defined in the function definition parentheses

- Function arguments: the values passed in the function call

### Function Expression:

- A function assignined into a variable is called function expression.
- Functions stop executing when they encounter the `return` keyword.
- Functions often compute a value and return back the value to the caller.

```
function add(a,b){
    return a+b;
}

var sum = add(10,20)

```

### Anonymous Function:

A function that has no name and is represented as a function expression.

```
var add = function (a,b) {
    return a+b;
}

```

---

# ECMAScript 2015 (ES6) Part 1

### var vs let vs const

- var is functional scope but let & const are block scope

  ```
  function displayName(){
      var first = "Divyansh"

      if(first){
          let mid = "Kumar"
          const last = "Mishra"
          console.log("My name is:" + first + ' ' + mid +  ' '+ last)   //logs My name is Divyansh Kumar Mishra
      }
      console.log("My name is:" + first + ' ' + mid +  ' '+ last)   //throws error because let and const are not accessible outside if scope
  }

  displayName()
  ```

- var and let can be reassigned but const can't be reassigned

  ```
  var a = 3;
  let b = 6;
  const c = 9;

  a = 4;    //works
  b = 8;    //works
  c = 12;   //throws error because const variables cannot be reassigned

  ```

### Template Literals

```
var first = "Divyansh"
let mid = "Kumar"
const last = "Mishra"

console.log(`My name is: ${first} ${mid} ${last}`)
```

### Default Parameters

Default parameters allow named parameters to be initialized with default values when no or less number of argumnets are passed during function call.

```
function add(a=5,b=6){
    return a+b;
}

console.log(add());
console.log(add(7));

```

### Fat Arrow functions vs Normal functions

- function keyword is not used in arrow function definition.

* Arrow functions can't be called before initialization.

  ```
  console.log(sum()); //throws error

  const add = (a=5,b=6) => {
      return a+b;
  }
  ```

- No need to write rerurn keyword if there is only one statement in the the function scope;

  ```
  const sum = () => `the sum of the two number is ${(a=5)+(b=6)}`;

  console.log(sum());
  ```

- Arrow functions don't have arguments binding but we can use rest operator.

  ```
  Normal functions:

  add(2,3);

  function add(a,b){
      console.log(arguments);
  }

  Arrow function:

  const add = (a,b) => console.log(arguments)
  add(2,3);   //throws error

  const add = (...args) => console.log(...args)
  add(2,3);
  ```

# ARRAYS

- In Javascript arrays are a collection of various datatypes unlike other programming languages.
- In javascript Array is a class of which arrays are a prototype.

  ```
  const names = ['Divyansh', 'Kumar', 'Mishra']
  ```

### Traversal

- #### for-in

  for-in loop gives the index number of each element in the array.

  ```
  for(let element in names)
      console.log(element)
  ```

  //to print the element use:

  ```
  for(let element in names)
      console.log(names[element])
  ```

- #### for-of

  for-of loop gives the elements in the array.

  ```
  for(let element of names)
      console.log(element)
  ```

* #### forEach()

  forEach loop is used to perform the same operation on all the array elements.
  forEach loop gives us element, index and the array itself.

  syntax:

  ```
  array.forEach(function(value,index,arrayName)=>{
        //operation
  })
  ```

  ```
  names.forEach(function(element,index,names)=> {
      element = '$' + element
      console.log(element)
  })
  ```

### Searching

- #### indexOf() :

  makes a forward search and return the first(least) index of element that matches the search parameter. Returns -1 if no elements matches the search parameter.

  ```
  array.indexOf(searchElement, startIndex, endIndex)
  ```

* #### lastIndexOf():

  makes a backward search and return the last(greatest) index of element that matches the search parameter. Returns -1 if no elements matches the search parameter.

  ```
  array.lastIndexOf(searchElement, startIndex, endIndex)
  ```

* #### find():

  will find the first element that matches the specified condition and returns that element. Returns undefined if no elements are found. This method executes a function for each element.

  ```
  console.log(array.find((element,index,array)=> {return element === 'Divyansh'}))
  ```

* #### findIndex():

  will find the first element that matches the specified condition and returns the index of that element. Returns -1 if no elements are pass the test. This method executes a function for each element.

  ```
  console.log(array.findIndex((element,index,array)=> {return element === 'Divyansh'}))
  ```

* #### includes():

  returns true if the array contains a specified value else returns false. It implements case sensitive search.

  ```
  console.log(array.includes(searchElement, startIndex)
  ```

### Filtering

- #### every();

  returns true if all the elements of an array pass the test. Returns false if even a single element fails the test. Executes a function for each element.

  ```
  const ages = [{name: 'Divyansh', age: 18},{name: 'Shalini', age: 18}, {name: 'Sakshi', age: 16}]

  const isAdult = (element,index,array) => {
    return element.age == 18
  }

  const result1  = ages.every(isAdult)  //  false

  const isTeenager = (element,index,array) => {
    return element.age >= 16
  }

  const result2  = ages.every(isTeenager) //  true
  ```

- #### some();

  returns true if even one of the elements of an array pass the test. Executes a function for each element.

  ```
  const ages = [{name: 'Divyansh', age: 18},{name: 'Shalini', age: 18}, {name: 'Sakshi', age: 16}]

  const isAdult = (element,index,array) => {
    return element.age == 18
  }

  const result  = ages.some(isAdult)  //  true
  ```

### Sorting

- #### sort();

  ```

  ```

### CRUD operations

- #### push():

  inserts a new element at the end of the array and returns the new lenght of the array.

- #### pop():

  removes an element from the end of the array and returns the new lenght of the array.

- #### unshift():

  inserts a new element at the beginning of the array and returns the new lenght of the array.

- #### shift():

  removes an element from the beginning of the array, shifts all succeeding elements and returns the new lenght of the array.

* #### concat();

  concats two or more arrays and returns the new array. This method does not change the original array.

* #### splice();

  adds/removes one or more elements from a particular position in the array. This methods chnages the original array.

  ```
  p = position
  n = no. of elements to remove

  array.splice(p, n, elements)

  const fruits = ["Banana", "Orange", "Apple", "Mango"];

  fruits.splice(2,0,'grapes','litchi')  // adds grapes and litchi at position 2
  fruits.splice(2,2)  // removes apple and mango from position 2
  ```

* #### slice();

  returns a part of the original array. It does not include the end index. This method does not change the original array.

  ```
  array.slice(startIndex, endIndex)

  const fruits = ["Banana", "Orange", "Apple", "Mango"];

  fruits.slice(1,3) //  ["Orange", "Apple"]
  ```

* #### join();

  returns an array as a string. The string can be separated by any separator. This method does not change the original array.

  ```
  const fruits = ["Banana", "Orange", "Apple", "Mango"];

  fruits.join(' and ')  // Banana and Orange and Apple and Mango
  ```

* #### toString();

  returns an array as a string. The string can be separated by commas. This method does not change the original array.

  ```
  const fruits = ["Banana", "Orange", "Apple", "Mango"];

  fruits.toString() // Banana,Orange,Apple,Mango
  ```

### Important methods

- #### map():

  the map function returns a new array containing a result of executing a function against each of the elements in the array.

  ```
  const nums = [1,2,3,4]
  const thrice = nums.map((ele, index, array)=> {
    return ele * 3;
  })
  console.log(thrice)
  ```

- #### filter():

  the filter function returns a new array containing all the elements that pass a certain condition.

  ```
  const nums = [16,10,3,40,56,4]
  const aboveTen = nums.filter((ele, index, array) => {
    return ele > 10;
  })
  console.log(aboveTen)
  ```

- #### reduce():

  the reduce function returns a single value by running a reducer function against all the array elements.
  reduce() takes a callback and an initial value as it's parameters. If the initial value is not provided then it takes the first array element as initial value.

  ```
  const nums = [16,10,3,40,56,4]
  const sum = nums.reduce((accumulator,curVal,index,array) => {
    return accumulator + curVal;
  },initialVal)
  console.log(sum)
  ```

  ##### flatten a 2d array

  ```
  const nums = [[1,2,3],[4,5,6],[7,8,9]]
  const flattened = nums.reduce((acc,cur) => acc.concat(cur))
  console.log(flattened)  //  [1,2,3,4,5,6,7,8,9]
  ```

- #### map() vs forEach():

  - map() returns a new array while forEach() returns undefined.
  - map() is chainable with functions like reduce(),filter() etc. while forEach() is not chainable as it return undefined.

# Strings

- A string is a sequence of characters.
- A string is zero or more number of characters writeen inside single/double quotes or template literals.

### String declaration

- Using string literals:

  ```
  let firstName = 'Divyansh'
  ```

- Using String constructor:

  ```
  let lastName = new String('Mishra')
  ```

### String important methods

- #### Extracting parts of string

  - ##### slice()

    - slice() method extracts a part of the string in a new string. It does not mutate the original string.
    - It takes two parameters: startIndex, endIndex
    - It can take negative indexes.

    ```
    let name = 'Divyansh Mishra';
    let firstName = name.slice(0,9)
    console.log(firstName)  //  Divyansh

    let lastName = name.slice(-6)
    console.log(lastName)  //  Mishra
    ```

  - ##### substring()

    - substring() method extracts a part of the string in a new string. It does not mutate the original string.
    - It takes two parameters: startIndex, endIndex
    - It doesn't take negative indexes

    * If we give negative indexes then the values start from 0th position

    ```
    let name = 'Divyansh Mishra';
    let firstName = name.substring(0,9)
    console.log(firstName)  //  Divyansh
    ```

  - ##### substr()

    - substr() method also extracts a part of the string in a new string. It does not mutate the original string.
    - It takes two parameters: startIndex, length of the extracted string

    * It takes negative indexes

    ```
    let name = 'Divyansh Mishra';
    let firstName = name.substr(0,8)
    console.log(firstName)  //  Divyansh

    console.log(name.substr(-6))  //  Mishra
    ```

  * ##### charAt()

  - The charAt() extracts the character present at the specified position.

    ```
    const name = 'Divyansh mishra'
    console.log(name.charAt(7)
    ```

  - ##### charCodeAt()

    - The charCodeAt() extracts the UNICODE of the character present at the specified position.

    ```
    const name = 'Divyansh mishra'
    console.log(name.charCodeAt(7)
    ```

* #### Replacing parts of string

  ##### replace()

  - The replace() method replaces the intended text with the new text and returns a new string. It does not mutate the original string.

  - It replaces the first match.

  * It is case-sensitive

  ```
  const name = 'The name is mishra , Divyansh mishra'
  console.log(name.replace('mishra', 'Mishra')); // The name is Mishra , Divyansh mishra
  ```

* #### Important String Methods

  - ##### concat()

    concat() method concatsenates two or more strings and returns a new string. It does not mutate the original string.

    ```
    const fName = 'Divyansh'
    const lName = 'Mishra'
    console.log(fName.concat(lName)); //  Divyansh Mishra
    ```

  - ##### trim()

    trim() method removes all the trailing and leading spaces in the string. It returns a new string. It does not mutate the original string.

    ```
    const fName = '   Divyansh     '
    const lName = 'Mishra     '
    console.log(fName.trim().concat(" ",lName.trim())); //  Divyansh Mishra
    ```

  - ##### split()

    split() method converts a string into an array of strings when it finds a separator. It returns a new string. It does not mutate the original string.

    ```
    const name = "Divyansh Kumar Mishra"
    console.log(name.split(' ')); //  ['Divyansh', 'Kumar', 'Mishra']
    ```

# Date and Time

- Date objects returns number of milliseconds since `1 January 1970`.

* Date objects represent a single moment in time in a platform-independent format.

  ### Date Object Creation

  - #### let date = new Date()

    ```
    let date = new Date()
    console.log(date) //  Sat Dec 17 2022 10:04:18 GMT+0530 (India Standard Time)
    console.log(date.toString()) //  Sat Dec 17 2022 10:04:18 GMT+0530 (India Standard Time)
    console.log(date.toLocaleString()) // 17/12/2022, 10:04:18
    console.log(Date.now()) //  1671251886293  -> returns number of milliseconds since 1 January 1970
    ```

  - #### let date = new Date(year, month, day, hour, minute, second, millisecond)

    - Here months range between 0 and 11 , January is 0 and December is 11.
    - Here hours range between 0 and 23.
    - Atleast provide year and month, otherwise it'll show data from January 1970.

    ```
    let date = new Date(2022, 11, 17, 10, 15, 36, 24)
    console.log(date.toLocaleString()) // 17/12/2022, 10:15:36

    let date = new Date(2022, 11)
    console.log(date.toLocaleString()) // 01/12/2022, 00:00:00
    ```

  - #### let date = new Date(dateString)

    ```
    let date = new Date('December 17, 2022 10:27:28')
    console.log(date.toLocaleString()) // 17/12/2022, 10:27:28
    ```

  - #### let date = new Date(milliseconds)

    ```
    let date = new Date(1671253388734)
    console.log(date.toLocaleString()) // 17/12/2022, 10:33:08
    ```

  ### Date and Time methods

  ```
  let curDate = new Date();
  const year = curDate.getFullYear()
  const month = curDate.getMonth() + 1
  const day = curDate.getDate()
  const hour = curDate.getHours()
  const minute = curDate.getMinutes()
  const second = curDate.getSeconds();

  console.log(`The current data and time is: ${day}/${month}/${year} ${hour}:${minute}:${second}`)
  // The current data and time is: 17/12/2022 10:47:0
  ```

# Math Object methods

```
console.log(Math.PI)  //  3.141592653589793

console.log(Math.pow(2,5) //  32

console.log(Math.sqrt(289)) // 17

console.log(Math.round(33.333)) //  33 rounds the number to nearest integer

console.log(Math.abs(-2369)) // 2369 return the absolute(positive) value of number

console.log(Math.ceil(33.33))  // 34 rounds the number to nearest biggest integer

console.log(Math.floor(33.33))  // 33 rounds the number to nearest smallest integer

console.log(Math.min(23, -6, 1999, 0, 97)) //  -6 return the minimum value among the list og arguments

console.log(Math.max(23, -6, 1999, 0, 97)) //  1999 return the maximum value among the list og arguments

Math.random() // returns a random between 0(included) and 1(excluded)
console.log(Math.round(Math.random()*10)) // return a random number between 0 and 1

console.log(Math.trunc(77.9867)) //  77 returns the integer part of the number
```

# ECMAScript 2015 (ES6) Part 2

### Object literals

- Object literal is `key : value` pair like data structure.

* We can store different types of data including functions in an object.

#### Object creation

- First way

  ```
  const myData = {
    fName: 'Divyansh',
    lName: 'Mishra',
    age: 23,
    getData: () => {
      console.log(`My name is ${myData.fName} ${myData.lName} and I'm ${myData.age} years old`);
    }
  }
  myData.getData()  //  My name is Divyansh Mishra and I'm 23 years old
  ```

- Second way : we can avoid using semicolon for function reference, writing function keyword or making fat arrow functions

  ```
  const myData = {
    fName: 'Divyansh',
    lName: 'Mishra',
    age: 23,
    getData (){
      console.log(`My name is ${myData.fName} ${myData.lName} and I'm ${myData.age} years old`);
    }
  }
  myData.getData()  //  My name is Divyansh Mishra and I'm 23 years old
  ```

- Third way : object inside object

  ```
  const myData = {
    fullName: {
        fName: 'Divyansh',
        lName: 'Mishra',
    },
    age: 23,
    getData (){
      console.log(`My name is ${myData.fullName.fName} ${myData.fullName.lName} and I'm ${myData.age} years old`);
    }
  }
  myData.getData()  //  My name is Divyansh Mishra and I'm 23 years old
  ```

#### this object

- `this` object contains the current context
- it's value varies depending on where it is placed

##### global window object(chrome developer tools)

```
console.log(this)  //   Window {window: Window, self: Window, document: document, name: '', location: Location, …}

this.alert(`I'm window object`)
```

##### Inside global function(global window object)

```
function myName() {
  console.log(this)  //   Window {window: Window, self: Window, document: document, name: '', location: Location, …}
}

myName()

let myName = 'Divyansh'

function showName() {
  console.log(this.myName)  // Divyansh
}

showName()
```

##### Inside a method in an object literal

```
  const myData = {
    fName: 'Divyansh',
    lName: 'Mishra',
    age: 23,
    getData() {
      console.log(this)
      console.log(`My name is ${this.fName} ${this.lName} and I'm ${this.age} years old`);
    }
  }
  myData.getData()

  //  {fName: 'Divyansh', lName: 'Mishra', age: 23, getData: ƒ}
  //  My name is Divyansh Mishra and I'm 23 years old
```

##### this object doesn't work with fat arrow function

```
const myData = {
    fName: 'Divyansh',
    lName: 'Mishra',
    age: 23,
    getData: () => {
      console.log(this)
      console.log(`My name is ${this.fName} ${this.lName} and I'm ${this.age} years old`);
    }
  }
  myData.getData()

  //  Window {window: Window, self: Window, document: document, name: '', location: Location, …}
  //  My name is undefined undefined and I'm undefined years old
```

### Destructuring

#### Array Destructuring

```
const myData = ['Divyansh', 'Mishra', 23];
const [fName, lName, age] = myData

console.log(`My name is ${fName} ${lName} and I'm ${age} years old`);
//  My name is Divyansh Mishra and I'm 23 years old

const [fName, lName, age] = ['Divyansh', 'Mishra', 23]

console.log(`My name is ${fName} ${lName} and I'm ${age} years old`)
//  My name is Divyansh Mishra and I'm 23 years old
```

#### Object Destructuring

```
const myData = {
    fName: 'Divyansh',
    lName: 'Mishra',
    age: 23,
}
const {fName, lName, age} = myData

console.log(`My name is ${fName} ${lName} and I'm ${age} years old`);
//  My name is Divyansh Mishra and I'm 23 years old

const {fName, lName, age} = {
    fName: 'Divyansh',
    lName: 'Mishra',
    age: 23,
}

console.log(`My name is ${fName} ${lName} and I'm ${age} years old`)
//  My name is Divyansh Mishra and I'm 23 years old
```

#### Add values through destructuring

- Add values in array.

  ```
  const myData = ['Divyansh', 'Mishra', 23];
  const [fName, lName, age, gender='Male'] = myData

  console.log(`My name is ${fName} ${lName} and I'm a ${age} years old ${gender}`)
  //  My name is Divyansh Mishra and I'm a 23 years old Male
  ```

- Add values in object.

  ```
  const myData = {
      fName: 'Divyansh',
      lName: 'Mishra',
      age: 23,
  }
  const {fName, lName, age, gender='Male'} = myData

  console.log(`My name is ${fName} ${lName} and I'm a ${age} years old ${gender}`)
  //  My name is Divyansh Mishra and I'm a 23 years old Male
  ```

### Object properties

- #### Dynamic properties

  ```
  const fruit = 'Banana'
  const vegie = 'Potato'

  const eatables = {
    [fruit] : 'Hi I am a fruit',
    [vegie] : 'Hi I am a vegetable',
  }

  console.log(eatables) //   {Banana: 'Hi I am a fruit', Potato: 'Hi I am a vegetable'}
  ```

- #### Need not write key : value pair if both key and value are same

  ```
  const fName = 'Divyansh'
  const lName = 'Mishra'

  const fullName = {
    fName: fName,
    lName: lName
  }
  console.log(fullName)


  //  Simply write this

  const fullName = {
    fName,
    lName
  }
  console.log(fullName)
  ```

### Spread Operator & Rest parameter

- #### Spread Operator

  The spread operator helps us expand an iterable such as an array where multiple arguments are needed, it also helps to expand the object expressions.

  ```
  function myBio(firstName, middlename, lastName) {
    console.log(`My name is ${firstName} ${middlename} ${lastName}`);
  }

  // Use spread to expand an array’s items into individual arguments:
  myBio(...["Divyansh", "Kumar", "Mishra"]);  //  My name is Divyansh Kumar Mishra
  ```

- #### Rest parameter

  The rest parameter is converse to the spread operator. while spread operator expands elements of an iterable, rest operator compresses them. It collects several elements. In functions when we require to pass arguments but were not sure how many we have to pass, the rest parameter makes it easier.

  ```
  function myBio(firstName, lastName, ...otherInfo) {
    console.log(`My name is ${firstName} ${lastName}, a ${otherInfo[2]} years old ${otherInfo[1]} working in ${otherInfo[0]}`);
  }

  // Use rest parameter to compress an array’s items :
  myBio("Divyansh","Mishra", "WebileApps", "Male", "23");
  //  My name is Divyansh Mishra, a 23 years old Male working in WebileApps
  ```

* #### Adding values using spread operator

  ```
  const colors1 = ['Violet','Indigo','blue']
  const colors2 = ['green','yellow','orange','red']

  const rainbow = [...colors1, ...colors2]
  console.log(rainbow)  // ['Violet', 'Indigo', 'blue', 'green', 'yellow', 'orange', 'red']

  ```

# ECMAScript 2017 (ES8)

- ### String Padding

  - #### padStart()

    This method ends a specified number of spaces at the beginning of the string. This method creates a new string and doesn't mutate the original string.

    `targetLength = number of spaces`

    `padStart(targetLength, padString)`

    ```
    const name = 'Divyansh'
    console.log(name.padStart(10,'$')) // $$Divyansh
    ```

  - #### padEnd()

    This method ends a specified number of spaces at the end of the string. This method creates a new string and doesn't mutate the original string.

    `targetLength = number of spaces`

    `padEnd(targetLength, padString)`

    ```
    const name = 'Divyansh'
    console.log(name.padEnd(10,'$'))  //  Divyansh$$
    ```

  ### Object.values()

  This method returns an array of values from all the `key:value` pairs in the object.

  ```
  const intro = {name: 'Divyansh Mishra', company: 'WebileApps', qualifications: 'MCA'}
  console.log(Object.values(intro))   //  ['Divyansh Mishra', 'WebileApps', 'MCA']
  ```

  ### Object.entries()

  An array of the given object's own enumerable string-keyed property key-value pairs. Each key-value pair is an array with two elements: the first element is the property key (which is always a string), and the second element is the property value.

  ```
  const intro = {name: 'Divyansh Mishra', company: 'WebileApps', qualifications: 'MCA', age:23}

  console.log(Object.entries(intro))

  //  [['name', 'Divyansh Mishra'],['company', 'WebileApps'],['qualifications', 'MCA'],['age', 23]]
  ```

# ECMAScript 2018 (ES9)

### Rest/Spread Properties

```
const intro = {name: 'Divyansh Mishra', company: 'WebileApps', qualifications: 'MCA'}

const {name, ...otherInfo} = intro
console.log(name)   //  Divyansh Mishra
console.log(otherInfo)  //  {company: 'WebileApps', qualifications: 'MCA'}

function showData(...otherInfo){
  console.log(otherInfo)  //  {name: 'Divyansh Mishra', company: 'WebileApps', qualifications: 'MCA'}
}

showData({name: 'Divyansh Mishra', company: 'WebileApps', qualifications: 'MCA'})
```

### Note: Only iterable objects like array can be expanded using the `Spread operator` not the plain objects that lack the `Symbol.iterator` method

# ECMAScript 2019 (ES10)

### 1. Array.flat() method

- The flat() method converts the multidimensional arrays into a single-dimensional array.
- By default this method flattens one level of nesting into a single-dimensional array.
- We can provide the level of flattening as an argument. If we provide `Infinity` as the argument then it will flatten all the levels of nesting into a single-dimensional array.

  #### Using reduce() : Can only flatten upto one level

  ```
  const array = [1,2,3,4,5,6,[7,8,9,[10,11,12]]]
  const flattened = array.reduce((acc, cur) => acc.concat(cur),[])
  console.log(flattened)  //  [1, 2, 3, 4, 5, 6, 7, 8, 9, [10,11,12]]
  ```

  #### Using flat()

  ```
  const array = [1,2,3,4,5,6,[7,8,9,[10,11,12,[14,15,16,[17,18,19]]]]]
  const flattened = array.flat(Infinity)
  console.log(flattened)  //  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 14, 15, 16, 17, 18, 19]
  ```

### 2. Object.fromEntries()

The Object.fromEntries() method transforms a list of key-value pairs into an object.

```
const intro = [['name', 'Divyansh Mishra'],['company', 'WebileApps'],['qualifications', 'MCA'],['age', 23]]
console.log(Object.fromEntries(intro))
//  {name: 'Divyansh Mishra', company: 'WebileApps', qualifications: 'MCA', age: 23}
```

### 3. trimStart() & trimEnd()

```
const name = '     Divyansh Mishra     '
console.log(name.trimStart())   //  'Divyansh Mishra     '
console.log(name.trimEnd())     //  '     Divyansh Mishra'
```

# ECMAScript 2020

- ### BIGINT

  - Javascript has a maximum number on which safely any of the operations can be performed but beyond that number operation might produce unexpected results.

  - A bigint number is succeeded by letter `n`

  ```
  console.log(Number.MAX_SAFE_INTEGER)  //  9007199254740991
  console.log(9007199254740991 + 327)   //  9007199254741364  which is errorneous
  ```

  To perform operations beyond this number we `BIGINT` was introduced in JavaScript.

  `console.log(9007199254740991n + 200n)  //  9007199254741191n`

- ### Nullish Coalesce (??) vs Logical OR (||) vs Logical AND (&&)

  - #### Nullish Coalesce (??)

    Nullish coalesce operator returns right-hand side of the operator if the left-hand side is null or undefined.

    ```
    console.log(null ?? 24)   //  24
    ```

  - #### Logical OR

    Logical OR operator returns right-hand side of the operator if the left-hand side is a falsy value.
    Logical OR operator returns the first `truthy value` it finds.

    ```
    console.log(null || undefined || '' || false || NaN || 24)   //  24
    ```

  - #### Logical AND

    Logical AND operator returns right-hand side of the operator if the left-hand side is a truthy value.
    Logical AND operator returns the first `falsy value` it finds.

    ```
    console.log(null && undefined && '' && false && NaN && 24)   //  null
    ```

# Advance Javascript

## Event Propagation

- ### Event Bubbling

  When an event is captured by the innermost element and is propagated to the outermost element then this phenomenon is called event bubbling.

- ### Event Capturing

  When an event is captured by the outermost element and is propagated to the innermost element then this phenomenon is called event capturing.

  ### NOTE: By default the events are in bubbling phase.

## Higher Order Functions & Callback Functions

- A function which accepts other functions as an argument is called a `higher order function`.

- A function which is passed as an argument inside a higher order function is known as a `callback function`.

```
const add = (a,b) => {
  console.log(`The result is ${a+b}`);
}

const subtract = (a,b) => {
  console.log(`The result is ${Math.abs(a-b)}`);
}

const multiply = (a,b) => {
  console.log(`The result is ${a*b}`);
}

const divide = (a,b) => {
  console.log(`The result is ${a/b}`);
}

const calculator = (num1, num2, operation) => {
  operation(num1,num2);
}

calculator(73,27,add);  //  The result is 100
calculator(73,27,subtract);  //  The result is 46
calculator(25,25,multiply);  //  The result is 625
calculator(100,4,divide);  //  The result is 25
```

## Asynchronous Javascript

### Hoisting

Hoisting is a mechanism in Javascript where variables and function declarations are moved to the top of thier scope.

```
console.log(myName);  //   undefined
var myName;
myName = 'Divyansh'
```

- Explanation

  ```
  1. var myName = undefined   // variable myName is moved to the top of it's scope and is assigned undefined
  2. console.log(myName); // displays undefined
  3. myName = 'Divyansh'
  ```

##### NOTE: Since ES6 hoisting is avoided by using `let` and `const` keywords which are limited to their scope.

### Scope Chain & Lexical Scope

#### Scope Chain

- The scope chain is used to resolve the values of variables in Javascript.
- When a variable is used in JavaScript, the JavaScript engine will try to find the variable’s value in the current scope. If it could not find the variable, it will look into the outer scope and will continue to do so until it finds the variable or reaches global scope.
- If it still could not find the variable, it will either implicitly declare the variable in the global scope (if not in strict mode) or return an error.

  ```
  let foo = 'foo';
  function bar() {
    let baz = 'baz';
    console.log(baz);   //  baz
    console.log(foo);   //  foo
    number = 42;
    console.log(number);    //   42
  }
  bar();
  ```

- ##### Explanation

  When the function bar() is executed, the JavaScript engine looks for the baz variable and finds it in the current scope. Next, it looks for foo variable in the current scope and it can’t find it there, so it looks for the variable in outer scope and finds it there (i.e global scope).

  After that, we assign 42 to the number variable, so the JavaScript engine looks for the number variable in the current scope and after that in the outer scope.

  If the script is not in strict mode, the engine will create a new variable named number and assign 42 to it or return an error (if not in strict mode).

  So when a variable is used the engine will traverse the scope chain until it finds the variable.

#### Lexical Scoping
