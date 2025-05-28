# Week 5: Detailed Notes and Code for Common Sorting Techniques

## Visualiser: https://visualgo.net/en/sorting
## 🎯 Learning Objectives

* Understand sorting algorithms and their implementation in C++ and Python.
* Analyze the efficiency of different sorting techniques.
* Compare sorting algorithms based on use case, performance, and stability.

## 🔍 Introduction

Sorting organizes data for efficient operations like searching and merging. Sorting orders can be ascending (smallest to largest) or descending (largest to smallest).

## 🔍 Bubble Sort

* **Detailed Idea:** Repeatedly step through the list, compare adjacent elements, and swap them if they are out of order. Each iteration moves the largest unsorted item to its correct position.
* **Simple Explanation:** Like bubbles rising to the surface in water. Larger numbers "float up."
* **Code:**

```cpp
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {
        for (int j = 0; j < n-i-1; j++) {
            if (arr[j] > arr[j+1]) std::swap(arr[j], arr[j+1]);
        }
    }
}
```

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n-1):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]: arr[j], arr[j+1] = arr[j+1], arr[j]
```
- Complexity Table:

| Metric           | Value |
| ---------------- | ----- |
| Best Case        | O(n)  |
| Average Case     | O(n²) |
| Worst Case       | O(n²) |
| Space Complexity | O(1)  |
| Stability        | Yes   |
## 🔍 Selection Sort

* **Detailed Idea:** Divides the list into sorted and unsorted parts. Selects the smallest unsorted element and swaps it to the end of the sorted part.
* **Simple Explanation:** Like finding the smallest card in a hand and placing it in order.
* **Code:**

```cpp
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {
        int min_idx = i;
        for (int j = i+1; j < n; j++) {
            if (arr[j] < arr[min_idx]) min_idx = j;
        }
        std::swap(arr[min_idx], arr[i]);
    }
}
```

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n-1):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]: min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
```
- Complexity Table:

| Metric           | Value   |
|-------------------|---------|
| Best Case        | O(n²)   |
| Average Case     | O(n²)   |
| Worst Case       | O(n²)   |
| Space Complexity | O(1)    |
| Stability        | No      |

## 🔍 Insertion Sort

* **Detailed Idea:** Builds the sorted list by picking elements from the unsorted list and inserting them into their correct position.
* **Simple Explanation:** Like sorting playing cards by placing each card into its right spot.
* **Code:**

```cpp
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
```
- Complexity Table:

| Metric           | Value   |
|-------------------|---------|
| Best Case        | O(n)    |
| Average Case     | O(n²)   |
| Worst Case       | O(n²)   |
| Space Complexity | O(1)    |
| Stability        | Yes     |
## 🔍 Merge Sort

* **Detailed Idea:** Divides the list into halves, recursively sorts each half, then merges them into a sorted list.
* **Simple Explanation:** Like splitting a deck of cards into two piles, sorting each, and combining them.
* **Code:**

```cpp
void merge(int arr[], int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;
    int L[n1], R[n2];
    for (int i = 0; i < n1; i++) L[i] = arr[l + i];
    for (int j = 0; j < n2; j++) R[j] = arr[m + 1 + j];
    int i = 0, j = 0, k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) arr[k++] = L[i++];
        else arr[k++] = R[j++];
    }
    while (i < n1) arr[k++] = L[i++];
    while (j < n2) arr[k++] = R[j++];
}
void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}
```

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr)//2
        L, R = arr[:mid], arr[mid:]
        merge_sort(L)
        merge_sort(R)
        i = j = k = 0
        while i < len(L) and j < len(R):
            if L[i] < R[j]: arr[k] = L[i]; i += 1
            else: arr[k] = R[j]; j += 1
            k += 1
        while i < len(L): arr[k] = L[i]; i += 1; k += 1
        while j < len(R): arr[k] = R[j]; j += 1; k += 1
```
- Complexity Table:

| Metric           | Value   |
|-------------------|---------|
| Best Case        | O(n log n) |
| Average Case     | O(n log n) |
| Worst Case       | O(n log n) |
| Space Complexity | O(n)    |
| Stability        | Yes     |

## 🔍 Quick Sort

* **Detailed Idea:** Picks a pivot element, partitions list into smaller and larger elements, and recursively sorts partitions.
* **Simple Explanation:** Like dividing a pile of cards around a chosen card and sorting both sides.
* **Code:**

```cpp
int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            std::swap(arr[i], arr[j]);
        }
    }
    std::swap(arr[i + 1], arr[high]);
    return i + 1;
}
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```

```python
def quick_sort(arr):
    if len(arr) <= 1: return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```
- Complexity Table:

| Metric           | Value   |
|-------------------|---------|
| Best Case        | O(n log n) |
| Average Case     | O(n log n) |
| Worst Case       | O(n²)   |
| Space Complexity | O(log n) |
| Stability        | No      |
## 🧠 Summary

* Sorting algorithms covered: bubble, selection, insertion, merge, and quick sort.
* Each has unique performance, stability, and memory considerations.
* Use case depends on dataset size, memory, and performance requirements.

