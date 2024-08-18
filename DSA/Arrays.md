# Arrays
have the least amount of rules. And because they are stored in contiguous memory (sequentially), they also tend to have a smaller memory footprint.

## Methods

| S.No | Method                           | BIG O       |
| :--- | :------------------------------- | :---------- |
| 1.   | Lookup                           | O(1)        |
| 2.   | Push (Static) / Append (Dynamic) | O(1) / O(n) |
| 3.   | Insert                           | O(n)        |
| 4.   | Delete                           | O(n)        |
*Example*:

```js
const strings= ['a', 'b', 'c', 'd'];
const numbers = [1,2,3,4,5];
// Variable array is somewhere in memory and the computer knows it.
// When I do array[2], i'm telling the computer, hey go to the array and grab the 3rd item from where the array is stored.


//push
strings.push('e'); // O(1)

//pop
strings.pop(); 
strings.pop(); // O(1)

//unshift
strings.unshift('x')  // O(n)

//splice
strings.splice(2, 0, 'alien'); // O(n)

console.log(strings)
```

## Arrays are of two types
- Static
- Dynamic


## Say we want to build Our own array, then we do it the following way:

```js
class MyArray {

    constructor() {
        this.length = 0;
        this.data = {};
    }

    get(index) {
        return this.data[index];
    }

    push(item) {
        this.data[this.length] = item;
        this.length++;

        return this.length;
    }

    pop() {
        const lastItem = this.data[this.length - 1];

        delete this.data[this.length - 1];
        this.length--;

        return lastItem;
    }

    delete(index) {
        const item = this.data[index];

        this.shiftItems(index);

        return item;
    }

    shiftItems(index) {
        for (let i = index; i < this.length - 1; i++) {
            this.data[i] = this.data[i + 1];
        }

        delete this.data[this.length - 1];
        this.length--;
    }
}

const newArray = new MyArray();

newArray.push("hi");
newArray.push("you");
newArray.push("!");

newArray.pop();

newArray.delete(1);

console.log(newArray);
```
