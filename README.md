Quick Sort
Code 
import time


best_case = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]    
average_case = [3, 7, 2, 8, 1, 5, 10, 6, 9, 4] 
worst_case = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]   


def measure_time(sort_func, arr, *args):
    start_time = time.time()
    sort_func(arr, *args)  
    end_time = time.time()
    return end_time - start_time


def quick_sort(arr, low, high):
    if low < high:
        pi = partition(arr, low, high)
        quick_sort(arr, low, pi - 1)
        quick_sort(arr, pi + 1, high)


def partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    for j in range(low, high):
        if arr[j] < pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1


def measure_quick_sort():
    print("\nQuick Sort Performance:")
    
   
    best = best_case[:]
    average = average_case[:]
    worst = worst_case[:]
    
    print("Best Case:", measure_time(lambda arr: quick_sort(arr, 0, len(arr) - 1), best))
    print("Average Case:", measure_time(lambda arr: quick_sort(arr, 0, len(arr) - 1), average))
    print("Worst Case:", measure_time(lambda arr: quick_sort(arr, 0, len(arr) - 1), worst))


measure_quick_sort()

Merge Sort 
Code
import time
best_case = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]    
average_case = [3, 7, 2, 8, 1, 5, 10, 6, 9, 4] 
worst_case = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]   
def measure_time(sort_func, arr):
    start_time = time.time()
    sort_func(arr)
    end_time = time.time()
    return end_time - start_time
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0

        
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1


def measure_merge_sort():
    print("\nMerge Sort Performance:")
    
    best = best_case[:]
    average = average_case[:]
    worst = worst_case[:]
    
    print("Best Case:", measure_time(merge_sort, best))
    print("Average Case:", measure_time(merge_sort, average))
    print("Worst Case:", measure_time(merge_sort, worst))


measure_merge_sort()
Selection Sort
Code
import time


best_case = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]    
average_case = [3, 7, 2, 8, 1, 5, 10, 6, 9, 4] 
worst_case = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]   


def measure_time(sort_func, arr):
    start_time = time.time()
    sort_func(arr)
    end_time = time.time()
    return end_time - start_time


def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]


def measure_selection_sort():
    print("\nSelection Sort Performance:")
    
    best = best_case[:]
    average = average_case[:]
    worst = worst_case[:]
    
    print("Best Case:", measure_time(selection_sort, best))
    print("Average Case:", measure_time(selection_sort, average))
    print("Worst Case:", measure_time(selection_sort, worst))


measure_selection_sort()
Bubble Sort
Code
import time

# Test Arrays for Bubble Sort
best_case = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]    # Already sorted array
average_case = [3, 7, 2, 8, 1, 5, 10, 6, 9, 4] # Randomly shuffled array
worst_case = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]   # Reverse sorted array

# Function to measure execution time
def measure_time(sort_func, arr):
    start_time = time.time()
    sort_func(arr)
    end_time = time.time()
    return end_time - start_time

# Bubble Sort Implementation
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

# Measure Time for Bubble Sort
def measure_bubble_sort():
    print("\nBubble Sort Performance:")
    # Make copies of the arrays to ensure original ones aren't altered
    best = best_case[:]
    average = average_case[:]
    worst = worst_case[:]
    
    print("Best Case:", measure_time(bubble_sort, best))
    print("Average Case:", measure_time(bubble_sort, average))
    print("Worst Case:", measure_time(bubble_sort, worst))

# Run Bubble Sort Test
measure_bubble_sort()

