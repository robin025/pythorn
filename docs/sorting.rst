Sorting Algorithms
==================


Quick Start Guide
------------------


``Sorting Algorithms`` :- A Sorting Algorithm is used to rearrange a given array or list elements according to a comparison operator on the elements. The comparison operator is used to decide the new order of element in the respective data structure.


Following are the basic sorting algorithms


- Bubble Sort
   + Bubble sort is an algorithm that compares the adjacent elements and swaps their positions if they are not in the intended order. The order can be ascending or descending.
   + How Bubble Sort Works?
      - Compare two items.
      - If the one on the left is bigger, swap them.
      - Move one position right.
      - Linear Search Algorithm::
            bubbleSort(array)
               for i = 1 to indexOfLastUnsortedElement-1
                  if leftElement > rightElement
                     swap leftElement and rightElement
            end bubbleSort


   + Optimized Bubble Sort
      - In the simple bubble sort algorithm, all possible comparisons are made even if the array is already sorted which increases the execution time.
      - The code can be optimized by introducing an extra variable ``swapped`` so After each iteration, if there is no swapping taking place then, there is no need for performing further iterations.
      - In such a case, variable swapped is set false. Thus, we can prevent further iterations.
      - Optimized Algorithm::
            bubbleSort(array)
               swapped = false
               for i = 1 to indexOfLastUnsortedElement-1
                  if leftElement > rightElement
                     swap leftElement and rightElement
                     swapped = true
            end bubbleSort

   + Efficiency
      - For 10 data items, this is 45 comparisons ``(9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1)``.
      - In general, where ``N`` is the number of items in the array, there are ``N-1`` comparisons on the first pass, ``N-2`` on the second, and so on. The formula for the sum of such a series is ``(N–1) + (N–2) + (N–3) + ... + 1 = N*(N–1)/2 N*(N–1)/2`` is 45 (10*9/2) when ``N`` is 10.


- Insertion Sort 
   + Insertion sort works similarly as we sort cards in our hand in a card game.
   + We assume that the first card is already sorted then, we select an unsorted card. If the unsorted card is greater than the card in hand, it is placed on the right otherwise, to the left. In the same way, other unsorted cards are taken and put at their right place.
   + A similar approach is used by insertion sort.
   + Insertion sort is a sorting algorithm that places an unsorted element at its suitable place in each iteration.
   + In most cases the insertion sort is the best of the elementary sorts as described above . It still executes in O(N2) time, but it’s about twice as fast as the bubble sort and somewhat faster than the selection sort in normal situations. It’s also not too complex, although it’s slightly more involved than the bubble and selection sorts. It’s often used as the final stage of more sophisticated sorts, such as quicksort.
   + How Insertion Sort Works?
      - The first element in the array is assumed to be sorted. Take the second element and store it separately in ``key`` variable
      - Compare ``key`` variable with the first element. If the first element is greater than ``key``, then key is placed in front of the first element
      - At this stage first two elements are sorted
      - Take the third element and compare it with the elements on the left of it. Placed it just behind the element smaller than it. If there is no element smaller than it, then place it at the beginning of the array
      - Place every unsorted element at its correct position till end
      - Insertion Algorithm::
            insertionSort(array)
               mark first element as sorted
               for each unsorted element X
                  store the element X in a variable key
                  for j = lastSortedIndex down to 0
                     if current element j > X
                     move sorted element to the right by 1
               break loop and insert X here
            end insertionSort
      - Efficiency
         + How many comparisons and copies does this algorithm require? On the first pass, it compares a maximum of one item. On the second pass, it’s a maximum of two items, and so on, up to a maximum of N-1 comparisons on the last pass. This is 1 + 2 + 3 + ... + N-1 = N*(N-1)/2
         + However, because on each pass an average of only half of the maximum number of items are actually compared before the insertion point is found, we can divide by 2, which gives N*(N-1)/4
         + The number of copies is approximately the same as the number of comparisons. However, a copy isn’t as time-consuming as a swap, so for random data this algorithm runs twice as fast as the bubble sort and faster than the selection sort.
         + In any case, like the other sort routines, the insertion sort runs in O(N2) time for random data.
         + For data that is already sorted or almost sorted, the insertion sort does much better. When data is in order, the condition in the while loop is never true, so it becomes a simple statement in the outer loop, which executes N-1 times. In this case the algorithm runs in O(N) time. If the data is almost sorted, insertion sort runs in almost O(N) time, which makes it a simple and efficient way to order a file that is only slightly out of order.


