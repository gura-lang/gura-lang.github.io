---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">31</span><a name="anchor-31"></a>math Module</h1>
<p>
The <code>math</code> module provices functions for mathematical calculation. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">31.1</span><a name="anchor-31-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">math.real</strong></div>
<div style="margin-bottom:1em"><code>math.real(num):map</code></div>
Returns a real part of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.imag</strong></div>
<div style="margin-bottom:1em"><code>math.imag(num):map</code></div>
Returns an imaginary part of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.arg</strong></div>
<div style="margin-bottom:1em"><code>math.arg(num):map:[deg]</code></div>
Returns an argument value of a complex number in radian.
</p>
<p>
<div><strong style="text-decoration:underline">math.norm</strong></div>
<div style="margin-bottom:1em"><code>math.norm(num):map</code></div>
Returns a norm value of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.conj</strong></div>
<div style="margin-bottom:1em"><code>math.conj(num):map</code></div>
Returns a conjugate of a complex number.
</p>
<p>
<div><strong style="text-decoration:underline">math.acos</strong></div>
<div style="margin-bottom:1em"><code>math.acos(num):map:[deg]</code></div>
Returns an inverse cosine value.
</p>
<p>
<div><strong style="text-decoration:underline">math.asin</strong></div>
<div style="margin-bottom:1em"><code>math.asin(num):map:[deg]</code></div>
Returns an inverse sine value.
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
<div><strong style="text-decoration:underline">math.ceil</strong></div>
<div style="margin-bottom:1em"><code>math.ceil(num):map</code></div>
Returns a nearest integer number above or equal to the specified value.
</p>
<p>
<div><strong style="text-decoration:underline">math.cos</strong></div>
<div style="margin-bottom:1em"><code>math.cos(num):map:[deg]</code></div>
Returns a cosine value.
</p>
<p>
<div><strong style="text-decoration:underline">math.cosh</strong></div>
<div style="margin-bottom:1em"><code>math.cosh(num):map</code></div>
Returns a hyperbolic cosine value.
</p>
<p>
<div><strong style="text-decoration:underline">math.exp</strong></div>
<div style="margin-bottom:1em"><code>math.exp(num):map</code></div>
Returns an exponential value.
</p>
<p>
<div><strong style="text-decoration:underline">math.abs</strong></div>
<div style="margin-bottom:1em"><code>math.abs(num):map</code></div>
Returns an absolute value.
</p>
<p>
<div><strong style="text-decoration:underline">math.floor</strong></div>
<div style="margin-bottom:1em"><code>math.floor(num):map</code></div>
Returns a nearest integer number below or equal to the specified value.
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
<div><strong style="text-decoration:underline">math.sin</strong></div>
<div style="margin-bottom:1em"><code>math.sin(num):map:[deg]</code></div>
Returns a sine value.
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
<div><strong style="text-decoration:underline">math.tanh</strong></div>
<div style="margin-bottom:1em"><code>math.tanh(num):map</code></div>
Returns a hyperbolic tangent value.
</p>
<p>
<div><strong style="text-decoration:underline">math.hypot</strong></div>
<div style="margin-bottom:1em"><code>math.hypot(x, y):map</code></div>
Returns a hyperbolic tangent value.
</p>
<p>
<div><strong style="text-decoration:underline">math.least_square</strong></div>
<div style="margin-bottom:1em"><code>math.least_square(x:iterator, y:iterator, dim:number =&gt; 1, var:symbol =&gt; `x)</code></div>
Calculates a least square method using a sequence of pairs of <code>x</code> and <code>y</code>, and returns an expression of the fitted curve. You can specify the dimension by an argument <code>dim</code>. In default, a symbol of the expression's variable is <code>x</code>and it can be changed by specifying an argument <code>var</code>.
</p>
<p>
<div><strong style="text-decoration:underline">math.bezier</strong></div>
<div style="margin-bottom:1em"><code>math.bezier(nums[]+:number)</code></div>
Returns a list that consists of functions that generate coordinates of bezier curves with specified control points. One or more lists of control points can be specified. This means that if you give it two lists of numbers as arguments, it returns two functions of bezier curve.
</p>
<p>
<div><strong style="text-decoration:underline">math.diff</strong></div>
<div style="margin-bottom:1em"><code>math.diff(expr:expr, var:symbol):map {block?}</code></div>
Returns a mathematical differential expression of the given <code>expr</code> by a variable <code>var</code>.
</p>
<p>
Example: <code>math.diff(</code>(math.sin(x 2)), <code>x)</code>**
</p>
<p>
<div><strong style="text-decoration:underline">math.optimize</strong></div>
<div style="margin-bottom:1em"><code>math.optimize(expr:expr):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.fft</strong></div>
<div style="margin-bottom:1em"><code>math.fft(seq[])</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.dot_product</strong></div>
<div style="margin-bottom:1em"><code>math.dot_product(a[], b[])</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.cross_product</strong></div>
<div style="margin-bottom:1em"><code>math.cross_product(a[], b[])</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.covariance</strong></div>
<div style="margin-bottom:1em"><code>math.covariance(a:iterator, b:iterator)</code></div>
Returns a covariance between the sequences of values.
</p>
<p>
<div><strong style="text-decoration:underline">math.integral</strong></div>
<div style="margin-bottom:1em"><code>math.integral()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">math.gcd</strong></div>
<div style="margin-bottom:1em"><code>math.gcd(a:number, b+:number):map</code></div>
Returns a greatest common divisor among two or more numbers.
</p>
<p>
<div><strong style="text-decoration:underline">math.lcm</strong></div>
<div style="margin-bottom:1em"><code>math.lcm(a:number, b+:number):map</code></div>
Returns a least common multiple among two or more numbers.
</p>
<p />

{% endraw %}
