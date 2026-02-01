<style>
.box {background-color:#eee; border:1px solid; padding:8px 12px; display:inline-block}
</style>
<h1>Upload More RAM</h1>
Oh no, the ForceCodes servers are running out of memory! Luckily, you can help them out by uploading some of your RAM!<br><br>
You want to upload n GBs of RAM. Every second, you will upload either 0 or 1 GB of RAM. However, there is a restriction on your network speed: in any k consecutive seconds, you can upload only at most 1 GB of RAM in total.<br>
Find the minimum number of seconds needed to upload n GBs of RAM!<br><br><br><br>
<h3>Examples</h3>
<b>Input</b>: n = 5, k = 1<br>
<b>Output</b>: T<sub>min</sub> = 5<br>
<b>Explanation</b>: In here, you can upload 1 GB of RAM per second, so to upload 5 GBs, you need 5 seconds.<br><br>
<b>Input</b>: n = 2, k = 2<br>
<b>Output</b>: T<sub>min</sub> = 3<br>
<b>Explanation</b>: In here, you can upload 1 GB in the first second, 0 GBs in the second second, and 1 GB in the third second, which in total adds up to exactly 2 GBs of uploaded RAM.<br><br>
<b>Input</b>: n = 2, k = 3<br>
<b>Output</b>: T<sub>min</sub> = 4<br>
<b>Explanation</b>: In here, you can upload 1 GB in the first second, 0 GBs in the second second, 0 GBs in the third second, and 1 GB in the fourth second, which in total adds up to exactly 2 GBs of uploaded RAM.<br><br>
<b>Input</b>: n = 1, k = 7<br>
<b>Output</b>: T<sub>min</sub> = 1<br><br>
<b>Input</b>: n = 11, k = 5<br>
<b>Output</b>: T<sub>min</sub> = 51<br><br>
<b>Input</b>: n = 100, k = 100<br>
<b>Output</b>: T<sub>min</sub> = 9901<br><br><br><br><br><br><br><br><br><br><br><br>
<div align="center">1</div>
<h2>Solution</h2>
Because any k consecutive seconds contain at most one “1”, if you look at the first T seconds and split them into blocks of length k (with a possibly shorter last block), each block can contribute at most 1 uploaded GB.<br>
Number of such blocks = upper_bound(T/k).<br>
So the total uploaded in T seconds is ≤ upper_bound(T/k) GB<br><br>
To reach n GB, we must have upper_bound(T/k) ≥ n<br><br>
<b>FACT</b>: upper_bound(x) ≥ n if and only if x > n-1<br>
Using these,
<div align="center">
T / k > n-1<br>
T > (n-1)*k<br>
<div class="box" style="margin-top:5px">T<sub>min</sub> = (n-1)*k + 1</div>
</div><br>
<b>EDGE CASE</b>: if n = 0, no upload is needed, so T<sub>min</sub> = 0.<br><br><br><br><br>
<br><h2>Aliter,</h2>
The constraint “at most 1 GB in any k consecutive seconds” means any two upload seconds must be at least k apart. To finish as early as possible, schedule uploads at the earliest valid seconds with equal gaps k:
<div align="center">1, 1+k, 1+2k, . . . . ., 1+(n−1)k</div><br>
This is an Arithmetic Progression (AP) with first term t<sub>1</sub>=1 and common difference d=k.<br>
The time when the n-th GB is uploaded is the n-th term:<br>
<div align="center">
t<sub>n</sub> = t<sub>1</sub> + (n-1)*d = (n-1)*k + 1
</div><br><br><br><br><br>
Time Complexity of the approaches: O(1)<br>
Space Complexity of the approaches: O(1)<br><br><br><br><br><br><br><br><br><br><br>
<div align="center">2</div>
<h2>OEIS</h2>
OEIS (Online Encyclopedia of Integer Sequences) is a huge database of number sequences that often appear in math and programming. In competitive programming, if you notice outputs forming a familiar pattern (like 1, 2, 5, 14, 42…), you can search it in OEIS to quickly identify if it’s a known sequence such as Catalan numbers, Fibonacci, Bell, or partition numbers. This helps you connect the problem to known formulas, recurrences, or combinatorial identities.<br>
<br><br>Using OEIS is like having a dictionary of sequences—once you recognize the sequence, you can apply its formula or recurrence to optimize your solution. It’s especially useful in math-heavy CP problems involving combinatorics or DP. Just remember to verify the sequence against the problem constraints, since multiple sequences can match the first few terms.<br><br><br>
Website <a href="https://oeis.org/">Link</a>











