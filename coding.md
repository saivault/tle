<style>
    .cc { background-color: #eee;border-radius: 4px;padding:2px; }
    .flash { text-decoration:underline;font-weight:bold; }
    .stylish { font-family:Yeon Sung;line-height:15px;font-size:15px;text-align:center;font-weight:bold;margin:10px }
    .nicehead{ font-size:20px; font-family:Rubik; }
    .topichead { font-size:32px;padding-bottom:10px;font-family:Rowdies }
</style>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@800&family=Rowdies:wght@300&family=Rubik:wght@500&family=Rubik:wght@500&family=Yeon+Sung&family=Finlandica:ital,wght@1,700&family=Alkatra:wght@500&display=swap" rel="stylesheet">
<h1 class="topichead" id="" style="margin-bottom:5px">Basics of Coding</h1>
<h2>Why C++?</h2>
<ul>
<li>It offers fast execution, being closer to hardware compared to languages like Python or Java.</li>
<li>It comes with the Standard Template Library (STL), which provides efficient and ready-to-use data structures like vectors, sets, maps, and algorithms such as sorting and binary search.</li>
</ul><br><br><br><br><br><br>
<h2>Header files</h2>
Header files allow us to declare variables, functions, classes, and other code elements that can be shared across multiple source files. They help in organizing code and avoiding repetition.<br>
<div style="margin:5px 0">
● Pre-existing Header Files: These are provided by the compiler and cover a wide range of functionalities (I/O, math, data structures, etc...).<br>
● User-defined Header Files: These are written by the programmer to keep code modular and manageable. They may contain templates, helper functions, or reusable classes. Not common in CP.
</div>

```cpp
#include <header_file> 
```
<br><br><br><br><br>
<h2>Namespaces</h2>
A namespace is a scope of the program that can store various useful functions and variables. Two ways to use namespaces:<br>
<div style="margin:5px 0">
● Use scope resolution operator “::” to use the values inside the namespace.<br>
● Type <span class="cc">using namespace name;</span> at the start of the file.
</div>
Namespaces are used to avoid conflicting names.<br><br><br><br><br><br><br>
<div align="center">1</div>
<h2 class="nicehead">Basic Constructs</h2>
<h3>Arrays</h3>
An array is a collection of multiple items of the same datatype.<br>
● Arrays are ordered, meaning they are continuous in memory.<br>
● The size of an array cannot be changed, once declared.<br>

```cpp
DataType arrayName[arraySize];
```
<br><br><br><br>
<h3>Functions</h3>
Functions are reusable blocks of code that can be run whenever called.<br>
They can take in parameters (input) and return a value (output).

```cpp
// Function definition syntax
ReturnType FunctionName(Type1 param1, Type2 param2, ...) {
    // Function body
    // Must return a value of type 'ReturnType'
    return value;
}
```
<br>
● The order of parameters passed is important while function calling.<br>
● Be sure to check and return value of the required type only.<br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<div align="center">2</div>
<h1 class="nicehead">Range of Datatypes</h1>
<h2>int vs long long int</h2>
An <span class="cc">int</span> in C++ typically uses 4 bytes (32 bits), so its maximum value is:
<div align="center">2<sup>31</sup> - 1 = 2,147,483,647 ≈ 2×10<sup>9</sup></div><br>
The range of <span class="cc">int</span> datatype is [-2<sup>31</sup>, 2<sup>31</sup>-1] = [INT_MIN, INT_MAX]<br>
<b>NOTE</b>: (INT_MAX + 1) leads us back to (INT_MIN) value.<br><br><br>
A <span class="cc">long long int</span> uses 8 bytes (64 bits), allowing values up to:
<div align="center">2<sup>63</sup> - 1 = 9,223,372,036,854,775,807 ≈ 9×10<sup>18</sup></div><br>
The range of <span class="cc">long long int</span> datatype is [-2<sup>63</sup>, 2<sup>63</sup>-1] = [LLONG_MIN, LLONG_MAX]<br><br>
<b>TIP</b>: Even multiplying two large ints can overflow. Use 1LL * a * b to ensure the result is promoted to long long.<br><br><br><br><br><br>
<h2>float / double / long double</h2><br><br><br><br><br><br><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br>
<div align="center">3</div>
<h2>setprecision</h2>
setprecision is a stream manipulator (from &lt;iomanip&gt;) that controls how many digits are printed when you output floating-point numbers using cout.<br><br>
<ul>
<li><b>Without fixed (Default)</b>: Controls total number of significant digits (before + after decimal).</li>
<li><b>With fixed</b>: Controls exactly n digits after the decimal point.</li>
<li><b>With scientific</b>: Prints in scientific notation (prints in x.yyyyyye±zz form) with n digits after the decimal.</li>
</ul><br>

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    double num = 123.456789;

    cout << setprecision(4) << num << endl;          // 123.5
    cout << fixed << setprecision(4) << num << endl; // 123.4568
    cout << scientific << setprecision(4) << num << endl; // 1.2346e+02
    
    int mod = 1e9+7;
    cout << mod; // 1000000007
    
    return 0;
}
```
<br><br><br><br><br><br>
<h2>Resources for Competitive Programming</h2>
<ul>
<li><a href="https://cses.fi/problemset/">CSES Problem set</a></li>
<li>https://github.com/kth-competitive-programming/kactl</li>
<li><a href="https://docs.google.com/spreadsheets/d/1YfQz0RgE4AIgSyC_BVDLVfoeBUJYcUNxbd1VvQEfFFU/edit?usp=sharing">Excel sheet with resources, problems, template and difficulty</a></li>
<li><a href="https://codeforces.com/blog/entry/78520">Reference books</a></li>
</ul><br><br><br><br><br><br><br><br>
<div align="center">4</div>
<h2 class="nicehead">Common Errors we encounter</h2>
When solving coding problems in C++, errors typically fall into a few broad categories. Understanding them can help debug more efficiently.<br><br>
<ul>
<li style="margin-top:10px"><b>Compilation Errors (Syntax Errors)</b>: These are errors detected by the compiler when code does not conform to C++ grammar rules.<br>Eg: Missing semicolon, Using undeclared variable, Type mismatch</li>
<li style="margin-top:10px"><b>Runtime Errors</b>: These occur while the program is running. The code compiles fine, but crashes or behaves unexpectedly at runtime.<br>
Eg: Division by 0, Invalid memory access, Stack overflow (infinite recursion)
</li>
<li style="margin-top:10px"><b>Logical Errors</b>: The program runs without crashing but produces wrong output due to incorrect logic. Hardest to catch as compilers don't report them.</li>
<li style="margin-top:10px"><b>Semantic Errors</b>: These occur when the syntax is valid, so the code compiles without any error, but it does not behave as intended due to misused language rules or incorrect assumptions.</li>

```cpp
if (a = b) 
// wrong operator used: always returns true

