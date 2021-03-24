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






# Reading 18

## Review, Research, and Discussion

## Terms
