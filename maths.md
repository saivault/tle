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
<h1 class="topichead" id="" style="margin-bottom:5px">Modular Arithmetic</h1>
Modular arithmetic is a system of arithmetic where <span class="flash">numbers “wrap around” after reaching a certain value</span>, called the modulus.<br>
Formally: For a positive integer m, two numbers a and b are congruent modulo m if their difference is divisible by m:
<div class="stylish">a ≡ b (mod m) if and only if m | (a-b)</div>
This means a and b leave the same remainder when divided by m.<br><br><br>
Analogy: Think of a clock. On a 12-hour clock, 15:00 is the same as 3:00.<br>
Because 15 ≡ 3 (mod 12). Numbers keep cycling every 12 hours, just like modular arithmetic cycles every m.<br><br><br><br><br><br>
<h3>In C++</h3>
We implement modular arithmetic in C++ using the % operator: a % m gives the remainder, cycling values within [0, m−1].<br>
But watch out: with negatives, a % m can be negative. Normalize with:

```cpp
long long modulo(long long a, long long m) {
    a %= m;
    if (a < 0) a += m;
    return a;
}
```
<br><br><br><br>
Addition and multiplication “stay on the clock” when you reduce after each step.

```cpp
const long long M = 1'000'000'007;
long long add = (a % M + b % M) % M;            // (a + b) % M
long long sub = ((a % M - b % M) + M) % M       // (a - b) % M 
long long mul = ((a % M) * (b % M)) % M;        // (a * b) % M 
```
<br><br><br><br><br><br><br><div align="center">1</div>
<b>NOTE</b>: Always reduce early and often to prevent overflow: cast to long long and mod after each operation.<br>
<b>NOTE</b>: The operators %, *, and / all share the same precedence level, so use brackets when needed to ensure the intended order of operations.<br><br>
<div class="stylish">That’s modular arithmetic<br>do math on a circle instead of a line</div>
<br><br><br><br><br>
<h2>Modular Division</h2>
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br><br>
<div align="center">2</div>
<h1 class="topichead" id="">Basic Mathematics</h1>
<h2 class="nicehead">Greatest Common Divisor</h2>
The Greatest Common Divisor (GCD) of two or more integers, which are not all zero, is the largest positive integer that divides each of the integers without leaving a remainder. Example: GCD(12, 18) = 6<br>
<b>ANALOGY</b>: If you have 12 chocolates and 18 biscuits, and want to make identical gift packs without leftovers, the maximum number of packs you can make is GCD(12, 18) = 6. <br><br>
<br><br><br><br><h3>Properties</h3>
<ul>
<li>Commutative: GCD(a, b) = GCD(b, a)</li>
<li>Associative: GCD(a, GCD(b, c)) = GCD(GCD(a, b), c)</li>
<li>Divisibility: If a % b == 0, then GCD(a, b) = b</li>
<li>For any integer a ≠ 0, a | 0 because 0 = a * 0</li>
<li>Two consecutive integers are always coprime: GCD(a, a+1) = 1<br>
As any divisor of both a and a+1 must also divide their difference: (a+1)−a=1</li>
<li>Can be extended for arrays using a loop.</li>

```cpp
int arr_gcd(vector<int>& arr) {
    int g = arr[0];
    for (int i = 1; i < arr.size(); i++)
        g = gcd(g, arr[i]);
    return g;
}
```
</ul><br><br><br><br><br>
<h2>Euclidean Algorithm</h2>
The algorithm works on the principle:
<div class="stylish">GCD(A, B) = GCD(B, A % B)</div>
This is because the remainder of dividing A by B is still divisible by the same GCD.<br><br>
<br><br><br><br><br><div align="center">3</div>
<h3>Step-by-Step Explanation</h3>
<ul>
<li>If A ≥ B, then GCD(A, B) = GCD(A - B, B) (repeated subtraction).</li>
<li>Instead of repeated subtraction, we use modulus: GCD(A, B) = GCD(B, A%B)</li>
<li>Base case: if B = 0, then GCD(A, B) = A.</li>
</ul><br><br><br>
<h3>Proof Sketch</h3>
If GCD(A, B) = G, then A = a*G and B = b*G.<br>
<ul>
<li>Subtraction: (A - B) = (a - b)*G, still divisible by G.</li>
<li>Modulus: A % B = (a % b) * G, also divisible by G.</li>
</ul>
Thus the GCD remains unchanged.<br><br><br><br>
<h3>GCD Implementation</h3>

```cpp
int gcd(int a, int b) {
    return (b == 0) ? a : gcd(b, a % b);
}
```
Each step reduces the numbers significantly (by modulus).<br>
Runs in O(log(min(a, b))), very efficient for large inputs.<br><br><br><br><br><br><br><br>
<h2 class="nicehead">Least Common Multiple</h2>
The Least Common Multiple (LCM) of two or more integers is the smallest positive integer that is divisible by each of the integers.<br>
<b>Example</b>: LCM of 6 and 8 is 24 as both 6 | 24 and 8 | 24<br><br><br>
<b>ANALOGY</b>: Think of LCM as the point where two clock hands meet again: If one clock ticks every A minutes and another every B minutes, The time they first tick together again is LCM(A, B).<br><br><br><br><br><br><br><br>
<div align="center">4</div>
<h3>Properties</h3>
<ul>
<li>Commutative: LCM((a, b) = LCM((b, a)</li>
<li>Associative: LCM(a, LCM(b, c)) = LCM(LCM(a, b), c)</li>
<li>LCM(A, 0) = 0</li>
</ul><br><br><br><br><br><br>
<h2>Relation with GCD</h2>
<div class="stylish">LCM(A, B) * GCD(A, B) = A*B</div>
Also, GCD(A, B) ≤ min(A, B) ≤ A, B ≤ max(A, B) ≤ LCM(A, B) ≤ A*B 
<br><br><h3>Proof</h3>
For any two positive integers A and B, the above relation holds.<br>
To see why, let g = GCD(A,B). Then we can write A = g*x and B = g*y, where GCD(x, y) = 1. Since x and y are coprime, their least common multiple is simply LCM(x,y) = x*y. Thus, LCM(A,B) = g*LCM(x,y) = g*x*y.<br>
Multiplying this with GCD gives (g*x*y)*g = g<sup>2</sup>xy, which is equal to (gx)(gy) = A*B.<br><br><br><br><br><br>
<h3>LCM Implementation</h3>

```cpp
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}

long long lcm(int a, int b) {
    return 1LL * a * b / gcd(a, b);
}
```
<br><br><br><br><br><br><br><br><br><br>
<div align="center">5</div>








