# Binary Search in Assembly Language

## Binary Search
Binary search is a divide-and-conquer algorithm used to search for a specific element in a sorted array. It works by repeatedly dividing the search range in half and comparing the middle element with the target value. If the middle element is equal to the target, the search is successful. If the middle element is greater or less than the target, the search continues in the left or right half of the array, respectively. This process continues until the target element is found or the search range becomes empty.

Binary search is highly efficient, especially for large sorted arrays, as it eliminates half of the remaining elements in each iteration. This makes it much faster than linear search, which examines each element one by one.

## Code
The binary search code is implemented in x86 assembly language. It takes three parameters:
- `ebx` - Base address of the sorted array.
- `ecx` - Length of the array.
- `edx` - Target value to search for.

The result (the index of the target) is returned in the `eax` register. Here's the code:
```
assembly
section .text
global binary_search

binary_search:
    mov eax, -1              ; Initialize result to -1 (not found)
    mov esi, 0               ; Initialize left index to 0
    mov edi, ecx             ; Initialize right index to array length - 1
    
binary_search_loop:
    cmp esi, edi             ; Compare left and right indices
    jg binary_search_done    ; If left index is greater than right index, exit loop
    
    mov ebx, esi             ; Calculate middle index (ebx = (esi + edi) / 2)
    add ebx, edi
    shr ebx, 1
    
    mov al, [ebx + ebx]      ; Load the value at the middle index into al (assuming each element is a byte)
    cmp al, dl               ; Compare with the target value in dl
    je binary_search_found   ; If equal, set eax to the middle index and exit
    
    jl binary_search_right   ; If less, adjust left index
    jg binary_search_left    ; If greater, adjust right index
    
binary_search_left:
    mov edi, ebx             ; Adjust right index to middle - 1
    dec edi
    jmp binary_search_loop   ; Continue the loop
    
binary_search_right:
    mov esi, ebx             ; Adjust left index to middle + 1
    inc esi
    jmp binary_search_loop   ; Continue the loop
    
binary_search_found:
    mov eax, ebx             ; Set eax to the index of the found element
    ret

binary_search_done:
    ret
```

## Usage
To use the binary search function, you can follow these steps:

1. Assemble the assembly code into an executable.
2. Call the `binary_search` function with the base address of the sorted array in `ebx`, the length of the array in `ecx`, and the target value in `edx`.
3. The result (index of the target) will be returned in the `eax` register.

## Project By
This project was created by:

1. Liza [PRN: 2214110206]
2. Divyansh [PRN: 2214110195]
3. Sargam [PRN: 2214110137]
