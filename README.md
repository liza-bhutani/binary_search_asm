# Binary Search in Assembly Language

## Binary Search
Binary search is a divide-and-conquer algorithm used to search for a specific element in a sorted array. It works by repeatedly dividing the search range in half and comparing the middle element with the target value. If the middle element is equal to the target, the search is successful. If the middle element is greater or less than the target, the search continues in the left or right half of the array, respectively. This process continues until the target element is found or the search range becomes empty.

Binary search is highly efficient, especially for large sorted arrays, as it eliminates half of the remaining elements in each iteration. This makes it much faster than linear search, which examines each element one by one.
The binary search code is implemented in x86 assembly language. It takes three parameters:
- `ebx` - Base address of the sorted array.
- `ecx` - Length of the array.
- `edx` - Target value to search for.

## Project By
This project was created by:

1. Liza [PRN: 2214110206]
2. Divyansh [PRN: 2214110195]
3. Sargam [PRN: 2214110137]
