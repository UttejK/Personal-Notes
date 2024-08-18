# BIG O - Introduction
---

Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity. It is a member of a family of notations invented by Paul Bachmann, Edmund Landau, and others, collectively called Bachmann–Landau notation or asymptotic notation

**Big O analysis** is also called **Big O Asymptotic Analysis** if you wanna sound cool

## What is good code?

Good Code should be:
- Readable
- Scalable - *Big O helps in identifying scalable code*

## Types of notations in Big O

- **O(1) Constant** - no loops

- **O(log N) Logarithmic** - usually searching algorithms have log n if they are sorted (Binary Search) 

- **O(n) Linear** - for loops, while loops through n items

- **O(n log(n)) Log Linear** - usually sorting operations

- **O(n^2) Quadratic** - every element in a collection needs to be compared to ever other element. Two nested loops

- **O(2^n) Exponential** - recursive algorithms that solves a problem of size N O(n!) Factorial- you are adding a loop for every element

*Iterating through half a collection is still O(n) Two separate collections: O(a \* b)*

*Example 1*: Calculation of Big O
```js
// What is the Big O of the below function? 
function funChallenge(input) {
  let a = 10; // O(1)  //Assignments are generally ignored in Big O Calculations
  a = 50 + 3; // O(1)  //Assignments are generally ignored in Big O Calculations

  for (let i = 0; i < input.length; i++) { // O(n)
    anotherFunction(); // O(n)
    let stranger = true; // O(n) 
    a++; // O(n)
  }
  return a; // O(1) //Returns are generally ignored in Big O Calculations
}
// Big O of the above example would be:
// BIG O(3 + 4n) -> BIG O(n) // Constants and multipliers are ignored
```
*Example 2*: Calculation of Big O
```js
function anotherFunChallenge(input) {
	let a = 5; // O(1)
	let b = 10; // O(1)
	let c = 50; // O(1)
	
	for (let i = 0; i < input; i++) {
		let x = i + 1; // O(n)
		let y = i + 2; // O(n)
		let z = i + 3; // O(n)
	}
	
	for (let j = 0; j < input; j++) {
		let p = j * 2; // O(n)
		let q = j * 2; // O(n)
	}
	
	let whoAmI = "I don't know" // O(1)
}
// BIG O(4 + 5n) -> BIG O(n) // Constants and multipliers are ignored
```

## What can cause time in a function?

- Operations (+, -, \*, /)
- Comparisons (<, >, \==)
- Looping (for, while)
- Outside Function call (function())

## Rule Book

- **Rule 1** : Always worst Case

- **Rule 2** : Remove Constants
*Example*: 
```js
function printFirstItemThenFirstHalfThenSayHi100Times(items) {
    console.log(items[0]); 
    
    var middleIndex = Math.floor(items.length / 2);
    var index = 0;
    
    while (index < middleIndex) {
        console.log(items[index]);
        index++;
    }

    for (var i = 0; i < 100; i++) {
        console.log('hi');
    }
}
// BIG O(1 + n/2 + 100) -> BIG O(n)
```

- **Rule 3** : Different inputs should have different variables. O( a + b ). A and B arrays nested would be O( a \* b ) 
	\+ for steps in order 
	\* for nested steps
*Example 1*: 
```js
function compressTwoBoxes(boxes1, boxes2)
{
	boxes1.forEach((box) => {
		console.log(box)
	})
	
	boxes2.forEach((box) => {
		console.log(box)
	})
}
// BIG O(a + b) // Two different input sizes.
// If the loops were nested, instead of run seperately, the BIG O would've been BIG O(a * b)
```
*Example 2*:
```js
const boxes = ['a', 'b', 'c', 'd', 'e'];

function logAllPairsOfArray(array) {
	for ( let i = 0; i < array.length; i++ ) {
		for ( let j = 0; j < array.length; j++ ) {
			console.log( array[i], array[j] );
		}
	}
}
logAllPairsOfArray(boxes);

// BIG O(n * n) -> BIG O(n^2)
```
- **Rule 4** : Drop Non-dominant terms
*Example*:
```js
function printAllNumbersThenAllPairSums(numbers) {
  console.log("these are the numbers:");
  numbers.forEach(function(number) {
    console.log(number);
  }); // BIG O(n)

  console.log("and these are their sums:");
  numbers.forEach(function(firstNumber) {
    numbers.forEach(function(secondNumber) {
      console.log(firstNumber + secondNumber);
    });
  }); // BIG O(n^2)
}

printAllNumbersThenAllPairSums([1, 2, 3, 4, 5]); // O(n + n^2) -> O(n^2)
```
## Big O Cheat sheet

![[DSA Cheatsheet.png| Big O Cheatsheet]]

The Official Cheat sheet can be found [here](https://www.bigocheatsheet.com/)

Going back to the question, "What is good code?", it's said that good code should be both readable and scalable.
When we say scalable, it can again be split into two important components:
- Speed (Discussed so far)
- Memory

## The Three Pillars of Programming

- Readable code
- Speed
- Memory

> Balancing both speed and memory, can be hard. Say we want more speed, then we might require more memory, and say we want less memory usage then we might have to compromise on speed. Learning to balance both can give an efficient programming solution.

When a program executes, it has two ways to remember things:
- The ***Heap***: This is where we generally store variables that we assign values to. 
- The ***Stack***: This is where we actually keep track of the function calls.

## What causes Space complexity?

- Variables
- Data Structures
- Function Call
- Allocations

*Example*:
```js
// Space complexity O(1)
function boooo(n) {
// We are not creating any new variables so the space complexity here is simply 1
  for (let i = 0; i < n; i++) {
    console.log("booooo");
  }
}

// Space complexity O(n)
function arrayOfHiNTimes(n) {
/* Here we append "hi" to the array at the said index, for every iteration. So it uses more
space. Therefore the space complexity here is simply n. */
  var hiArray = [];
  for (let i = 0; i < n; i++) {
    hiArray[i] = "hi";
  }
  return hiArray;
}

arrayOfHiNTimes(6);
```