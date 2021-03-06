---
title: "[Algorithm] Sorting Algorithms"
categories: [ Algorithm ]
updated: false
comments: true
---

## Preface

Sorting would be the first well-formed algorithm that beginners encounter. This is the very fundamental technique in most of problem solvings. For example, other algorithms, such as search and merge algorithms, require sorted input data. I firmly believe that sorting algorithm is the most useful to know among innumerable algorithms.

{% include table-of-contents.html contents="Sorting Algorithms, Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Quick Sort, Time complexity, Other sorting algorithms" %}

## Sorting Algorithms

### Sorting Algorithms

* All of the sorting algorithms share the same goal: **Sorting the data**.
* But, the difference among those is the way that each algorithms goes on.
* As the way varies, the efficiency would be vary. The efficiency of the program highly depends on how the data is arranged and what specific rule, such as ascending or descending, is applied.
* Here are some well-known sort algorithms:
  - Bubble Sort
  - Selection Sort
  - Insertion Sort
  - Merge Sort
  - Quick Sort
* In efficiency of specific algorithm, it is important to know two factors about it:
  - **Time Complexity**: How fast the algorithm runs.
  - **Space Complexity**: How much space the algorithm operates in.
* In most cases, becuase of high-tech hardware and the era of big data, time complexity is regarded much more important than space complexity. (It does not mean that space complexity is not important)
* Let's find out how different those algorithms are and what is different.
* There is a sample **C++** code about the implementation below each algorithm without comments. It's not the only way to implement algorithm. Analyzing my sample code will be a nice try, but implementing yourself is more recommended.

### Bubble Sort

* **Bubble Sort** compares two adjacent elements and then swaps them if they are not in order. This process is repeated until no more swapping is needed.

* Before sorting: [3, 2, 1, 4]
  - First phase: [3, 2, 1, 4] -> [**2, 3**, 1, 4] -> [2, **1, 3**, 4] -> [2, 1, **3, 4**]
  - Second phase: [2, 1, 3, 4] -> [**1, 2**, 3, 4] -> [1, **2, 3**, 4] -> [1, 2, **3, 4**]
  - Third phase: [1, 2, 3, 4] -> [**1, 2**, 3, 4] -> [1, **2, 3**, 4] -> [1, 2, **3, 4**]
  - The repetition terminates as no more changes occured in third phase.
  
* Time complexity:
  - Best: O(n)
  - Average: O(n^2)
  - Worst: O(n^2)
  
* Space complexity:
  - This algorithm does not need additional storages.
  
```cpp
// Written in C++

void swap(int &a, int &b){
  int tmp = a;
  a = b;
  b = tmp;
}

void bubbleSort(int arr[], int len){
  bool swapped = true;
  while(swapped){
    swapped = false;
    for(int i=0; i<len-1; i++){
      if(arr[i] > arr[i+1]){
        swap(arr[i], arr[i+1]);
      swapped = true;
      }
    }
  }
}
```

### Selection Sort

* **Selection Sort** finds the smallest element in the array and swaps it with the element in the first position. That element becomes the last element of the sorted list. Continues in this way in the unsorted array until the entire array is sorted.

* Before sorting: [4, 2, 1, 3]
  - First phase: [4, 2, 1, 3] -> [**1**, 2, **4**, 3]
  - Second phase: [1, 2, 4, 3] -> [1, **2**, 4, 3]
  - Third phase: [1, 2, 4, 3] -> [1, 2, **3, 4**]
  
* Time complexity:
  - Best: O(n^2)
  - Average: O(n^2)
  - Worst: O(n^2)
  
* Space complexity:
  - This algorithm does not need additional storages.
  
```cpp
// Written in C++

void swap(int &a, int &b){
  int tmp = a;
  a = b;
  b = tmp;
}

void selectionSort(int array[], int len){
  int min_index;
  for(int last_elem = 0; last_elem < len - 1; last_elem++){
    min_index = last_elem;
    for(int i=last_elem; i<len; i++){
      if(arr[i] < arr[min_index]) min_index = i;
    }
    swap(arr[last_elem], arr[min_index]);
  }
}
```

### Insertion Sort

* **Insertion Sort** separates the array in two sections, sorted and not sorted, and grows sorted section up until the whole elements are sorted, just like Selection sort; however, the way of growing is different. It choose the first element in unsorted part and place it in the appropriate position in the sorted section. If confusing, look at an example below.

* Before sorting: [4, 2, 1, 3]
  - First phase: [4, 2, 1, 3] -> [**2, 4**, 1, 3]
    + At the first phase, the very first element in the original array is regarded as sorted section in itself.
  - Second phase: [2, 4, 1, 3] -> [**2, 1, 4**, 3] -> [**1, 2, 4**, 3]
    + From the second phase, expands the sorted section by placing element in the appropriate position in it.
	+ Note that the element `1` is sliding down to find its appropriate position.
  - Third phase: [1, 2, 4, 3] -> [**1, 2, 3, 4**]
  
* Time complexity:
  - Best: O(n)
  - Average: O(n^2)
  - Worst: O(n^2)
  
* Space complexity:
  - This algorithm does not need additional storages.
  
```cpp
// Written in C++

void swap(int &a, int &b){
  int tmp = a;
  a = b;
  b = tmp;
}

void insertionSort(int arr[], int len){
  for(int i=1; i<lenn; i++){
    int j=i;
    while(j > 0 && arr[j] < arr[j-1]){
      swap(arr[j], arr[j-1]);
      j--;
    }
  }
}
```

### Merge Sort

* **Merge Sort** operates by breaking down array into smaller and more easily sortable arrays. It divides the array in half over and over again until each piece is only one item long. Then those items are put back together in specific order.
  - Solving problems by **dividing** large problems into smaller problems and then **conquering** from those is called **Divide and Conquer** algorithm, which is very famous problem solving technique.
  
