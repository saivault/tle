<style>
    .cc { background-color: #eee;border-radius: 4px;padding:2px; }
    .flash { text-decoration:underline;font-weight:bold; }
    .stylish { font-family:Yeon Sung;line-height:15px;font-size:15px;text-align:center;font-weight:bold;margin:10px }
    .nicehead{ font-size:20px; font-family:Rubik; }
    .topichead { font-size:32px;padding-bottom:10px;font-family:Rowdies }
    .box {background-color:#eee; border:1px solid; padding:8px 12px; display:inline-block}
</style>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@800&family=Rowdies:wght@300&family=Rubik:wght@500&family=Rubik:wght@500&family=Yeon+Sung&family=Finlandica:ital,wght@1,700&family=Alkatra:wght@500&display=swap" rel="stylesheet">
<h1 class="topichead" id="">Searching and Sorting</h1>
Most problems in Computer Science can be reduced to:<br>
Searching → finding something in a defined space.<br>
Sorting → arranging data to make searching, optimization, and decision-making easier.<br><br>
<br><br><br><h2 class="nicehead">Searching</h2>
Searching is the process of efficiently finding a solution or a specific piece of information within a defined search space.<br><br>
Search space can be:
<ul>
<li>Explicit: arrays, lists, databases.</li>
<li>Implicit: range of values, possible states of a problem, decision trees.</li>
</ul><br><br><br><br>
<h2>What can we search for?</h2>
<h3>Finding an element</h3>
<ul>
<li>Example: Does a number exist in an array?</li>
<li>Techniques: Linear Search, Binary Search.</li>
</ul>
<h3>Optimization</h3>
<ul>
<li>Example: What is the maximum/minimum value that satisfies a condition?</li>
<li>Techniques: Binary Search on answer, Greedy, Dynamic Programming.</li>
</ul>
<h3>Thresholds / Boundaries</h3>
<ul>
<li>Example: Where does a property start or stop being true?</li>
<li>Techniques: Binary Search variations (lower_bound, upper_bound).</li>
</ul>
<h3>Pathfinding / State Search</h3>
<ul>
<li>Example: Shortest path in a graph, solving puzzles.</li>
<li>Techniques: BFS, DFS, Dijkstra’s, A*.</li>
</ul>
<br><br><br><br><br><br><br><br><div align="center">1</div>
<h2>Linear Search</h2>
Linear Search is the simplest searching algorithm.<br><br>
It works by checking each element in a dataset sequentially until:
<ul>
<li>The target value is found → return its index/position.</li>
<li>The dataset is completely traversed → target not found.</li>
</ul>
<b>NOTE</b>: Works on both sorted and unsorted datasets.<br><br><br>
<h3>Implementation</h3>

```cpp
int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target)
            return i;  // found at index i
    }
    return -1;  // not found
}
```
Input: arr = [5, 3, 7, 2, 8], target = 7<br>
Output: Index = 2<br><br><br>
Time Complexity: O(n), where n is the size of the dataset<br>
Space Complexity: O(1)<br><br><br><br><br><br><br>
<h2>Binary Search</h2>
Binary Search is a highly efficient algorithm for finding the position of a target element in a sorted dataset.<br><br>
It works by repeatedly dividing the search interval in half until:
<ul>
<li>The target is found → return its index.</li>
<li>The interval becomes empty → target not found.</li>
</ul><br>
<b>NOTE</b>: Not suitable for linked lists (no random access).<br>
<br><br><br><br><br><br><br><div align="center">2</div>
<h3>Implementation</h3>

```cpp
int binarySearch(int arr[], int n, int target) {
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2; // avoid overflow
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1; // not found
}
```
Input: arr = [2, 3, 5, 7, 8], target = 7<br>
Output: Index = 3<br><br><br>
Time Complexity: O(log<sub>2</sub>n)<br>
Space Complexity: O(1) in iterative and O(log n) in recursive (stack space)<br><br><br><br>
<br><br><br><h2 class="nicehead">Sorting</h2>
Sorting is the process of arranging data or elements in a specific order, typically ascending or descending.<br>
It helps organize data for efficient searching, processing, and problem-solving.<br><br>
<b>Example</b>: Take an unsorted array [7, 2, 9, 1, 5],<br>
It becomes [1, 2, 5, 7, 9] after sorting.<br><br><br><br>
<h3>What Can Be Sorted?</h3>
- Numbers → e.g., sorting test scores in ascending order.<br>
- Strings → e.g., sorting names alphabetically.<br>
- Objects/Structures → e.g., sorting students by grade, age, or custom criteria.<br>

<br><br><br><br><br><br><br>
<div align="center">3</div>
<h3>Why Sorting Matters?</h3>
Sorting is often used as a preprocessing step or a core part of algorithms:
<ul style="margin-top:5px">
<li><b>Binary Search</b> requires sorted data to search efficiently.</li>
<li><b>Greedy Algorithms</b>: Many greedy approaches need sorted input (e.g., activity selection, interval scheduling).</li>
<li><b>Grouping/Deduplication</b>: Easy to detect duplicates, group elements when sorted.</li>
</ul><br><br>
<b>NOTE</b>: Though it's easier to search on a sorted array, but maintaining order on insertion/deletion costs extra.<br><br><br><br><br><br><br>
<h2>CHARACTERISTICS OF SORTING</h2>
<h3>Stable Sorting</h3>
A sorting algorithm is called stable if it preserves the relative order of elements with equal keys/values.<br>
This is essential when sorting by multiple keys. Example: If you sort students by grade, and then sort again by name, a stable sort ensures that students with the same grade remain in the same relative order from the previous sort.<br><br>
<b>Example</b>: Unsorted list (with marks):<br>
[(Alice, 90), (Bob, 85), (Charlie, 90), (David, 80)]<br>
Sorted by marks (stable):<br>
[(David, 80), (Bob, 85), (Alice, 90), (Charlie, 90)]<br><br><br><br><br><br>
<h3>In-Place Sorting</h3>
A sorting algorithm is called in-place if it requires only a constant amount of extra space (O(1)), aside from the input array.<br><br>
<b>Examples</b>: QuickSort rearranges elements within the array itself without requiring extra storage. MergeSort creates additional arrays during merging → not in-place.<br><br><br><br>
<br><br><br><br><br><div align="center">4</div>
<h2>Bubble Sort</h2>
Bubble Sort is a simple comparison-based sorting algorithm.<br>
It repeatedly swaps adjacent elements if they are in the wrong order, making larger elements “bubble up” to the end.<br><br><br>
<h3>Implementation</h3>

```cpp
void bubbleSort(int arr[], int n) {
    // Outer loop → runs n-1 passes
    for (int i = 0; i < n - 1; i++) {
        bool swapped = false; // Optimization: check if array is already sorted

        // Inner loop → compares adjacent elements
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap if elements are in the wrong order
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }

        // If no swaps in this pass → array is already sorted
        if (!swapped) break;
    }
}
```
<br>
Time Complexity of the algorithm: O(n<sup>2</sup>)<br>
Space Complexity of the algorithm: O(1) => in-place<br>
It's a stable sorting algorithm.<br><br><br><br><br><br><br>
<h2>Selection Sort</h2>
Selection Sort is a simple comparison-based sorting algorithm.<br>
It works by repeatedly selecting the minimum element from the unsorted portion and swapping it with the first unsorted element.<br><br><br><br><br><br><br><br>
<div align="center">5</div>
<h3>Implementation</h3>

```cpp
void selectionSort(int arr[], int n) {
    // Outer loop → move the boundary of the unsorted array
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i; // Assume the current element is the smallest

        // Inner loop → find the index of the minimum element
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j; // Update minIndex if a smaller element is found
            }
        }

        // Swap the found minimum element with the first unsorted element
        swap(arr[i], arr[minIndex]);
    }
}
```
<br>Time Complexity of the algorithm: O(n<sup>2</sup>)<br>
Space Complexity of the algorithm: O(1) => in-place<br>
Not a stable sorting algorithm as it can swap equal elements and change their order.<br><br>
<br><br><br><br><br>