int a = 1, b = 2;
float c = a / b;           // Outputs: 0
// Integer division used instead of floating-point

for (int i = 0; i <= 10; i++) { ... }
// Incorrect loop condition

arr[x]          // accessing array index out of bounds
```
<li style="margin-top:15px"><b>Timeout Errors</b>: Occurs when your code takes longer than allowed time limits.
Eg: Inefficient algorithm, Infinite loops</li>
<li style="margin-top:10px"><b>Memory Limit Exceeded (MLE)</b>: Program uses more memory than allowed by the problem constraints.<br>
Eg: Declaring huge arrays, Not deleting dynamically allocated memory</li>
<li style="margin-top:10px"><b>Segmentation Fault</b>: Occurs due to illegal access of memory.</li>
</ul><br><br><br><br><br><br><br><br><br><br><br>
<div align="center">5</div>
<h2 class="nicehead">When do we get a Segmentation Fault?</h2>
<h3>1. Far Out-of-Bounds Access</h3>
Accessing an index well beyond the allocated size (e.g., arr[1000000]) may hit protected memory regions.

```cpp
int arr[5];
arr[1000000] = 10; // Likely segfault
```
<br><br><h3>2. Accessing a Null Pointer</h3>
Dereferencing a null pointer is guaranteed to cause a segmentation fault.

```cpp
int* ptr = nullptr;
ptr[0] = 5; // Immediate crash
```
<br><br><h3>3. Accessing Freed or Invalid Heap Memory</h3>
Using a pointer after delete, or indexing far beyond a dynamically allocated array can lead to a crash.

```cpp
int* arr = new int[5];
delete[] arr;
arr[2] = 10; // Use-after-free: may crash