- Selection Sort
   + Selection sort is an algorithm that selects the smallest element from an unsorted list in each iteration and places that element at the beginning of the unsorted list.
   + The selection sort improves on the bubble sort by reducing the number of swaps necessary from O(N2) to O(N). Unfortunately, the number of comparisons remains O(N2). However, the selection sort can still offer a significant improvement for large records that must be physically moved around in memory, causing the swap time to be much more important than the comparison time.
   + How Selection Sort Works?
      - Set the first element as ``minimum``
      - Compare ``minimum`` with the 2nd element
      - If the 2nd element is smaller than ``minimum``, assign the second element as ``minimum``
      - Compare ``minimum`` with the third element
      - Again, if the third element is smaller, then assign ``minimum`` to the third element otherwise do nothing,The process goes on until the last element
      - After each iteration, ``minimum`` is placed in the front of the unsorted list
      - For each iteration, indexing starts from the first unsorted element
      - So bascially  the list is divided into two parts: the sublist of items already sorted, which is built up from left to right and is found at the beginning, and the sublist of items remaining to be sorted, occupying the remainder of the array
      - Selection Sort Algorithm::
            selectionSort(array, size)
            repeat (size - 1) times
               set the first unsorted element as the minimum
               for each of the unsorted elements
                  if element < currentMinimum
                     set element as new minimum
               swap minimum with first unsorted position
            end selectionSort
      - Efficiency
         + The selection sort performs the same number of comparisons as the bubble sort: N*(N-1)/2. For 10 data items, this is 45 comparisons
         + However, 10 items require fewer than 10 swaps. With 100 items, 4,950 comparisons are required, but fewer than 100 swaps
         + For large values of N, the comparison times will dominate, so we would have to say that the selection sort runs in O(N2) time, just as the bubble sort did

- Counting Sort
   + Counting sort is a sorting algorithm that sorts the elements of an array by counting the number of occurrences of each unique element in the array. The count is stored in an auxiliary array and the sorting is done by mapping the count as an index of the auxiliary array
   + How Counting Sort Works?
      - Find out the maximum element (let it be max) from the given array
      - Initialize an array of length ``max+1`` with all elements 0. This array is used for storing the count of the elements in the array
      - Store the count of each element at their respective index in count array
      - For example: if the count of element 3 is 2 then, 2 is stored in the 3rd position of count array. If element "5" is not present in the array, then 0 is stored in 5th position
      - Store cumulative sum of the elements of the count array. It helps in placing the elements into the correct index of the sorted array
      - Find the index of each element of the original array in the count array. This gives the cumulative count. Place the element at the index calculated 
      - After placing each element at its correct position, decrease its count by one.
   + Counting Sort Algorithm::
      countingSort(array, size)
         max : find largest element in array
         initialize count array with all zeros
         for j <- 0 to size
            find the total count of each unique element and 
            store the count at jth index in count array
         for i <- 1 to max
            find the cumulative sum and store it in count array itself
         for j <- size down to 1
            restore the elements to array
            decrease count of each element restored by 1
   + Efficiency
      - Counting sorts fail when there are large key values (the k in the O(n)). This means that if you have a large variety of key values, counting sort will be slow
      - Radix sort can help solve that problem but it does nothing for other issue
      - Both counting and radix sort are only valid for integer keys
      - While not a terribly serious limitation, it does mean that Radix Sort's value for the number of digits in a key should not be considered constant


