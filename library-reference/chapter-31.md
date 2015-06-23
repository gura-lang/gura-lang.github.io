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
<strong>math.real</strong>
</p>
<p>
<code>math.real(num):map</code>
</p>
<p>
Returns a real part of a complex number.
</p>
<p>
<strong>math.imag</strong>
</p>
<p>
<code>math.imag(num):map</code>
</p>
<p>
Returns an imaginary part of a complex number.
</p>
<p>
<strong>math.arg</strong>
</p>
<p>
<code>math.arg(num):map:[deg]</code>
</p>
<p>
Returns an argument value of a complex number in radian.
</p>
<p>
<strong>math.norm</strong>
</p>
<p>
<code>math.norm(num):map</code>
</p>
<p>
Returns a norm value of a complex number.
</p>
<p>
<strong>math.conj</strong>
</p>
<p>
<code>math.conj(num):map</code>
</p>
<p>
Returns a conjugate of a complex number.
</p>
<p>
<strong>math.acos</strong>
</p>
<p>
<code>math.acos(num):map:[deg]</code>
</p>
<p>
Returns an inverse cosine value.
</p>
<p>
<strong>math.asin</strong>
</p>
<p>
<code>math.asin(num):map:[deg]</code>
</p>
<p>
Returns an inverse sine value.
</p>
<p>
<strong>math.atan</strong>
</p>
<p>
<code>math.atan(num):map:[deg]</code>
</p>
<p>
Returns an inverse tangent value.
</p>
<p>
<strong>math.atan2</strong>
</p>
<p>
<code>math.atan2(num1, num2):map:[deg]</code>
</p>
<p>
Returns an inverse tangent value of a fraction of num1 and num2.
</p>
<p>
<strong>math.ceil</strong>
</p>
<p>
<code>math.ceil(num):map</code>
</p>
<p>
Returns a nearest integer number above or equal to the specified value.
</p>
<p>
<strong>math.cos</strong>
</p>
<p>
<code>math.cos(num):map:[deg]</code>
</p>
<p>
Returns a cosine value.
</p>
<p>
<strong>math.cosh</strong>
</p>
<p>
<code>math.cosh(num):map</code>
</p>
<p>
Returns a hyperbolic cosine value.
</p>
<p>
<strong>math.exp</strong>
</p>
<p>
<code>math.exp(num):map</code>
</p>
<p>
Returns an exponential value.
</p>
<p>
<strong>math.abs</strong>
</p>
<p>
<code>math.abs(num):map</code>
</p>
<p>
Returns an absolute value.
</p>
<p>
<strong>math.floor</strong>
</p>
<p>
<code>math.floor(num):map</code>
</p>
<p>
Returns a nearest integer number below or equal to the specified value.
</p>
<p>
<strong>math.log</strong>
</p>
<p>
<code>math.log(num):map</code>
</p>
<p>
Returns a natural logarithm value.
</p>
<p>
<strong>math.log10</strong>
</p>
<p>
<code>math.log10(num):map</code>
</p>
<p>
Returns a decadic logarithm value.
</p>
<p>
<strong>math.sin</strong>
</p>
<p>
<code>math.sin(num):map:[deg]</code>
</p>
<p>
Returns a sine value.
</p>
<p>
<strong>math.sinh</strong>
</p>
<p>
<code>math.sinh(num):map</code>
</p>
<p>
Returns a hyperbolic sine value.
</p>
<p>
<strong>math.sqrt</strong>
</p>
<p>
<code>math.sqrt(num):map</code>
</p>
<p>
Returns a square root value.
</p>
<p>
<strong>math.tan</strong>
</p>
<p>
<code>math.tan(num):map:[deg]</code>
</p>
<p>
Returns a tangent value.
</p>
<p>
<strong>math.tanh</strong>
</p>
<p>
<code>math.tanh(num):map</code>
</p>
<p>
Returns a hyperbolic tangent value.
</p>
<p>
<strong>math.hypot</strong>
</p>
<p>
<code>math.hypot(x, y):map</code>
</p>
<p>
Returns a hyperbolic tangent value.
</p>
<p>
<strong>math.least_square</strong>
</p>
<p>
<code>math.least_square(x:iterator, y:iterator, dim:number =&gt; 1, var:symbol =&gt; `x)</code>
</p>
<p>
Calculates a least square method using a sequence of pairs of <code>x</code> and <code>y</code>, and returns an expression of the fitted curve. You can specify the dimension by an argument <code>dim</code>. In default, a symbol of the expression's variable is <code>x</code>and it can be changed by specifying an argument <code>var</code>.
</p>
<p>
<strong>math.bezier</strong>
</p>
<p>
<code>math.bezier(nums[]+:number)</code>
</p>
<p>
Returns a list that consists of functions that generate coordinates of bezier curves with specified control points. One or more lists of control points can be specified. This means that if you give it two lists of numbers as arguments, it returns two functions of bezier curve.
</p>
<p>
<strong>math.diff</strong>
</p>
<p>
<code>math.diff(expr:expr, var:symbol):map {block?}</code>
</p>
<p>
Returns a mathematical differential expression of the given <code>expr</code> by a variable <code>var</code>.
</p>
<p>
Example: <code>math.diff(</code>(math.sin(x 2)), <code>x)</code>**
</p>
<p>
<strong>math.optimize</strong>
</p>
<p>
<code>math.optimize(expr:expr):map {block?}</code>
</p>
<p>
<strong>math.fft</strong>
</p>
<p>
<code>math.fft(seq[])</code>
</p>
<p>
<strong>math.dot_product</strong>
</p>
<p>
<code>math.dot_product(a[], b[])</code>
</p>
<p>
<strong>math.cross_product</strong>
</p>
<p>
<code>math.cross_product(a[], b[])</code>
</p>
<p>
<strong>math.covariance</strong>
</p>
<p>
<code>math.covariance(a:iterator, b:iterator)</code>
</p>
<p>
Returns a covariance between the sequences of values.
</p>
<p>
<strong>math.integral</strong>
</p>
<p>
<code>math.integral()</code>
</p>
<p>
<strong>math.gcd</strong>
</p>
<p>
<code>math.gcd(a:number, b+:number):map</code>
</p>
<p>
Returns a greatest common divisor among two or more numbers.
</p>
<p>
<strong>math.lcm</strong>
</p>
<p>
<code>math.lcm(a:number, b+:number):map</code>
</p>
<p>
Returns a least common multiple among two or more numbers.
</p>
<p />

{% endraw %}
