---
title: Counting sort 1
date: 2024-10-24
categories: [Exercise]
tags: [test, exercise, javascript]
description: >
  Counting sort 1
---

# TL:DR

Add limitation: 
```
int[100]: a frequency array
```

```javascript
function countingSort(arr) {
    const count = new Array(100).fill(0);

    for (let i = 0; i <= arr.length; i++) {
        count[arr[i]] = count[arr[i]] + 1;
    }
    
    return count;
}
```

## Explenation

1. Create array count: Array count is used to store the number of occurrences of each element. We fixed the size 100 base on the limitation

2. Count occurrences of elements: In this step, we iterate through the input array and increase the number of occurrences of each element in the count array.