- Merge Sort
   + mergesort is a much more efficient sorting technique than those we saw in above section, at least in terms of speed. While the bubble, insertion, and selection sorts take ``O(N2)`` time, the mergesort is ``O(N*logN)``
   + For example, if ``N`` (the number of items to be sorted) is ``10,000``, then ``N2`` is ``100,000,000``, while``N*logN`` is only ``40,000``
   + If sorting this many items required 40 seconds with the mergesort, it would take almost 28 hours for the insertion sort.
   + Merge Sort uses Divide and Conquer Strategy
   + Using the Divide and Conquer technique, we divide a problem into subproblems. When the solution to each subproblem is ready, we 'combine' the results from the subproblems to solve the main problem.
   + The mergesort is also fairly easy to implement. It’s conceptually easier than quicksort and the Shell short.
   + The heart of the mergesort algorithm is the merging of two already-sorted arrays. Merging two sorted arrays ``A`` and ``B`` creates a third array, ``C``, that contains all the elements of ``A`` and ``B``, also arranged in sorted order.
   + Similar to quicksort the list of element which should be sorted is divided into two lists. These lists are sorted independently and then combined. During the combination of the lists the elements are inserted (or merged) on the correct place in the list
   + You divide the half into two quarters, sort each of the quarters, and merge them to make a sorted half
   + How Mergesort Works?
      - Assume the size of the left array is k, the size of the right array is m and the size of the total array is n (=k+m).
      - Create a helper array with the size n
      - Copy the elements of the left array into the left part of the helper array. This is position 0 until k-1.
      - Copy the elements of the right array into the right part of the helper array. This is position k until m-1.
      - Create an index variable i=0; and j=k+1
      - Loop over the left and the right part of the array and copy always the smallest value back into the original array. Once i=k all values have been copied back the original array. The values of the right array are already in place.
   + Efficiency
      - As we noted, the mergesort runs in O(N*logN) time. There are ``24`` copies necessary to sort ``8`` items. ``Log28`` is ``3``, so ``8*log28`` equals ``24``. This shows that, for the case of 8 items, the number of copies is proportional to ``N*log2N``
      - In the mergesort algorithm, the number of comparisons is always somewhat less than the number of copies.



- Quick Sort
   + Quicksort is an algorithm based on divide and conquer approach in which the array is split into subarrays and these sub-arrays are recursively called to sort the elements.
   + Quicksort is a divide-and-conquer algorithm that involves choosing a pivot value from a data-set and splitting the set into two subsets: a set that contains all values less than the pivot and a set that contains all values greater than or equal to the pivot. The pivot/split process is recursively applied to each subset until there are no more subsets to split. The results are combined to form the final sorted set.
   + The challenge of a quicksort is to determine a reasonable midpoint value for dividing the data into two groups. The efficiency of the algorithm is entirely dependent upon how successfully and accurate the midpoint value is selected
   + Quicksort is undoubtedly the most popular sorting algorithm, and for good reason: In the majority of situations, it’s the fastest, operating in ``O(N*logN)`` time. (This is only true for internal or in-memory sorting; for sorting data in disk files, other algorithms may be better)
   + To understand quicksort, you should be familiar with the partitioning algorithm.
   + How Quick Sort Works?
      - If the array contains only one element or zero elements then the array is sorted.
      - If the array contains more then one element then:
      - Select an element from the array. This element is called the "pivot element". For example select the element in the middle of the array.
      - All elements which are smaller then the pivot element are placed in one array and all elements which are larger are placed in another array.
      - Sort both arrays by recursively applying Quicksort to them.
      - Combine the arrays.
      - Quicksort can be implemented to sort "in-place". This means that the sorting takes place in the array and that no additional array need to be created.
   + Quick Sort Algorithm::
         quickSort(array, leftmostIndex, rightmostIndex)
            if (leftmostIndex < rightmostIndex)
               pivotIndex = partition(array,leftmostIndex, rightmostIndex)
               quickSort(array, leftmostIndex, pivotIndex)
               quickSort(array, pivotIndex + 1, rightmostIndex)

            partition(array, leftmostIndex, rightmostIndex)
            set rightmostIndex as pivotIndex
            storeIndex = leftmostIndex - 1
            for i <- leftmostIndex + 1 to rightmostIndex
            if element[i] < pivotElement
               swap element[i] and element[storeIndex]
               storeIndex++
            swap pivotElement and element[storeIndex+1]
            return storeIndex + 1
   + Efficiency
      - Quicksort operates in ``O(N*logN)`` time. This is generally true of the divide-and-conquer algorithms, in which a recursive method divides a range of items into two groups and then calls itself to handle each group. 
      - In this situation the logarithm actually has a base of ``2:`` The running time is proportional to ``N*log2N``