* Before sorting: [2, 1, 7, 8, 4, 6, 3, 5]
  - **Dividing**
    + First phase: [2, 1, 7, 8] [4, 6, 3, 5]
    + Second phase: [2, 1] [7, 8] [4, 6] [3, 5]
    + Third phase: [2] [1] [7] [8] [4] [6] [3] [5]
  - **Conquering**
    + First phase: [1, 2] [7, 8] [4, 6] [3, 5]
    + Second phase: [1, 2, 7, 8] [3, 4, 5, 6]
    + Third phase: [1, 2, 3, 4, 5, 6, 7, 8]
	
* Time complexity:
  - Best: O(n log n)
  - Average: O(n log n)
  - Worst: O(n log n)
	
```cpp
// Written in C++

void merge(int arr[], int from, int mid, int to){
  int i=from, j=mid+1, idx=0;
  int tmp[to - from + 1];
  
  while(i <= mid && j <= to){
    if(arr[i] < arr[j]) tmp[idx++] = arr[i++];
    else tmp[idx++] = arr[j++];
  }
  
  while(i <= mid) tmp[idx++] = arr[i++];
  while(j <= to) tmp[idx++] = arr[j++];
  
  for(int i=from; i <= to; i++) arr[i] = tmp[i - from];
}

void mergeSort(int arr[], int from, int to){
  if(from == to) return;
  if(from < to) {
    int mid = (from + to) / 2;
    mergeSort(arr, from, mid);
    mergeSort(arr, mid + 1, to);
    merge(arr, from, mid, to);
  }
}
```

### Quick Sort

* **Quick Sort** is another **Divide and Conquer** algorithm. The idea of quick sort is dividing data based on pivot. In the case of ascending sort, in every dividing moment, the elements which value is smaller than pivot are placed on left side of it and the ones bigger than pivot are placed on right side.

* How to choose the pivot varies the implementation of quick sort. Common way to pick pivot is choosing one of these: the first element, last element, median element, or random element. Becuase this varies time complexity in specific case, choosing random element as pivot is recommended in order to achieve average efficiency in general cases.

* Before sorting: [2, 1, 7, 8, 4, 6, 3, 5]
  - If confusing, directly go to the sample code and try to follow the flow of the algorithm. This example chooses pivot as the last value in each dividing moment.
  - First phase:
    + [2, 1, 7, 8, 4, 6, 3, 5]
	+ [2, 1, **5**, 8, 4, 6, 3, **7**]
	+ [2, 1, **3**, 8, 4, 6, **5**, 7]
	+ [2, 1, 3, **5**, 4, 6, **8**, 7]
	+ [2, 1, 3, **4**, **5**, 6, 8, 7]
	+ [2, 1, 3, 4] (5) [6, 8, 7]
  - Second phase: [2, 1, 3, 4] (5) [6, 8, 7] -> [[2, 1, 3] (4)] (5) [[6] (7) [8]]
  - Third phase: [[2, 1, 3] (4)] (5) [[6] (7) [8]] -> [[[2, 1] (3)] (4)] (5) [[6] (7) [8]]
  - Fourth phase: [[[2, 1] (3)] (4)] (5) [[6] (7) [8]] -> [[[[1] (2)] (3)] (4)] (5) [[6] (7) [8]]
  
* Time complexity:
  - Best: O(n log n)
  - Average: O(n log n)
  - Worst: O(n^2)
  
```cpp
// Written in C++

void swap(int &a, int &b){
  int tmp = a;
  a = b;
  b = tmp;
}

void quickSort(int arr[], int left, int right){
  if(left >= right) return;
  
  int pivot = arr[right];
  int l = left, r = right;
  while(l < r){
    while(arr[r] > pivot && l < r) r--;
    while(arr[l] < pivot && l < r) l++;
    if(l < r) swap(arr[l], arr[r]);
  }
  quickSort(arr, left, l - 1);
  quickSort(arr, r + 1, right);
}
```

### Time complexity

* Some of those have O(n^2) time complexity and others have O(n log n). None of those have constant time complexity. Why?

* Sorting needs to visit every element at least one. That is why there's no constant time complexity. At least O(n) time is required.

* Most of sorting algorithms have similar pattern: picking one element and then compare it with other elements. As sorting algorithms pick every element and compare it with every element, most of algorithms have O(n^2) complexity.

* Then how O(n log n) is possible? Draw graph of `y = x^2` and `y = x log x`. The difference between those is not meaningful on the small value `x`. The bigger `x` is, however, the gap between `y` widens correspondingly. This means that the O(n log n) algorithms are absolutely outstanding than the O(n^2) algorithms when it operates on very long array.

* The idea is on **dividing the data**. Separating the problems into easily solvable ones has great effect on time efficiency.
  - Orinial array's length is `n`. And dividing it half over and over again until the devided array's length becomes 1. Assuming that `k` iterations need until that, `n = 2^k`.
  - The dividing time complexity of sorting algorithm can be expressed as the number of dividing, `k`. And each phase needs O(n) time as they need to sort each array. So, total time complexity becomes O(nk) = O(n log n).

* This pattern is very common in other **divide and conquer** algorithms which divide data in half.

### Other sorting algorithms

* Googling **Sorting Algorithms**. There would be a lot of algorithms: Heap Sort, Radix Sort, Bucket Sort, etc. The five algorithms which I showed you in this post are not only well-known but also fundamental ones. If you want to study more about sorting algorithms, googling yourself or refer to this site.

[GeeksforGeeks - Sorting Algorithms](https://www.geeksforgeeks.org/sorting-algorithms/)