# Count Inversions in an array

## Brute Force

**Approach** use two loops and just check every element on right

**Time Complexity** o(N*N)

## Optimal

**note** this below is copied from TUF article but basically while merging they are adding a count for no of Inversions

he steps are basically the same as they are in the case of the merge sort algorithm. The change will be just a one-line addition inside the merge() function. Inside the merge(), we need to add the number of pairs to the count when a[left] > a[right].

**The steps of the merge() function were the following:**

     In the merge function, we will use a temp array to store the elements of the two sorted arrays after merging. Here, the range of the left array is low to mid and the range for the right half is mid+1 to high.
    Now we will take two pointers left and right, where left starts from low and right starts from mid+1.
    Using a while loop( while(left <= mid && right <= high)), we will select two elements, one from each half, and will consider the smallest one among the two. Then, we will insert the smallest element in the temp array. 
    After that, the left-out elements in both halves will be copied as it is into the temp array.
    Now, we will just transfer the elements of the temp array to the range low to high in the original array.

**Modifications in merge() and mergeSort():**


    In order to count the number of pairs, we will keep a count variable, cnt, initialized to 0 beforehand inside the merge().
    While comparing a[left] and a[right] in the 3rd step of merge(), if a[left] > a[right], we will simply add this line:
    cnt += mid-left+1 (mid+1 = size of the left half)
    Now, we will return this cnt from merge() to mergeSort(). 
    Inside mergeSort(), we will keep another counter variable that will store the final answer. With this cnt, we will add the answer returned from mergeSort() of the left half, mergeSort() of the right half, and merge().
    Finally, we will return this cnt, as our answer from mergeSort().

**for time Complexity it will be same as for merge sort nlogn for code check out the TUF**