Time Complexity And Space Complexity

+------------------------+------------------------------------------+------------------+
|   Sorting Algorithms   |             Time Complexity              | Space Complexity |
|                        |                                          |                  |
+========================+============+==============+==============+==================+
|  Sorting               |   Best     | Average      | Worst        |       Worst      |
+------------------------+------------+--------------+--------------+------------------+
| Bubble Sort            | O(n)       | O(n^2)       | O(n^2)       |       O(1)       |
+------------------------+------------+--------------+--------------+------------------+
| Insertion Sort         | O(n)       | O(n^2)       | O(n^2)       |       O(1)       |
+------------------------+------------+--------------+--------------+------------------+
| Selection Sort         | O(n^2)     | O(n^2)       | O(n^2)       |       O(1)       |
+------------------------+------------+--------------+--------------+------------------+
| Counting Sort          | O(n+k)     | O(n+k)       | O(n+k)       |       O(k)       |
+------------------------+------------+--------------+--------------+------------------+
| Merge Sort             | O(nLogn)   | O(nLogn)     | O(nLogn)     |       O(n)       |
+------------------------+------------+--------------+--------------+------------------+
| Heap Sort              | O(nLogn)   | O(nLogn)     | O(nLogn)     |       O(1)       |
+------------------------+------------+--------------+--------------+------------------+
| Quick Sort             | O(nLogn)   | O(nLogn)     | O(n^2)       |     O(nLogn)     |
+------------------------+------------+--------------+--------------+------------------+
| ShellSort              | O(n)       | O((nLogn)^2) | O((nLogn)^2) |      O(1)        |
+------------------------+------------+--------------+--------------+------------------+






.. code-block:: python

    # import required algorithm
    >>> from package.pygostructures.data_structures.sorting import BubbleSort

    # create array
    >>> my_array = [4,1,77,2,3,0,99,100,65]

    # pass the array as argument
    >>> b = BubbleSort(my_array)

    # call the function
    >>> b.bubblesort()
    Sorted Array :  [0, 1, 2, 3, 4, 65, 77, 99, 1

   

Sorting Algorithms
------------------

.. automodule:: pythorn.data_structures.sorting

    Bubble Sort
    -----------

    .. autoclass:: BubbleSort
       :members:


    Counting Sort
    -------------


    .. autoclass:: CountingSort
       :members:




    Insertion Sort
    --------------


    .. autoclass:: InsertionSort
       :members:


    Merge Sort
    ----------


    .. autoclass:: MergeSort
       :members:


    Quick Sort
    ----------

    Example :
        .. code-block:: python

            # import required algorithm
            >>> from pythorn.data_structures.sorting import QuickSort

            # create array
            >>> f = [2,6,9,10,100,20,3,6,9,78,98,2,1500]

            # pass array , value zero and len(array)-2 as an argument 
            >>> b = QuickSort(f,0,len(f)-2)
            >>> b.quick_sort()

            # call the function
            [2, 2, 3, 6, 6, 9, 9, 10, 20, 78, 98, 100, 1500]

    .. autoclass:: QuickSort
       :members:

    
    Selection Sort
    -------------


    .. autoclass:: SelectionSort
       :members:


    Shell Sort
    -----------


    .. autoclass:: ShellSort
       :members:

       
    HeapSort
    -----------


    .. autoclass:: HeapSort
       :members:


    
