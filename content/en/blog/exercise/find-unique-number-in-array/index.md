---
title: How to find unique number in array
date: 2024-10-15
categories: [Exercise]
tags: [test, exercise, javascript]
description: >
  How to find unique number in array
---

# TL:DR

```javascript
const numbers = [1, 2, 3, 4, 3, 2, 1];

const uniqueNumbers = numbers.filter((num, index, arr) => {
  return arr.indexOf(num) === arr.lastIndexOf(num);
});

console.log(uniqueNumbers); 
```

### Or using an object-based approach

```javascript
const frequency = {};

numbers.forEach(num => {
  frequency[num] = (frequency[num] || 0) + 1;
});

const uniqueNumbers = Object.keys(frequency).filter(key => frequency[key] === 1).map(Number);

console.log(uniqueNumbers);
```

***
***

## Explenation 1

```javascript
const numbers = [1, 2, 3, 4, 3, 2, 1];

const uniqueNumbers = numbers.filter((num, index, arr) => {
  return arr.indexOf(num) === arr.lastIndexOf(num);
});

console.log(uniqueNumbers); 
```

* a.filter(...):    
The filter() method is used to create a new array that contains only the elements that pass the condition specified in the callback function.
In this case, the callback function takes three parameters:
    * num: The current element in the array a.
    * index: The index of that element in the array a.
    * arr: The array a itself.

* arr.indexOf(num):  
The indexOf() method returns the first index of the element num in the array arr.
For example, if num is 2 and 2 first appears at index 1, indexOf(num) will return 1.

* arr.lastIndexOf(num):  
The lastIndexOf() method returns the last index of the element num in the array arr.
For example, if num is 2 and 2 last appears at index 5, lastIndexOf(num) will return 5.

* Condition arr.indexOf(num) === arr.lastIndexOf(num):  
This condition checks whether the element appears only once in the array. If indexOf(num) and lastIndexOf(num) are the same, it means the element appears only once in the array.
If this is true, the element will be included in the result array produced by filter().

## Explenation 1 (using an object-based approach)

```javascript
const frequency = {};

numbers.forEach(num => {
  frequency[num] = (frequency[num] || 0) + 1;
});

const uniqueNumbers = Object.keys(frequency).filter(key => frequency[key] === 1).map(Number);

console.log(uniqueNumbers);
```

* const frequency = {};  
Creates an empty object that will store the frequency of each number in the array.

* numbers.forEach(num => {...}):  
    * Uses the forEach() method to iterate over the array numbers.
    * In each iteration, the line frequency[num] = (frequency[num] || 0) + 1 adds the number to the frequency object as a key and increments its frequency.
    * If num is already in the frequency object, its frequency is incremented by 1. If it is not, it is initialized with 0 first.


* Object.keys(frequency).filter(...).map(Number):  
    * Object.keys(frequency) returns an array of all the keys (numbers in string form) from the frequency object.
    * filter(key => frequency[key] === 1) keeps only the keys where the value (frequency) is equal to 1, meaning the number appears once.
    * map(Number) converts the keys, which are strings, back to numbers.