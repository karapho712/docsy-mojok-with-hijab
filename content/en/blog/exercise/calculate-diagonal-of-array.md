---
title: Calculate diagonal of array
date: 2024-10-23
categories: [Exercise]
tags: [test, exercise, javascript]
description: >
  Calculate diagonal of array
---

# TL:DR

```javascript
function diagonalDifference(matrix) {
    let primaryDiagonalSum = 0;
    let secondaryDiagonalSum = 0;

    for (let i = 0; i < matrix.length; i++) {
        primaryDiagonalSum += matrix[i][i];
        secondaryDiagonalSum += matrix[i][matrix.length - 1 - i];
    }

    return Math.abs(primaryDiagonalSum - secondaryDiagonalSum);
}
```

## Explenation

* Calculate the sum of the primary diagonal (from the top-left to the bottom-right).

* Calculate the sum of the secondary diagonal (from the top-right to the bottom-left).

* Compute the absolute difference between these two sums.