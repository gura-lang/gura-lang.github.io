---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-32.html#naviitem-selected
nextpage: chapter-34.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">33</span>math Module</h1>
<h2><span class="caption-index-2">33.1</span><a name="anchor-33-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">math</code> module provices functions for mathematical calculation. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">33.2</span><a name="anchor-33-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">math.abs</strong></div>
<div style="margin-bottom:1em"><code>math.abs(num):map</code></div>
Returns an absolute value.
</p>
<p>
<div><strong style="text-decoration:underline">math.acos</strong></div>
<div style="margin-bottom:1em"><code>math.acos(num):map:[deg]</code></div>
Returns an inverse cosine value.
</p>
<p>
In default, the result is returned in radian. Specifying an attribute <code class="highlighter-rouge">:deg</code> would return that in degree.
</p>
<p>
<div><strong style="text-decoration:underline">math.arg</strong></div>
<div style="margin-bottom:1em"><code>math.arg(num):map:[deg]</code></div>
Returns an argument, an angle from the real-axis in the complex plane, of a complex number.
</p>
<p>
In default, the angle value is returned in radian. Specifying an attribute <code class="highlighter-rouge">:deg</code> would return that in degree.
</p>
<p>
<div><strong style="text-decoration:underline">math.asin</strong></div>
<div style="margin-bottom:1em"><code>math.asin(num):map:[deg]</code></div>
Returns an inverse sine value.
</p>
<p>
In default, the result is returned in radian. Specifying an attribute <code class="highlighter-rouge">:deg</code> would return that in degree.
</p>
<p>
<div><strong style="text-decoration:underline">math.atan</strong></div>
<div style="margin-bottom:1em"><code>math.atan(num):map:[deg]</code></div>
Returns an inverse tangent value.
</p>
<p>
<div><strong style="text-decoration:underline">math.atan2</strong></div>
<div style="margin-bottom:1em"><code>math.atan2(num1, num2):map:[deg]</code></div>
Returns an inverse tangent value of a fraction of num1 and num2.
</p>
<p>
In default, the result is returned in radian. Specifying an attribute <code class="highlighter-rouge">:deg</code> would return that in degree.
</p>
<p>
<div><strong style="text-decoration:underline">math.bezier</strong></div>
<div style="margin-bottom:1em"><code>math.bezier(nums[]+:number)</code></div>
Returns a list that consists of functions that generate coordinates of bezier curves with specified control points. One or more lists of control points can be specified. This means that if you give it two lists of numbers as arguments, it returns two functions of bezier curve.
</p>
<p>
<div><strong style="text-decoration:underline">math.ceil</strong></div>
<div style="margin-bottom:1em"><code>math.ceil(num):map</code></div>
Returns a nearest integer number above or equal to the specified value.
</p>
<p>
<div><strong style="text-decoration:underline">math.conj</strong></div>
<div style="margin-bottom:1em"><code>math.conj(num):map</code></div>
Returns a conjugate of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.cos</strong></div>
<div style="margin-bottom:1em"><code>math.cos(num):map:[deg]</code></div>
Returns a cosine value.
</p>
<p>
In default, the given argument is treated as a radian number. Specifying an attribute <code class="highlighter-rouge">:deg</code> would treat that as a degree number.
</p>
<p>
<div><strong style="text-decoration:underline">math.cosh</strong></div>
<div style="margin-bottom:1em"><code>math.cosh(num):map</code></div>
Returns a hyperbolic cosine value.
</p>
<p>
<div><strong style="text-decoration:underline">math.covariance</strong></div>
<div style="margin-bottom:1em"><code>math.covariance(a, b)</code></div>
Returns a covariance between the <code class="highlighter-rouge">a</code> and <code class="highlighter-rouge">b</code>.
</p>
<p>
<div><strong style="text-decoration:underline">math.cross</strong></div>
<div style="margin-bottom:1em"><code>math.cross (a, b)</code></div>
Calculates a cross product between <code class="highlighter-rouge">a</code> and <code class="highlighter-rouge">b</code>.
</p>
<p>
<div><strong style="text-decoration:underline">math.delta</strong></div>
<div style="margin-bottom:1em"><code>math.delta(num):map</code></div>
Evaluates a delta function with a given argument <code class="highlighter-rouge">num</code> that returns <code class="highlighter-rouge">1</code> when <code class="highlighter-rouge">num == 0</code> and <code class="highlighter-rouge">0</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">math.diff</strong></div>
<div style="margin-bottom:1em"><code>math.diff(expr:expr, var:symbol):map {block?}</code></div>
Calculates a mathematical differential expression of the given <code class="highlighter-rouge">expr</code> by a variable <code class="highlighter-rouge">var</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|rtn:expr|</code>, where <code class="highlighter-rouge">rtn</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Example: <code class="highlighter-rouge">math.diff(</code>(math.sin(x 2)), <code class="highlighter-rouge">x)</code>**
</p>
<p>
<div><strong style="text-decoration:underline">math.dot</strong></div>
<div style="margin-bottom:1em"><code>math.dot(a, b)</code></div>
Calculates a dot product between <code class="highlighter-rouge">a</code> and <code class="highlighter-rouge">b</code>.
</p>
<p>
<div><strong style="text-decoration:underline">math.exp</strong></div>
<div style="margin-bottom:1em"><code>math.exp(num):map</code></div>
Returns an exponential value.
</p>
<p>
<div><strong style="text-decoration:underline">math.fft</strong></div>
<div style="margin-bottom:1em"><code>math.fft(seq[])</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.floor</strong></div>
<div style="margin-bottom:1em"><code>math.floor(num):map</code></div>
Returns a nearest integer number below or equal to the specified value.
</p>
<p>
<div><strong style="text-decoration:underline">math.gcd</strong></div>
<div style="margin-bottom:1em"><code>math.gcd(a:number, b+:number):map</code></div>
Returns a greatest common divisor among two or more numbers.
</p>
<p>
<div><strong style="text-decoration:underline">math.hypot</strong></div>
<div style="margin-bottom:1em"><code>math.hypot(x, y):map</code></div>
Returns a hyperbolic tangent value.
</p>
<p>
<div><strong style="text-decoration:underline">math.imag</strong></div>
<div style="margin-bottom:1em"><code>math.imag(num):map</code></div>
Returns an imaginary part of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.integral</strong></div>
<div style="margin-bottom:1em"><code>math.integral()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.lcm</strong></div>
<div style="margin-bottom:1em"><code>math.lcm(a:number, b+:number):map</code></div>
Returns a least common multiple among two or more numbers.
</p>
<p>
<div><strong style="text-decoration:underline">math.least_square</strong></div>
<div style="margin-bottom:1em"><code>math.least_square(x:iterator, y:iterator, dim:number =&gt; 1, var:symbol =&gt; `x)</code></div>
Takes two iterators <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> that return coordinate of points and returns a function that fits them using least square metho. You can specify the fitting curve's dimension by an argument <code class="highlighter-rouge">dim</code>, which default value is one. The variable symbol used in the function is <code class="highlighter-rouge">x</code>, which can be changed by specifying an argument <code class="highlighter-rouge">var</code>.
</p>
<p>
<div><strong style="text-decoration:underline">math.log</strong></div>
<div style="margin-bottom:1em"><code>math.log(num):map</code></div>
Returns a natural logarithm value.
</p>
<p>
<div><strong style="text-decoration:underline">math.log10</strong></div>
<div style="margin-bottom:1em"><code>math.log10(num):map</code></div>
Returns a decadic logarithm value.
</p>
<p>
<div><strong style="text-decoration:underline">math.norm</strong></div>
<div style="margin-bottom:1em"><code>math.norm(num):map</code></div>
Returns a norm value of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.optimize</strong></div>
<div style="margin-bottom:1em"><code>math.optimize(expr:expr):map {block?}</code></div>
Returns an optimized expression of the given argument <code class="highlighter-rouge">expr</code>, which needs to be made up of mathematical elements.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|rtn:expr|</code>, where <code class="highlighter-rouge">rtn</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">math.real</strong></div>
<div style="margin-bottom:1em"><code>math.real(num):map</code></div>
Returns a real part of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.relu</strong></div>
<div style="margin-bottom:1em"><code>math.relu(num):map</code></div>
Evaluates a rectified linear unit function with a given argument <code class="highlighter-rouge">num</code> that returns <code class="highlighter-rouge">num</code> when <code class="highlighter-rouge">num &gt;= 0</code> and <code class="highlighter-rouge">0</code> otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">math.sin</strong></div>
<div style="margin-bottom:1em"><code>math.sin(num):map:[deg]</code></div>
Returns a sine value.
</p>
<p>
In default, the given argument is treated as a radian number. Specifying an attribute <code class="highlighter-rouge">:deg</code> would treat that as a degree number.
</p>
<p>
<div><strong style="text-decoration:underline">math.sinh</strong></div>
<div style="margin-bottom:1em"><code>math.sinh(num):map</code></div>
Returns a hyperbolic sine value.
</p>
<p>
<div><strong style="text-decoration:underline">math.sqrt</strong></div>
<div style="margin-bottom:1em"><code>math.sqrt(num):map</code></div>
Returns a square root value.
</p>
<p>
<div><strong style="text-decoration:underline">math.tan</strong></div>
<div style="margin-bottom:1em"><code>math.tan(num):map:[deg]</code></div>
Returns a tangent value.
</p>
<p>
In default, the given argument is treated as a radian number. Specifying an attribute <code class="highlighter-rouge">:deg</code> would treat that as a degree number.
</p>
<p>
<div><strong style="text-decoration:underline">math.tanh</strong></div>
<div style="margin-bottom:1em"><code>math.tanh(num):map</code></div>
Returns a hyperbolic tangent value.
</p>
<p>
<div><strong style="text-decoration:underline">math.unitstep</strong></div>
<div style="margin-bottom:1em"><code>math.unitstep(num):map</code></div>
Evaluates a unit step function with a given argument <code class="highlighter-rouge">num</code> that returns <code class="highlighter-rouge">1</code> when <code class="highlighter-rouge">num &gt;= 0</code> and <code class="highlighter-rouge">0</code> otherwise.
</p>
{% endraw %}
