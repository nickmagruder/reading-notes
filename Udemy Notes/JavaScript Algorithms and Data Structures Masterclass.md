# JavaScript Algorithms and Data Structures Masterclass

# Section 2 - Big O

# Trees
- DOM is a tree!
## Binary Trees



<br/><br/><br/><br/>






# Section 15: Merge Sort

## Merge Sort Algorithms are much more efficient
- Bubble sort is quadratic
## Faster Sorts
- Can improve time complexity from O(n2) to O(n log n)
- More complex, harder to understand
# Merge Sort
- Created 1948 - Jonathan van Neuman
- Combination of splitting up, merging and sorting
- Exploits fact that arrays of 0 or 1 element are always sorted
- Works by decomposing an array into smaller arrays of 0 or 1 elements, then building up a newly sorted array
### How does it work?
- First splits an array in half
- Then splits those in half
- Until each element is in it's own array
- Then, it starts merging them back together
- Comparing sorted arrays is easier than unsorted
### Merging the Arrays
- To complete a merge-sort, you first need a function for merging two sorted arrays.
- When you have two sorted arrays, the helper function will return a new array which consists of all elements from the two input arrays
- Will run on O(n + m) time and O(n + m) space and will not modify the paramaters passed to it
### Pseudocode
- Create an empty array to be returned at the end
- First look at the smallest values in each input array
  - Typically use a while loop ("while" we still haven't looked at every element/there are elements left)
    - If the value of first value in first array is smaller than first value value in the second array, push that value into return array, then move on to next value in first array
    - If the value of the firsty value in the first array is LARGER than the first value in the second array, we push the value of the SECOND array into the return array and move on to the next value in the SECOND array
      - Once one array is exhausted, push all remaining values in the return array
### Code
```javascript
function merge(arr1, arr2) {
  let results = [];
  let i = 0;
  let j = 0;

  while (i < arr1.length && j < arr2.length) {
    if (arr2[j] > arr1[i]) {
      results.push(arr1[i]);
      i++;
    } else {
      results.push(arr2[j]);
      j++;
    }
  }
  while (i < arr1.length) {
    results.push(arr1[i]);
    i++;
  }
  while (j < arr2.length) {
    results.push(arr2[j]);
    j++;
  }
  return results;
}
```

## Sorting Portion
### PseudoCode
- Break the array into halves until you have arrays that are empty or have one element
- Once we have those sorted arrays we merge them back with our merge function
- Seems simple, but isnt!
- Once merged, return the final (merged and sorted) array!

### Code
```javascript
function mergeSort(arr){
  if(arr.length <= 1) return arr;
  let mid = Math.floor(arr.length/2);
  let left = mergeSort(arr.slice(0,mid));
  let right = mergeSort(arr.slice(mid));

  return merge(left, right);
}
```

## Merge-Sort Big O
- Time (Best, Avg, & Worse): O(n log n)
- Space: O(n)



<br/><br/><br/><br/>



# Quick Sort
- Similar to merge sort, uses the face that arrays of 0 or 1 are inherently always sorted
- Functions by the selection of a single element, the "pivot," and then finding the index of where that pivot should ideally be in the final, sorted array
  - Then, move all smaller numbers to the left and larger ones to the right, but not yet sort them
    - After this, the "pivot" is in the right position.
    - Then, we repeat the process on the left and right, similarly to merge sort, recursively


# Partition/Pivot (Helper Function)
- To do a quick sort, it is helpful to create a helper function that arranges elements in an array on each side of the "pivot"
- With array as argument, function selects an element as the pivot
- It arranges smaller values to the left, and larger values to the right, order doesn't matter
- Function arranges "in-place", no new array
- Returns the pivot's index

# Pivot Selection
- Ideally this would be the median
- For this solution, we will select the first element

# Hash Tables

## What makes a good Hash?
- Fast (ie constant time)
- Doesnt cluster outputs at specific indices, but distributes uniformly
- Deterministic, same input yields same ouput

## charcode MINUS <a number> = number in the alphabet
- a - <a number... find this number> = 1

## Use prime numbers, less collisions 

## Handling Collisions
- Separate Chaining
  - Store at same spot using a nested data structure, multiple key-value-pairs a the same position
- Linear probing
  - Only storing one piece of data at each position
  - When collison, we look forward in array to the next empty spot

## Separate Chaining Implementation
- Set / Get
  - Set 
  1. Accept a key and a value
  2. Hash the key
  3. Store the key-value pair in the hash table array via separate chaining
  - Get
  1. Accepts a key
  2. Hashes the key
  3. Retrieves the key-value pair in the hash table
  4. If the key isnt found, returns undefined

### Keys / Values
- Keys
  - Loops through the hash table array and returns an array of keys in the table 
- Values
  - Loops through the hash table array and reutns an array of values in the table