int* big = new int[5];
big[10000] = 42;  // Invalid index: possible crash
```
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<div align="center">6</div>
<h1 class="topichead" id="" style="margin-bottom:5px">Complexities</h1>
<h3>Elementary Operations</h3>
An operation that takes constant time is called an elementary operation.<br>
<b>Examples</b>: Arithmetic Operations, Comparison of primitive datatypes, Input and Output of primitive datatypes.<br><br>
10<sup>8</sup> arithmetic operations ≈ 1 second of time<br><br><br><br><br><br>
<h2 class="nicehead">Time Complexity</h2>
Time complexity describes how the number of operations in an algorithm grows relative to the input size N.<br>
It allows us to estimate whether our code will run within the given constraints. Instead of exact execution time (which depends on hardware, compiler, etc.), we focus on growth rate.<br>
<br><br><br><br><br>
<h2>Big-O Notation</h2>
Big-O gives the upper bound (worst-case growth rate) of an algorithm.<br>
Written as: O(f(N)) where f(N) describes how the runtime scales with input size.<br><br>
<ul>
<li>O(1) → Constant time (accessing an array element).</li>
<li>O(log N) → Logarithmic time (binary search on a sorted array)</li>
<li>O(N) → Linear time (looping through an array).</li>
<li>O(N logN) → Linearithmic time (sortings: merge sort, quick sort)</li>
<li>O(N²) → Quadratic time (nested loops).</li>
<li>O(2<sup>N</sup>) → Exponential time (subset related problems)</li>
<li>O(N!) → Facotrial time (permutation related problems)</li>
</ul>
</div><br><br><br><br><br><br><br><br>
<div align="center">1</div>
<img src="https://raw.githubusercontent.com/saivault/dsanotes/refs/heads/main/store/bigo.jpg" height="250" width="400" style="margin-left:80px"><br>
<b>Note</b>: For both logn and nlogn in the above graph, the base is 2<br><br><br><br><br><br>
<h2>Rules for Big-O Notation</h2>
● Should not have constants. <span class="cc">O(N + K) = O(N)</span><br>
● Should not have constant factors. <span class="cc">O(N / 2) = O(N)</span><br>
● Only include the fastest growing function for each variable. <span class="cc">O(N<sup>2</sup> + N) = O(N<sup>2</sup>)</span><br>
● Can never be 0. Has to be at least O(1).<br><br><br>
<b>Examples</b>:<br>
O(N * (N+1)/2) = O(N<sup>2</sup>)<br>
O(2N<sup>2</sup> + 4N + 4(M<sup>3</sup> + 5) + 10) = O(N<sup>2</sup> + M<sup>3</sup>)<br><br>
<br><br>
<h3>Problem: Finding Time Complexity of the code snippet - 1</h3>

```cpp
for (int i=0; i<n; i++) {
    for (int j=0; j<n/2; j++) {
        // Elementary operations ......
    }
}
```
<br><br><br><br><br><div align="center">2</div>
<b>ANALYSIS</b>: 
<ul style="margin-top:-8px">
<li>The outer loop runs n times.</li>
<li>For each iteration of the outer loop, the inner loop runs n/2 times.</li>
</ul>
So, the total number of operations = n * (n/2) = n<sup>2</sup>/2<br>
Time Complexity = O(n<sup>2</sup>/2) = O(n<sup>2</sup>)<br><br><br><br><br><br><br>
<h3>Problem: Finding Time Complexity of the code snippet - 2</h3>

```cpp
for (int i=12; i <= n-123; i += 5) {
    for (int j=6; j <= m*2; j += 321) {
        for (int k=4023; k > 23; k -= 16) {
            // Elementary operations ......
        }
    }
}
```
<br>
Time Complexity = O( n-135/5 * m*2-6/321 * 4023-23/16) = O(n*m)<br><br><br><br><br><br><br>
<h3>Problem: Finding Time Complexity of the code snippet - 3</h3>

```cpp
for (int i=1; i<n; i*=2) {
    // Elementary operations ......
}
```
In this loop, the variable i starts at 1 and doubles each time (i *= 2). This means it takes values like 1, 2, 4, 8, 16, and so on, growing exponentially.<br>
The loop continues until i reaches or exceeds n, so the number of iterations is about the number of times you can double 1 before hitting n, which is log<sub>2</sub>(n)<br>
Since each iteration does only constant work, the overall time complexity is O(log n).<br><br>
<br><br><br><br><br><br><br><div align="center">3</div>
<h2>Points to Note</h2>
<ul>
<li>Always identify which variables influence the time complexity of your solution.</li>
<li>Even if problem constraints allow slower solutions, aim to optimize. For example, when 
n=1000, both O(n<sup>2</sup>) and O(n) might work, but the O(n) approach is still preferable.</li>
<li>Pay attention to test case conditions. Sometimes, the problem specifies limits across all test cases (e.g., “The sum of n over all test cases does not exceed X”), which can change how you design your solution.</li>
<li>While Big-O notation ignores constants and lower-order terms, in practice, these constant factors can significantly impact performance.</li>
</ul><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<div align="center">4</div>























