---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">5</span><a name="anchor-5"></a>Built-in Class</h1>
<h2><span class="caption-index-2">5.1</span><a name="anchor-5-1"></a>argument Class</h2>
<h3><span class="caption-index-3">5.1.1</span><a name="anchor-5-1-1"></a>Overview</h3>
<p>
The <code>argument</code> class provides measures to access argument information that is passed to a function. One of its purposes is to check if an attribute is specified in the function call. It also provides a method to control a leader-trailer sequence, a mechanism that flow controls such as <code>if-elsif-else</code> and <code>try-catch</code> utilize.
</p>
<p>
There's no constructor to realize an instance of <code>argument</code> class. Its instance is implicitly created when a function is called, and you can refer to it by a variable named <code>__arg__</code>.
</p>
<p>
Below is an example to use <code>argument</code> class:
</p>
<pre><code>func(v0, v1, v2):[attr1,attr2] = {
    printf('arg#%d %s\n', 0.., __arg__.values)
    printf('attr1:%s attr2:%s\n', __arg__.isset(`attr1), __arg__.isset(`attr2))
}
</code></pre>
<h3><span class="caption-index-3">5.1.2</span><a name="anchor-5-1-2"></a>Property</h3>
<p>
An <code>argument</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>function</code></td>
<td>
<code>function</code></td>
<td>
R</td>

<td>
The <code>function</code> instance that has created the argument.</td>
</tr>

<tr>
<td>
<code>values</code></td>
<td>
<code>function</code></td>
<td>
R</td>

<td>
A list of argument values.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.1.3</span><a name="anchor-5-1-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">argument#finalize_trailer</strong></div>
<div style="margin-bottom:1em"><code>argument#finalize_trailer():void</code></div>
Signals finalizing status to trailers after the current function.
</p>
<p>
<div><strong style="text-decoration:underline">argument#isset</strong></div>
<div style="margin-bottom:1em"><code>argument#isset(symbol:symbol)</code></div>
Returns <code>true</code> if the function is called with an attribute that matches the specified symbol.
</p>
<p>
<div><strong style="text-decoration:underline">argument#quit_trailer</strong></div>
<div style="margin-bottom:1em"><code>argument#quit_trailer():void</code></div>
Cancels evaluation of following trailers.
</p>
<p>
Example:
</p>
<pre><code>f(flag:boolean) = {
    !flag &amp;&amp; __arg__.quit_trailer() 
}

f(true) println('printed')
f(false) println('not printed')
</code></pre>
<h2><span class="caption-index-2">5.2</span><a name="anchor-5-2"></a>array Class</h2>
<h3><span class="caption-index-3">5.2.1</span><a name="anchor-5-2-1"></a>Overview</h3>
<p>
An instance of the <code>array</code> class stores multiple numeric values in a seamless binary sequence. It can directly be passed to functions in C libraries without any modification that expect arrays of <code>char</code>, <code>short</code>, <code>int</code>, <code>float</code>, <code>double</code> and so on.
</p>
<p>
There are several <code>array</code> classes that deal with different element types as shown below:
</p>
<p>
<table>
<tr>
<th>
Class Name</th>
<th>
Element Type</th>
</tr>

<tr>
<td>
<code>array@int8</code></td>
<td>
<code>Int8</code></td>
</tr>

<tr>
<td>
<code>array@uint8</code></td>
<td>
<code>Uint8</code></td>
</tr>

<tr>
<td>
<code>array@int16</code></td>
<td>
<code>Int16</code></td>
</tr>

<tr>
<td>
<code>array@uint16</code></td>
<td>
<code>Uint16</code></td>
</tr>

<tr>
<td>
<code>array@int32</code></td>
<td>
<code>Int32</code></td>
</tr>

<tr>
<td>
<code>array@uint32</code></td>
<td>
<code>Uint32</code></td>
</tr>

<tr>
<td>
<code>array@int64</code></td>
<td>
<code>Int64</code></td>
</tr>

<tr>
<td>
<code>array@uint64</code></td>
<td>
<code>Uint64</code></td>
</tr>

<tr>
<td>
<code>array@half</code></td>
<td>
<code>Half</code></td>
</tr>

<tr>
<td>
<code>array@float</code></td>
<td>
<code>Float</code></td>
</tr>

<tr>
<td>
<code>array@double</code></td>
<td>
<code>Double</code></td>
</tr>

<tr>
<td>
<code>array@complex</code></td>
<td>
<code>Complex</code></td>
</tr>

</table>

</p>
<p>
In the specification described here, the class name is is represented as <code>array@T</code> where <code>T</code> means its element type.
</p>
<p>
Most of methods in <code>array</code> class are implemented in <code>arrayt</code> module while the class itself is provided by the intepreter. This is because array features cost much code size and it would be preferable to reduce the size of the intepreter body by separating the implementation of array methods. So, you have to import <code>arrayt</code> module before using the <code>array</code> class in your program.
</p>
<h3><span class="caption-index-3">5.2.2</span><a name="anchor-5-2-2"></a>Property</h3>
<p>
An <code>array</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>T</code></td>
<td>
<code>array</code></td>
<td>
R</td>

<td>
Return an array with its row and column being tranposed.</td>
</tr>

<tr>
<td>
<code>elembytes</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the size of each element in bytes.</td>
</tr>

<tr>
<td>
<code>elemtype</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Returns the type name of the elements as a <code>symbol</code> including: <code>`boolean</code>, <code>`int8</code>, <code>`uint8</code>, <code>`int16</code>, <code>`uint16</code>, <code>`int32</code>, <code>`uint32</code>, <code>`int64</code>, <code>`uint64</code>, <code>`half</code>, <code>`float</code>, <code>`double</code> and <code>`complex</code>.</td>
</tr>

<tr>
<td>
<code>major</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Returns the major-mode in symbols <code>`row</code> or <code>`column</code>.</td>
</tr>

<tr>
<td>
<code>memoryid</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Returns the id of memory.</td>
</tr>

<tr>
<td>
<code>ndim</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the number of dimensions.</td>
</tr>

<tr>
<td>
<code>p</code></td>
<td>
<code>pointer</code></td>
<td>
R</td>

<td>
Returns the pointer through which you can inspect and modify the content of the array as a binary data.</td>
</tr>

<tr>
<td>
<code>shape</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns a list of sizes of each dimension.</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the total number of elements.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.2.3</span><a name="anchor-5-2-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">array</strong></div>
<div style="margin-bottom:1em"><code>array(src?, elemtype?:symbol) {block?}</code></div>
Creates an <code>array</code> instance that contains <code>double</code> type of elements from a <code>list</code> or an <code>iterator</code> specified as an argument <code>src</code> or from elements described in the block. The followings are examples to create an <code>array</code> instance:
</p>
<pre><code>array([[0, 1, 2], [3, 4, 5]])
array {{0, 1, 2}, {3, 4, 5}}
</code></pre>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The following examples create an <code>array</code> instance of <code>int32</code> elements:
</p>
<pre><code>array([[0, 1, 2], [3, 4, 5]], elemtype =&gt; `int32)
array(elemtype =&gt; `int32) {{0, 1, 2}, {3, 4, 5}}
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Functions named <code>array@T</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32 ([[0, 1, 2], [3, 4, 5]])
array@int32 {{0, 1, 2}, {3, 4, 5}}
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.identity</strong></div>
<div style="margin-bottom:1em"><code>array.identity(n:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an array of <code>double</code> type of elements that represents an identity matrix with specified size <code>n</code>.
</p>
<p>
Example:
</p>
<pre><code>x = array.identity(3)
// x is array@double {{1, 0, 0}, {0, 1, 0}, {0, 0, 1}}
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>int32</code> elements:
</p>
<pre><code>array.identity(3, elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.identity</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32.identity(3)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.interval</strong></div>
<div style="margin-bottom:1em"><code>array.interval(begin:number, end:number, samples:number, elemtype?:symbol):static:map:[open,open_l,open_r] {block?}</code></div>
Creates a one-dimentional array with <code>double</code> type of element that contains a sequence of numbers according to the beginning, ending numbers and the number of samples between them.
</p>
<p>
In default, it creates a sequence with a range of <code>[begin, end]</code> meaning that the sequence contains the beginning and ending numbers. Following attributes would control the range:
</p>
<ul>
<li><code>:open</code> .. Numbers in range of <code>(begin, end)</code> that doesn't contain either <code>begin</code> or <code>end</code>.</li>
<li><code>:open_l</code> .. Numbers in range of <code>(begin, end]</code> that doesn't contain <code>begin</code>.</li>
<li><code>:open_r</code> .. Numbers in range of <code>[begin, end)</code> that doesn't contain <code>end</code>.</li>
</ul>
<p>
Example:
</p>
<pre><code>x = array.interval(0, 3, 7)
// x is array@double {0, 0.5, 1, 1.5, 2, 2.5, 3}
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.interval(0, 3, 7, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.interval</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.interval(0, 3, 7)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.ones</strong></div>
<div style="margin-bottom:1em"><code>array.ones(dims[]:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an array of <code>double</code> type of elements, which are initialized with one. The argument <code>dims</code> specifies the dimension of the created array.
</p>
<p>
Example:
</p>
<pre><code>x = array.ones([3, 4])
// x is array@double {{1, 1, 1, 1}, {1, 1, 1, 1}, {1, 1, 1, 1}}
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>int32</code> elements:
</p>
<pre><code>array.ones([3, 4], elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.ones</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32.ones([3, 4])
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.rands</strong></div>
<div style="margin-bottom:1em"><code>array.rands(dims[]:number, range?:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an array of <code>double</code> type of elements which are initialized with random numbers. The argument <code>dims</code> specifies the dimension of the created array. When the argument <code>range</code> is specified, the generated elements are all integer numbers that are ranged within <code>[0, range)</code>. Otherwise, the generated elements are real numbers ranged within <code>[0, 1)</code>.
</p>
<p>
Example:
</p>
<pre><code>x = array.rands([3, 4], 10)
// x is like array@double {{6, 7, 6, 9}, {3, 3, 6, 0}, {7, 9, 5, 5}}
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>int32</code> elements:
</p>
<pre><code>array.rands([3, 4], 10, elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.rands</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32.rands([3, 4], 10)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.rands@normal</strong></div>
<div style="margin-bottom:1em"><code>array.rands@normal(dims[]:number, mu?:number, sigma?:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an array of <code>double</code> type of elements which are initialized with normal distribution random numbers. The argument <code>dims</code> specifies the dimension of the created array. The arguments <code>mu</code> and <code>sigma</code> supply parameters for normal distribution where <code>mu</code> specifies the mean value and <code>sigma</code> the standard deviation. In default, the <code>mu</code> is zero and <code>sigma</code> one.
</p>
<p>
Example:
</p>
<pre><code>x = array.rands@normal([3, 4], 1, 3)
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.rands@normal([3, 4], 1, 3, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.rands@normal</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32.rands@normal([3, 4], 1, 3)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.range</strong></div>
<div style="margin-bottom:1em"><code>array.range(num:number, num_end?:number, step?:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an array of <code>double</code> type of elements that are initialized with a sequence of integer numbers.
</p>
<p>
This function can generate three types of sequence like below:
</p>
<ul>
<li><code>array.range(num)</code> .. between <code>0</code> and <code>(num - 1)</code>.</li>
<li><code>array.range(num, num_end)</code> .. between <code>num</code> and <code>(num_end - 1)</code>.</li>
<li><code>array.range(num, num_end, step)</code> .. between <code>num</code> and <code>(num_end - 1)</code> incremented by <code>step</code>.</li>
</ul>
<p>
Example:
</p>
<pre><code>x = array.range(5)
// x is array@double {0, 1, 2, 3, 4}
x = array.range(2, 5)
// x is array@double {2, 3, 4}
x = array.range(2, 10, 2)
// x is array@double {2, 4, 6, 8}
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>int32</code> elements:
</p>
<pre><code>array.range(5, elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.range</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32.range(5)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.rotation</strong></div>
<div style="margin-bottom:1em"><code>array.rotation(angle:number, xtrans?:number, ytrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
Creates an <code>array</code> of <code>double</code> type of elements representing a matrix to rotate a 2-D coord.
</p>
<p>
The rotation <code>angle</code> is specified in radian value. If the attribute <code>:deg</code> is specified, the <code>angle</code> is specified in degree value.
</p>
<p>
If one or both of <code>xtrans</code> and <code>ytrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre><code>x = array.rotation(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation(math.pi / 6, 3, 5)
// x is a matrix to rotate by pi/6 and translate by [3, 5].
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.rotation(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.rotation</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.rotation(math.pi / 6)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.rotation@x</strong></div>
<div style="margin-bottom:1em"><code>array.rotation@x(angle:number, xtrans?:number, ytrans?:number, ztrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
Creates an <code>array</code> of <code>double</code> type of elements representing a matrix to rotate a 3-D coord around x-axis.
</p>
<p>
The rotation <code>angle</code> is specified in radian value. If the attribute <code>:deg</code> is specified, the <code>angle</code> is specified in degree value.
</p>
<p>
If one or more of <code>xtrans</code>, <code>ytrans</code> and <code>ztrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre><code>x = array.rotation@x(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation@x(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation@x(math.pi / 6, 3, -2, 5)
// x is a matrix to rotate by pi/6 and translate by [3, -2, 5].
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.rotation@x(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.rotation@x</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.rotation@x(math.pi / 6)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.rotation@y</strong></div>
<div style="margin-bottom:1em"><code>array.rotation@y(angle:number, xtrans?:number, ytrans?:number, ztrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
Creates an <code>array</code> of <code>double</code> type of elements representing a matrix to rotate a 3-D coord around y-axis.
</p>
<p>
The rotation <code>angle</code> is specified in radian value. If the attribute <code>:deg</code> is specified, the <code>angle</code> is specified in degree value.
</p>
<p>
If one or more of <code>xtrans</code>, <code>ytrans</code> and <code>ztrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre><code>x = array.rotation@y(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation@y(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation@y(math.pi / 6, 3, -2, 5)
// x is a matrix to rotate by pi/6 and translate by [3, -2, 5].
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.rotation@y(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.rotation@y</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.rotation@y(math.pi / 6)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.rotation@z</strong></div>
<div style="margin-bottom:1em"><code>array.rotation@z(angle:number, xtrans?:number, ytrans?:number, ztrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
Creates an <code>array</code> of <code>double</code> type of elements representing a matrix to rotate a 3-D coord around z-axis.
</p>
<p>
The rotation <code>angle</code> is specified in radian value. If the attribute <code>:deg</code> is specified, the <code>angle</code> is specified in degree value.
</p>
<p>
If one or more of <code>xtrans</code>, <code>ytrans</code> and <code>ztrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre><code>x = array.rotation@z(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation@z(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation@z(math.pi / 6, 3, -2, 5)
// x is a matrix to rotate by pi/6 and translate by [3, -2, 5].
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.rotation@z(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.rotation@z</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.rotation@z(math.pi / 6)
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.scaling</strong></div>
<div style="margin-bottom:1em"><code>array.scaling(xscale:number, yscale:number, zscale?:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an <code>array</code> of <code>double</code> type of elements representing a matrix to scale a coord.
</p>
<p>
It creates a matrix that works on a 2-D coord if <code>xscale</code> and <code>yscale</code> are specified while it creates a matrix on a 3-D coord if <code>xscale</code>, <code>yscale</code> and <code>zscale</code> are specified.
</p>
<p>
Example:
</p>
<pre><code>x = array.scaling(3, 4)
// x is a matrix to scale a 2-D coord by [3, 4].
x = array.scaling(3, 4, -2)
// x is a matrix to scale a 3-D coord by [3, 4, -2].
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.scaling(3, 4, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.scaling</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.scaling(3, 4
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.translation</strong></div>
<div style="margin-bottom:1em"><code>array.translation(xtrans:number, ytrans:number, ztrans?:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an <code>array</code> of <code>double</code> type of elements representing a matrix to translate a coord.
</p>
<p>
It creates a matrix that works on a 2-D coord if <code>xtrans</code> and <code>ytrans</code> are specified while it creates a matrix on a 3-D coord if <code>xtrans</code>, <code>ytrans</code> and <code>ztrans</code> are specified.
</p>
<p>
Example:
</p>
<pre><code>x = array.translation(3, 4)
// x is a matrix to translate a 2-D coord by [3, 4].
x = array.translation(3, 4, -2)
// x is a matrix to translate a 3-D coord by [3, 4, -2].
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>float</code> elements:
</p>
<pre><code>array.translation(3, 4, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.translation</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@float.translation(3, 4
</code></pre>
<p>
<div><strong style="text-decoration:underline">array.zeros</strong></div>
<div style="margin-bottom:1em"><code>array.zeros(dims[]:number, elemtype?:symbol):static:map {block?}</code></div>
Creates an array of <code>double</code> type of elements, which are initialized with zero. The argument <code>dims</code> specifies the dimension of the created array.
</p>
<p>
Example:
</p>
<pre><code>x = array.zeros([3, 4])
// x is array@double {{0, 0, 0, 0}, {0, 0, 0, 0}, {0, 0, 0, 0}}
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code>elemtype</code> would create an array of element type other than <code>double</code>. The followings examples create an <code>array</code> instance of <code>int32</code> elements:
</p>
<pre><code>array.zeros([3, 4], elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code>array@T.zeros</code> where <code>T</code> gets an element type name are also provided to create an <code>array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre><code>array@int32.zeros([3, 4])
</code></pre>
<h3><span class="caption-index-3">5.2.4</span><a name="anchor-5-2-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">array#argmax</strong></div>
<div style="margin-bottom:1em"><code>array#argmax(axis?:number):map:[last_index] {block?}</code></div>
Returns index of a maximum number of elements in the target <code>array</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array#argmin</strong></div>
<div style="margin-bottom:1em"><code>array#argmin(axis?:number):map:[last_index] {block?}</code></div>
Returns index of a minimum number of elements in the target <code>array</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array.dot</strong></div>
<div style="margin-bottom:1em"><code>array.dot(a:array, b:array):static:map {block?}</code></div>
Calculates a dot product between two arrays that have one or two dimensions.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#dump</strong></div>
<div style="margin-bottom:1em"><code>array#dump(stream?:stream):void:[upper]</code></div>
Prints out a binary dump of the array's content.
</p>
<p>
<div><strong style="text-decoration:underline">array#each</strong></div>
<div style="margin-bottom:1em"><code>array#each():[flat] {block?}</code></div>
Creates an iterator that iterates each element in the array.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
The block parameter is <code>|elem:number, idx:number|</code> where <code>elem</code> is the element value.
</p>
<p>
<div><strong style="text-decoration:underline">array#elemcast</strong></div>
<div style="margin-bottom:1em"><code>array#elemcast(elemtype:symbol) {block?}</code></div>
Cast value type of contained elements.
</p>
<p>
Available symbols for <code>elemtype</code> are as follows:
</p>
<ul>
<li><code>`boolean</code></li>
<li><code>`int8</code></li>
<li><code>`uint8</code></li>
<li><code>`int16</code></li>
<li><code>`uint16</code></li>
<li><code>`int32</code></li>
<li><code>`uint32</code></li>
<li><code>`int64</code></li>
<li><code>`uint64</code></li>
<li><code>`half</code></li>
<li><code>`float</code></li>
<li><code>`double</code></li>
<li><code>`complex</code></li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#fill</strong></div>
<div style="margin-bottom:1em"><code>array#fill(value:number):void</code></div>
Fills array with a specified value.
</p>
<p>
<div><strong style="text-decoration:underline">array#flatten</strong></div>
<div style="margin-bottom:1em"><code>array#flatten() {block?}</code></div>
Returns an <code>array</code> instance as a result that has flattened elements in the target <code>array</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#head</strong></div>
<div style="margin-bottom:1em"><code>array#head(n:number):map {block?}</code></div>
Returns an <code>array</code> instance as a result that has extracted <code>n</code> elements from the beginning of the target <code>array</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#invert</strong></div>
<div style="margin-bottom:1em"><code>array#invert(eps?:number) {block?}</code></div>
Returns an <code>array</code> instance as a result that has elements of inverted matrix of the target <code>array</code>. If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#iselemsame</strong></div>
<div style="margin-bottom:1em"><code>array#iselemsame(array:array)</code></div>
Returns <code>true</code> if the target <code>array</code> instance has the same elements with the specified <code>array</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array#issquare</strong></div>
<div style="margin-bottom:1em"><code>array#issquare()</code></div>
Returns <code>true</code> if the target <code>array</code> consists square matrices.
</p>
<p>
<div><strong style="text-decoration:underline">array#max</strong></div>
<div style="margin-bottom:1em"><code>array#max(axis?:number):map:[index,last_index] {block?}</code></div>
Finds a maximum number of elements in the target <code>array</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array#mean</strong></div>
<div style="margin-bottom:1em"><code>array#mean(axis?:number):map {block?}</code></div>
Calculates an mean value of elements in the array.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#min</strong></div>
<div style="margin-bottom:1em"><code>array#min(axis?:number):map:[index,last_index] {block?}</code></div>
Finds a minimum number of elements in the target <code>array</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array#offset</strong></div>
<div style="margin-bottom:1em"><code>array#offset(n:number):map {block?}</code></div>
Returns an <code>array</code> instance as a result that has extracted elements of the target <code>array</code> after skipping its first <code>n</code> elements.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#paste</strong></div>
<div style="margin-bottom:1em"><code>array#paste(offset:number, src:array):map</code></div>
Pastes elements of <code>src</code> into the target <code>array</code> instance.
</p>
<p>
The argument <code>offset</code> specifies the posision where elements are pasted in
</p>
<p>
<div><strong style="text-decoration:underline">array#reshape</strong></div>
<div style="margin-bottom:1em"><code>array#reshape(dims[]:number:nil) {block?}</code></div>
Returns an <code>array</code> instance as a result that has reshaped the target <code>array</code> according to a list of dimension size specified by <code>dims</code>.
</p>
<p>
Below are examples:
</p>
<pre><code>x = array(1..24)
a = x.reshape([6, 4])    // a is an array of 6x4.
b = x.reshape([2, 3, 4]) // b is an array of 2x3x4.
</code></pre>
<p>
A value of <code>nil</code> in the list of dimension means it would be calculated from the whole size and other dimension sizes. Only one <code>nil</code> is allowed to exist.
</p>
<pre><code>x = array(1..24)
b = x.reshape([2, nil, 4]) // b is an array of 2x3x4.
</code></pre>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#roundoff</strong></div>
<div style="margin-bottom:1em"><code>array#roundoff(threshold?:number) {block?}</code></div>
Returns an <code>array</code> instance as a result that has rounded off elements less than <code>threshold</code> to zero in the target <code>array</code>. The default value for <code>threshold</code> is <code>1.0e-6</code> when omitted.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#std</strong></div>
<div style="margin-bottom:1em"><code>array#std(axis?:number):map:[p] {block?}</code></div>
Calculates a standard deviation value of elements in the target <code>array</code>.
</p>
<p>
In default, it calculates an unbiased estimation of standard deviation in which the summation of squared deviations is divided by <code>(n - 1)</code>. Specifying <code>:p</code> attributes will calculate a population variance that divides that summation by <code>n</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array#sum</strong></div>
<div style="margin-bottom:1em"><code>array#sum(axis?:number):map {block?}</code></div>
Calculates a summation value of elements in the target <code>array</code>.
</p>
<p>
<div><strong style="text-decoration:underline">array#tail</strong></div>
<div style="margin-bottom:1em"><code>array#tail(n:number):map {block?}</code></div>
Returns an <code>array</code> instance as a result that has extracted <code>n</code> elements from the bottom of the target <code>array</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#transpose</strong></div>
<div style="margin-bottom:1em"><code>array#transpose(axes[]?:number) {block?}</code></div>
Creates an array instance that transposes axes of the original array according to the specified argument <code>axes</code>.
</p>
<p>
If the argument is not specified, two axes at the lowest rank, which correspond to row and column for a matrix, would be transposed.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|array:array|</code>, where <code>array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">array#var</strong></div>
<div style="margin-bottom:1em"><code>array#var(axis?:number):map:[p] {block?}</code></div>
Calculates a variation value of elements in the target <code>array</code>.
</p>
<p>
In default, it calculates an unbiased estimation of standard deviation in which the summation of squared deviations is divided by <code>(n - 1)</code>. Specifying <code>:p</code> attributes will calculate a population variance that divides that summation by <code>n</code>.
</p>
<h2><span class="caption-index-2">5.3</span><a name="anchor-5-3"></a>audio Class</h2>
<h3><span class="caption-index-3">5.3.1</span><a name="anchor-5-3-1"></a>Overview</h3>
<p>
The <code>audio</code> class provides measures to work on audio data.
</p>
<h3><span class="caption-index-3">5.3.2</span><a name="anchor-5-3-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">audio#each</strong></div>
<div style="margin-bottom:1em"><code>audio#each(channel:number, offset?:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">audio#get</strong></div>
<div style="margin-bottom:1em"><code>audio#get(channel:number, offset:number):map</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">audio#put</strong></div>
<div style="margin-bottom:1em"><code>audio#put(channel:number, offset:number, data:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">audio#sinewave</strong></div>
<div style="margin-bottom:1em"><code>audio#sinewave(channel:number, freq:number, len:number, amplitude?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">audio#store</strong></div>
<div style="margin-bottom:1em"><code>audio#store(channel:number, offset:number, data:iterator):reduce</code></div>

</p>
<h2><span class="caption-index-2">5.4</span><a name="anchor-5-4"></a>binary Class</h2>
<h3><span class="caption-index-3">5.4.1</span><a name="anchor-5-4-1"></a>Overview</h3>
<p>
The <code>binary</code> class provides measures to work on binary data that is a byte sequence without any format.
</p>
<p>
You can create a <code>binary</code> instance by calling <code>binary()</code> function.
</p>
<p>
You can also create the instance by specifying <code>b</code> prefix before a string literal. For example, the code below creates a <code>binary</code> instance that contains a sequence <code>0x41, 0x42, 0xfe, 0x03, 0x43, 0x44</code>.
</p>
<pre><code>b'AB\xfe\x03CD'
</code></pre>
<h3><span class="caption-index-3">5.4.2</span><a name="anchor-5-4-2"></a>Property</h3>
<p>
A <code>binary</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>p</code></td>
<td>
<code>pointer</code></td>
<td>
R</td>

<td>
Returns a <code>pointer</code> instance that accesses the binary. This result is equivalent to that of calling the method <code>binary#pointer()</code></td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the binary size in bytes.</td>
</tr>

<tr>
<td>
<code>writable</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
Indicates if the content of the binary object is writable.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.4.3</span><a name="anchor-5-4-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">binary</strong></div>
<div style="margin-bottom:1em"><code>binary(buff*) {block?}</code></div>
Creates a <code>binary</code> instance after combining <code>string</code> or <code>binary</code> specified by the arguments <code>buff</code>. If no argument is specified for <code>buff</code>, an empty <code>binary</code> instance would be created.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|bin:binary|</code>, where <code>bin</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.4.4</span><a name="anchor-5-4-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">binary.alloc</strong></div>
<div style="margin-bottom:1em"><code>binary.alloc(bytes:number, data?:number):static:map {block?}</code></div>
Creates a <code>binary</code> instance that has the specified size of buffer. If the argument <code>data</code>, which should have a number between 0 and 255, is specified, the buffer would be initialized with the value.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|bin:binary|</code>, where <code>bin</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">binary#dump</strong></div>
<div style="margin-bottom:1em"><code>binary#dump(stream?:stream:w):void:[upper]</code></div>
Prints a hexadecimal dump from the content of the <code>binary</code> to the standard output. If the argument <code>stream</code> is specified, the result would be output to the stream.
</p>
<p>
In default, hexadecimal digit are printed with lower-case characters. Specifying an attribute <code>:upper</code> would output them with upper-case characters instead.
</p>
<p>
Example:
</p>
<pre><code>&gt;&gt;&gt; b'A quick brown fox jumps over the lazy dog.'.dump():upper
41 20 71 75 69 63 6B 20 62 72 6F 77 6E 20 66 6F  A quick brown fo
78 20 6A 75 6D 70 73 20 6F 76 65 72 20 74 68 65  x jumps over the
20 6C 61 7A 79 20 64 6F 67 2E                     lazy dog.
</code></pre>
<p>
<div><strong style="text-decoration:underline">binary#pointer</strong></div>
<div style="margin-bottom:1em"><code>binary#pointer(offset?:number):map {block?}</code></div>
Returns a <code>pointer</code> instance that has an initial offset specified by the argument <code>offset</code>. If the argument is omitted, it would return a <code>pointer</code> instance that points to the top of the binary.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|p:pointer|</code>, where <code>p</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">binary#reader</strong></div>
<div style="margin-bottom:1em"><code>binary#reader() {block?}</code></div>
Creates a <code>stream</code> instance with which you can read data from the binary by <code>stream#read()</code> method. If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">binary#writer</strong></div>
<div style="margin-bottom:1em"><code>binary#writer() {block?}</code></div>
Creates a <code>stream</code> instance with which you can append data to the binary by <code>stream#write()</code> method. If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">5.5</span><a name="anchor-5-5"></a>boolean Class</h2>
<h3><span class="caption-index-3">5.5.1</span><a name="anchor-5-5-1"></a>Overview</h3>
<p>
The <code>boolean</code> class represents a boolean data type that is used in logical operations including NOT, AND, OR and XOR.
</p>
<p>
The <code>boolean</code> type provides two values: <code>true</code> and <code>false</code>. The other types of values can also be calculated in logical operations according to the following general rule:
</p>
<ul>
<li>The <code>nil</code> value is evaluated as <code>false</code> value.</li>
<li>Other values are evaluated as <code>true</code>.</li>
</ul>
<p>
Note that the number <code>0</code> is treated as <code>true</code> in logical operations. 
</p>
<h2><span class="caption-index-2">5.6</span><a name="anchor-5-6"></a>codec Class</h2>
<h3><span class="caption-index-3">5.6.1</span><a name="anchor-5-6-1"></a>Overview</h3>
<p>
The <code>codec</code> class has features to decoding/encoding character codes stored in <code>string</code> and <code>binary</code>. Following measures are provided:
</p>
<ul>
<li>Decode .. Converts specific character codes stored in <code>binary</code> into UTF-8 code and generages <code>string</code> containing the result. It can also delete a CR code (<code>0x0d</code>) before a LF code (<code>0x0d</code>) at each end of line so that lines in the result are joined with LF code.</li>
<li>Encode .. Converts UTF-8 character codes stored in <code>string</code> into specific codes and generates <code>binary</code> containing the result. It can also add a CR code (<code>0x0d</code>) before a LF code (<code>0x0a</code>) at each end of line so that lines in the result are joined with CR-LF sequence.</li>
</ul>
<p>
You can utilize these functions using <code>codec</code> class's methods <code>codec#decode()</code> and <code>codec#encode()</code> as well as using <code>stream</code> class's method to read/write text by specifying <code>codec</code> instance when creating its instance.
</p>
<p>
The actual functions for encoding and decoding are provided by sub modules under <code>codecs</code> module. Each module provides following codecs:
</p>
<ul>
<li><code>codecs.basic</code> .. <code>us-ascii</code>, <code>utf-8</code>, <code>utf-16</code>, <code>utf-16le</code>, <code>utf-16be</code></li>
<li><code>codecs.iso8859</code>.. <code>iso-8859-1</code>, <code>iso-8859-2</code>, <code>iso-8859-3</code>, <code>iso-8859-4</code>, <code>iso-8859-5</code>, <code>iso-8859-6</code>, <code>iso-8859-7</code>, <code>iso-8859-8</code>, <code>iso-8859-9</code>, <code>iso-8859-10</code>, <code>iso-8859-11</code>, <code>iso-8859-13</code>, <code>iso-8859-14</code>, <code>iso-8859-15</code>, <code>iso-8859-16</code></li>
<li><code>codecs.korean</code> .. <code>cp949</code>, <code>euc-kr</code></li>
<li><code>codecs.chinese</code> .. <code>cp936</code>, <code>gb2312</code>, <code>gbk</code>, <code>cp950</code>, <code>big5</code></li>
<li><code>codecs.japanese</code> .. <code>euc-jp</code>, <code>cp932</code>, <code>shift_jis</code>, <code>ms_kanji</code>, <code>jis</code>, <code>iso-2022-jp</code></li>
</ul>
<p>
Importing other codec modules would expand available codecs. You can call <code>codecs.dir()</code> to get a list of codec names currently available.
</p>
<h3><span class="caption-index-3">5.6.2</span><a name="anchor-5-6-2"></a>Predefined Variable</h3>
<p>
<table>
<tr>
<th>
Variable</th>
<th>
Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>codec.bom@utf8</code></td>
<td>
<code>binary</code></td>

<td>
BOM for UTF-8: <code>b'\xef\xbb\xbf'</code></td>
</tr>


<tr>
<td>
<code>codec.bom@utf16le</code></td>
<td>
<code>binary</code></td>

<td>
BOM for UTF-16 little endian: <code>b'\xff\xfe'</code></td>
</tr>


<tr>
<td>
<code>codec.bom@utf16be</code></td>
<td>
<code>binary</code></td>

<td>
BOM for UTF-16 big endian: <code>b'\xfe\xff'</code></td>
</tr>


<tr>
<td>
<code>codec.bom@utf32le</code></td>
<td>
<code>binary</code></td>

<td>
BOM for UTF-32 little endian: <code>b'\xff\xfe\x00\x00'</code></td>
</tr>


<tr>
<td>
<code>codec.bom@utf32be</code></td>
<td>
<code>binary</code></td>

<td>
BOM for UTF-32 big endian: <code>b'\x00\x00\xfe\xff'</code></td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.6.3</span><a name="anchor-5-6-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">codec</strong></div>
<div style="margin-bottom:1em"><code>codec(encoding:string) {block?}</code></div>
Creates a <code>codec</code> instance of the specified encoding name. You can call <code>codecs.dir()</code> to get a list of available encoding names.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|codec:codec|</code>, where <code>codec</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.6.4</span><a name="anchor-5-6-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">codec#addcr</strong></div>
<div style="margin-bottom:1em"><code>codec#addcr(flag?:boolean):reduce</code></div>
The codec's encoder has a feature to add a CR code (<code>0x0d</code>) before a LF code (<code>0x0a</code>) so that the lines are joined with CR-LF codes in the encoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">codec#decode</strong></div>
<div style="margin-bottom:1em"><code>codec#decode(buff:binary):map</code></div>
Decodes a binary <code>buff</code> and returns the decoded result as <code>string</code>.
</p>
<p>
<div><strong style="text-decoration:underline">codec#delcr</strong></div>
<div style="margin-bottom:1em"><code>codec#delcr(flag?:boolean):reduce</code></div>
The codec's decoder has a feature to delete a CR code (<code>0x0d</code>) before a LF code (<code>0x0a</code>) so that the lines are joined with LF code in the decoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">codec#encode</strong></div>
<div style="margin-bottom:1em"><code>codec#encode(str:string):map</code></div>
Encodes a string <code>str</code> and returns the encoded result as <code>binary</code>.
</p>
<h3><span class="caption-index-3">5.6.5</span><a name="anchor-5-6-5"></a>Cast Operation</h3>
<p>
A function that expects a <code>codec</code> instance in its argument can also take a value of <code>string</code> that is recognized as a codec name.
</p>
<p>
With the above casting feature, you can call a function <code>f(codec:codec)</code> that takes a <code>codec</code> instance in its argument as below:
</p>
<ul>
<li><code>f(codec('utf-16'))</code> .. The most explicit way.</li>
<li><code>f('utf-16')</code> .. Implicit casting: from <code>string</code> to <code>codec</code>. </li>
</ul>
<h2><span class="caption-index-2">5.7</span><a name="anchor-5-7"></a>color Class</h2>
<h3><span class="caption-index-3">5.7.1</span><a name="anchor-5-7-1"></a>Overview</h3>
<p>
An instance of the <code>color</code> class represents a color data that consists of red, green, blue and alpha elements.
</p>
<p>
You can create a <code>color</code> instance by calling <code>color()</code> function.
</p>
<p>
There are class variables as shown below:
</p>
<h3><span class="caption-index-3">5.7.2</span><a name="anchor-5-7-2"></a>Predefined Variable</h3>
<p>
<table>
<tr>
<th>
Variable</th>
<th>
Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>color.names</code></td>
<td>
<code>string[]</code></td>

<td>
A list of color names that can be passed to <code>color()</code> function.</td>
</tr>


<tr>
<td>
<code>color.zero</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 0, 0, 0)</code></td>
</tr>


<tr>
<td>
<code>color.black</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 0, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.maroon</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(128, 0, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.green</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 128, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.olive</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(128, 128, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.navy</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 0, 128, 255)</code></td>
</tr>


<tr>
<td>
<code>color.purple</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(128, 0, 128, 255)</code></td>
</tr>


<tr>
<td>
<code>color.teal</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 128, 128, 255)</code></td>
</tr>


<tr>
<td>
<code>color.gray</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(128, 128, 128, 255)</code></td>
</tr>


<tr>
<td>
<code>color.silver</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(192, 192, 192, 255)</code></td>
</tr>


<tr>
<td>
<code>color.red</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(255, 0, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.lime</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 255, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.yellow</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(255, 255, 0, 255)</code></td>
</tr>


<tr>
<td>
<code>color.blue</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 0, 255, 255)</code></td>
</tr>


<tr>
<td>
<code>color.fuchsia</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(255, 0, 255, 255)</code></td>
</tr>


<tr>
<td>
<code>color.aqua</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(0, 255, 255, 255)</code></td>
</tr>


<tr>
<td>
<code>color.white</code></td>
<td>
<code>color</code></td>

<td>
Color instance equivalent with <code>color(255, 255, 255, 255)</code></td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.7.3</span><a name="anchor-5-7-3"></a>Property</h3>
<p>
A <code>color</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>a</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Value of the alpha element.</td>
</tr>

<tr>
<td>
<code>b</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Value of the blue element.</td>
</tr>

<tr>
<td>
<code>g</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Value of the green element.</td>
</tr>

<tr>
<td>
<code>r</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Value of the red element.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.7.4</span><a name="anchor-5-7-4"></a>Cast Operation</h3>
<p>
A function that expects a <code>color</code> instance in its argument can also take a value of <code>symbol</code>, <code>string</code> and <code>list</code> as below:
</p>
<ul>
<li><code>symbol</code> .. Recognized as a color name to look up the color table.</li>
<li><code>string</code> .. Recognized as a color name to look up the color table.</li>
<li><code>list</code> .. Expected to contain elements in a format <code>[red, green, blue]</code> or <code>[red, green, blue, alpha]</code>.</li>
</ul>
<p>
With the above casting feature, you can call a function <code>f(c:color)</code> that takes a <code>color</code> instance in its argument as below:
</p>
<ul>
<li><code>f(color(`purple))</code> .. The most explicit way.</li>
<li><code>f(`purple)</code> .. Implicit casting: from <code>symbol</code> to <code>color</code>.</li>
<li><code>f('purple')</code> .. Implicit casting: from <code>string</code> to <code>color</code>.</li>
<li><code>f([128, 0, 128])</code> .. Implicit casting: from <code>list</code> to <code>color</code>.</li>
</ul>
<h3><span class="caption-index-3">5.7.5</span><a name="anchor-5-7-5"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">color</strong></div>
<div style="margin-bottom:1em"><code>color(args+):map {block?}</code></div>
Creates a <code>color</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|c:color|</code>, where <code>c</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
There are two forms to call this function as below:
</p>
<ul>
<li><code>color(name:string, a?:number)</code> .. Creates an instance from color name and an optional alpha element. Predefined variable <code>color.names</code> is a list that contains available color names. A string in a format of <code>'#rrggbb'</code> that is used in HTML documents is also acceptable as a color name.</li>
<li><code>color(r:number, g?:number, b?:number, a?:number)</code> .. Creates an instance from RGB elements and an optional alpha element.</li>
</ul>
<h3><span class="caption-index-3">5.7.6</span><a name="anchor-5-7-6"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">color#getgray</strong></div>
<div style="margin-bottom:1em"><code>color#getgray()</code></div>
Calculates a gray scale from RGB elements in the <code>color</code> instance.
</p>
<p>
This is computed by a formula: <code>gray = 0.299 * red + 0.587 * blue + 0.114 * blue</code>.
</p>
<p>
<div><strong style="text-decoration:underline">color#html</strong></div>
<div style="margin-bottom:1em"><code>color#html()</code></div>
Returns a color string in a format of <code>'#rrggbb'</code> that is used in HTML documents.
</p>
<p>
<div><strong style="text-decoration:underline">color#list</strong></div>
<div style="margin-bottom:1em"><code>color#list():[alpha]</code></div>
Returns a list of RGB elements in a form <code>[r, g, b]</code>.
</p>
<p>
Specifying <code>:alpha</code> attribute would add the alpha element to the list.
</p>
<h2><span class="caption-index-2">5.8</span><a name="anchor-5-8"></a>complex Class</h2>
<h3><span class="caption-index-3">5.8.1</span><a name="anchor-5-8-1"></a>Overview</h3>
<p>
The <code>complex</code> class provides measures to calculate complex numbers.
</p>
<p>
You can create a <code>complex</code> instance by following ways:
</p>
<ul>
<li>Calls <code>complex()</code> function with a real and imaginary part of numbers. e.g., <code>complex(2, 3)</code></li>
<li>Calls <code>complex.polar()</code> function with an absolute value and an argument in radius. e.g., <code>complex.polar(5, math.pi / 6)</code></li>
<li>Appending <code>j</code> suffix after a number literal would create an imaginal part of a complex numbrer. e.g., <code>2 + 3j</code></li>
</ul>
<h3><span class="caption-index-3">5.8.2</span><a name="anchor-5-8-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">complex</strong></div>
<div style="margin-bottom:1em"><code>complex(real:number, imag?:number):map {block?}</code></div>
Creates a <code>complex</code> instance with a real part <code>real</code> and an imaginary part <code>imag</code>.
</p>
<p>
If the argument <code>imag</code> is omitted, the imaginary part would be set to zero.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:complex|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.8.3</span><a name="anchor-5-8-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">complex.polar</strong></div>
<div style="margin-bottom:1em"><code>complex.polar(abs:number, arg:number):static:map:[deg] {block?}</code></div>
Creates a <code>complex</code> instance with an absolute number <code>abs</code> and an angle <code>arg</code> in polar coords.
</p>
<p>
The argument <code>arg</code> is specified in a unit of radian. You can give it a degree value by calling the function with <code>:deg</code> attribute.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:complex|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">complex.roundoff</strong></div>
<div style="margin-bottom:1em"><code>complex.roundoff(threshold:number =&gt; 1e-10) {block?}</code></div>
Returns a complex number with real and imaginary parts being rounded off.
</p>
<p>
The argument <code>threshold</code> specifies the threshold value for the round-off.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:complex|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">5.9</span><a name="anchor-5-9"></a>datetime Class</h2>
<h3><span class="caption-index-3">5.9.1</span><a name="anchor-5-9-1"></a>Overview</h3>
<p>
The <code>datetime</code> class provides measures to handle date and time information.
</p>
<p>
You can create a <code>datetime</code> instance by calling following functions:
</p>
<ul>
<li><code>datetime()</code> .. Creates an intance from specified date and time.</li>
<li><code>datetime.now()</code> .. Creates an instance with its date and time fields set as the current one.</li>
<li><code>datetime.today()</code> .. Creates an instance with its date field set as the current one. Its time fields, <code>hour</code>, <code>min</code>, <code>sec</code> and <code>usec</code>, are set to zero.</li>
</ul>
<p>
You can calculate a <code>datetime</code> with a <code>timedelta</code> to put its date and time values forward and backward.
</p>
<h3><span class="caption-index-3">5.9.2</span><a name="anchor-5-9-2"></a>Predefined Variable</h3>
<p>
<table>
<tr>
<th>
Variable</th>
<th>
Type</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>datetime.Sunday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 0 that represents Sunday.</td>
</tr>


<tr>
<td>
<code>datetime.Monday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 1 that represents Monday.</td>
</tr>


<tr>
<td>
<code>datetime.Tuesday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 2 that represents Tuesday.</td>
</tr>


<tr>
<td>
<code>datetime.Wednesday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 3 that represents Wednesday.</td>
</tr>


<tr>
<td>
<code>datetime.Thursday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 4 that represents Thursday.</td>
</tr>


<tr>
<td>
<code>datetime.Friday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 5 that represents Friday.</td>
</tr>


<tr>
<td>
<code>datetime.Saturday</code></td>
<td>
<code>number</code></td>

<td>
Assigned with number 6 that represents Saturday.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.9.3</span><a name="anchor-5-9-3"></a>Property</h3>
<p>
A <code>datetime</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>day</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Day value betwen 1 and 31.</td>
</tr>

<tr>
<td>
<code>hour</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Hour value between 0 and 23.</td>
</tr>

<tr>
<td>
<code>min</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Minute value between 0 and 59.</td>
</tr>

<tr>
<td>
<code>month</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Month value between 1 and 12.</td>
</tr>

<tr>
<td>
<code>sec</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Second value between 0 and 59.</td>
</tr>

<tr>
<td>
<code>unixtime</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Unixtime, a time in second since January 1st of 1970.</td>
</tr>

<tr>
<td>
<code>usec</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Milli second value between 0 and 999999.</td>
</tr>

<tr>
<td>
<code>wday</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Week day value between 0 and 6.</td>
</tr>

<tr>
<td>
<code>week</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>yday</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Day in a year between 1 and 366.</td>
</tr>

<tr>
<td>
<code>year</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Year value between 1 and 9999.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.9.4</span><a name="anchor-5-9-4"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">datetime</strong></div>
<div style="margin-bottom:1em"><code>datetime(year:number, month:number, day:number, hour:number =&gt; 0, min:number =&gt; 0, sec:number =&gt; 0, usec:number =&gt; 0, minsoff?:number):map {block?}</code></div>
Creates an instance of <code>datetime</code> class based on the specified arguments.
</p>
<p>
Explanations of the arguments are shown below:
</p>
<ul>
<li><code>year</code> .. Christian year.</li>
<li><code>month</code> .. Month starting from 1. Numbers from 1 to 12 correspond to January to December.</li>
<li><code>day</code> .. Day in a month starting from 1.</li>
<li><code>hour</code> .. Hour in a day between 0 and 23.</li>
<li><code>min</code> .. Minute in an hour between 0 and 59.</li>
<li><code>sec</code> .. Second in a minute between 0 and 59.</li>
<li><code>usec</code> .. Millisecond in a second between 0 and 999.</li>
<li><code>minsoff</code> .. Timezone offset in minutes.</li>
</ul>
<p>
In default, the instance has a timezone offset based on the current system settings.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.9.5</span><a name="anchor-5-9-5"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">datetime#clrtzoff</strong></div>
<div style="margin-bottom:1em"><code>datetime#clrtzoff():reduce</code></div>
Eliminates timezone offset information from the instance.
</p>
<p>
<div><strong style="text-decoration:underline">datetime#format</strong></div>
<div style="margin-bottom:1em"><code>datetime#format(format =&gt; `w3c)</code></div>
Returns a string of the datetime properties based on the specified format. For the argument <code>format</code>, you can specify either a string of user-specific format or a symbol of predefined style.
</p>
<p>
A string of user-specific format contains following specifiers:
</p>
<ul>
<li><code>%d</code> .. day of month</li>
<li><code>%H</code> .. hour in 24-hour format</li>
<li><code>%I</code> .. hour in 12-hour format</li>
<li><code>%m</code> .. month</li>
<li><code>%M</code> .. minute</li>
<li><code>%S</code> .. second</li>
<li><code>%w</code> .. week number starting from 0 for Sunday.</li>
<li><code>%y</code> .. lower two digits of year</li>
<li><code>%Y</code> .. four digits of year</li>
</ul>
<p>
Below are the symbols of predefined styles:
</p>
<ul>
<li><code>`w3c</code> .. W3C style. eg) <code>'2015-01-01T12:34:56+09:00'</code></li>
<li><code>`http</code> .. a style used in HTTP protocol. eg) <code>'Thu, 01 Jan 2015 12:34:56 +0900'</code></li>
<li><code>`asctime</code> .. a style used by the C function <code>asctime()</code>. eg) <code>'Thu Jan  1 12:34:56 +0900 2015'</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">datetime.isleap</strong></div>
<div style="margin-bottom:1em"><code>datetime.isleap(year:number):static:map</code></div>
Returns <code>true</code> if the specified year is a leap one.
</p>
<p>
<div><strong style="text-decoration:underline">datetime.monthdays</strong></div>
<div style="margin-bottom:1em"><code>datetime.monthdays(year:number, month:number):static:map {block?}</code></div>
Returns a number of days that exists in the specified month.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">datetime.now</strong></div>
<div style="margin-bottom:1em"><code>datetime.now():static:[utc] {block?}</code></div>
Creates a <code>datetime</code> instance of the current time.
</p>
<p>
In default, the timezone offset is set to one in the system setting. Specifying <code>:utc</code> attribute would set the offset to 0.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">datetime.parse</strong></div>
<div style="margin-bottom:1em"><code>datetime.parse(str:string):static:map {block?}</code></div>
Parses a string that describs date and time information and returns the <code>datetime</code> instance.
</p>
<p>
It is capable of parsing the following style:
</p>
<ul>
<li>RFC1123 style. eg) <code>'Sat, 06 Nov 2010 08:49:37 GMT'</code></li>
<li>RFC1036 style. eg) <code>'Saturday, 06-Nov-10 08:49:37 GMT'</code></li>
<li>C's <code>asctime()</code> style. eg) <code>'Sat Nov  6 08:49:37 2010'</code>, <code>'Sat Nov  6 08:49:37 +0000 2010'</code></li>
<li>W3C style. eg) <code>'2010-11-06T08:49:37Z'</code></li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">datetime#settzoff</strong></div>
<div style="margin-bottom:1em"><code>datetime#settzoff(mins:number):reduce</code></div>
Sets timezone offset in minutes.
</p>
<p>
<div><strong style="text-decoration:underline">datetime.time</strong></div>
<div style="margin-bottom:1em"><code>datetime.time(hour:number =&gt; 0, minute:number =&gt; 0, sec:number =&gt; 0, usec:number =&gt; 0):static:map {block?}</code></div>
Creates a <code>datetime</code> instance from time information. The date inforomation is set as 1st of January in the Christian year of 0.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">datetime.today</strong></div>
<div style="margin-bottom:1em"><code>datetime.today():static:[utc] {block?}</code></div>
Creates a <code>datetime</code> instance of today. All the time information are cleared to 0.
</p>
<p>
In default, the timezone offset is set to one in the system setting. Specifying <code>:utc</code> attribute would set the offset to 0.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|dt:datetime|</code>, where <code>dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">datetime#utc</strong></div>
<div style="margin-bottom:1em"><code>datetime#utc()</code></div>
Calculates UTC time of the target <code>datetime</code> instance. An error occurs if the instance has no timezone offset
</p>
<p>
<div><strong style="text-decoration:underline">datetime.weekday</strong></div>
<div style="margin-bottom:1em"><code>datetime.weekday(year:number, month:number, day:number):static:map</code></div>
Returns a week number for the specified date, which starts from 0 for Sunday.
</p>
<h2><span class="caption-index-2">5.10</span><a name="anchor-5-10"></a>declaration Class</h2>
<h3><span class="caption-index-3">5.10.1</span><a name="anchor-5-10-1"></a>Overview</h3>
<p>
The <code>declaration</code> class provides information about argument's declaration defined in a function. You can get an iterator of <code>declaration</code> instances with the following measures that the <code>function</code> class provides:
</p>
<ul>
<li>A property value: <code>function#decls</code></li>
<li>An instance method: <code>function.getdecls()</code></li>
</ul>
<p>
Below is an example to print argument names declared in a function.
</p>
<pre><code>f(a, b, c, d) = {}
println(f.decls:*name)
</code></pre>
<h3><span class="caption-index-3">5.10.2</span><a name="anchor-5-10-2"></a>Property</h3>
<p>
A <code>declaration</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>default</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
An <code>expr</code> instance that represents a default value in the declaration if exists. This is <code>nil</code> when no default value is specified.</td>
</tr>

<tr>
<td>
<code>name</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
A <code>string</code> instance that represents the declaration's name.</td>
</tr>

<tr>
<td>
<code>symbol</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
A <code>symbol</code> instance that represents the declaration's name.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.10.3</span><a name="anchor-5-10-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">declaration#istype</strong></div>
<div style="margin-bottom:1em"><code>declaration#istype(type+:expr):map</code></div>
Return <code>true</code> if the declaration is defined as a type that is specified in the arguments.
</p>
<p>
The argument <code>type</code> has following formats:
</p>
<ul>
<li>a single symbol.</li>
<li>a sequence of symbols joined by a dot.</li>
</ul>
<p>
In the second format, a symbol on the left side indicates a container such as a module and a class.
</p>
<p>
Below is an example to check if the declaration is defined as <code>number</code> type.
</p>
<pre><code>decl.istype(`number)
</code></pre>
<p>
Below is an example to check if the declaration is defined as <code>re.match</code> type, which is a type named <code>match</code> defined in <code>re</code> module.
</p>
<pre><code>decl.istype(`re.match)
</code></pre>
<p>
You can also specify a type by describing factors in separate arguments like below:
</p>
<pre><code>decl.istype(`re, `match)
</code></pre>
<h2><span class="caption-index-2">5.11</span><a name="anchor-5-11"></a>dict Class</h2>
<h3><span class="caption-index-3">5.11.1</span><a name="anchor-5-11-1"></a>Overview</h3>
<p>
The <code>dict</code> class provides measures to handle dictionary data that can seek values by indexing with their associated keys. You can specify values of <code>string</code>, <code>number</code> and <code>symbol</code> as a dictionary key.
</p>
<p>
You can create a <code>dict</code> instance by following measures:
</p>
<ul>
<li>Calls <code>dict()</code> constructor.</li>
<li>Calls a function named <code>%</code> that is an alias of <code>dict()</code> constructor.</li>
</ul>
<p>
Below are examples to create a <code>dict</code> instance:
</p>
<pre><code>dict {'first' =&gt; 1, 'second' =&gt; 2, 'third' =&gt; 3}
dict {{'first', 1}, {'second', 2}, {'third', 3}}
dict {'first', 1, 'second', 2, 'third', 3}

dict(['first' =&gt; 1, 'second' =&gt; 2, 'third' =&gt; 3])
dict([['first', 1], ['second', 2], ['third', 3]])
dict(['first', 1, 'second', 2, 'third', 3])

%{'first' =&gt; 1, 'second' =&gt; 2, 'third' =&gt; 3}
%{{'first', 1}, {'second', 2}, {'third', 3}}
%{'first', 1, 'second', 2, 'third', 3}
</code></pre>
<p>
You can specify different type of values for keys in the same dictionary. In this case, values of different types are just recognized as different values.
</p>
<h3><span class="caption-index-3">5.11.2</span><a name="anchor-5-11-2"></a>Index Access</h3>
<p>
You can read and write element values in a <code>dict</code> with an indexer by giving it a key value which type is <code>string</code>, <code>number</code> or <code>symbol</code>. Below is an example:
</p>
<pre><code>x = %{'first' =&gt; 1, 'second' =&gt; 2, 'third' =&gt; 3}

println(x['second']) // prints `2`
x['third'] = 33      // replaces `3` with `33`
</code></pre>
<h3><span class="caption-index-3">5.11.3</span><a name="anchor-5-11-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">dict</strong></div>
<div style="margin-bottom:1em"><code>dict(elems?):[icase] {block?}</code></div>
Creates a <code>dict</code> instance.
</p>
<p>
It takes a list of key-value pairs in an argument as shown below:
</p>
<pre><code>d = dict([['apple', 100], ['grape', 200], ['banana', 80]])
</code></pre>
<p>
Or, you can use a block to describe them like below:
</p>
<pre><code>d = dict {
    ['apple', 100], ['grape', 200], ['banana', 80]
}
</code></pre>
<p>
You can specify values of <code>number</code>, <code>string</code> or <code>symbol</code> as dictionary keys.
</p>
<p>
You can also use the operator <code>=&gt;</code> to create a key-value pair like below:
</p>
<pre><code>d = dict(['apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80])
</code></pre>
<p>
Below is an example using a block:
</p>
<pre><code>d = dict {
    'apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80
}
</code></pre>
<p>
The symbol <code>%</code> is an alias of the function <code>dict()</code>.
</p>
<pre><code>d = %{
    'apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80
}
</code></pre>
<p>
In default, if keys contain alphabet characters, different cases are distinguished. Appending the attribute <code>:icase</code> would ignore cases in them.
</p>
<h3><span class="caption-index-3">5.11.4</span><a name="anchor-5-11-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">dict#append</strong></div>
<div style="margin-bottom:1em"><code>dict#append(elems?):reduce:[overwrite,strict,timid] {block?}</code></div>
Adds multiple key-value pairs. It takes a list of key-value pairs in an argument or in a block that has the same format with one for the function <code>dict()</code>.
</p>
<p>
If the specified key already exists in the dictionary, it would be overwritten. This behavior can be customized with the following attributes:
</p>
<ul>
<li><code>:overwrite</code> .. overwrite the existing one (default)</li>
<li><code>:strict</code> .. raises an error</li>
<li><code>:timid</code> .. keep the existing one</li>
</ul>
<p>
<div><strong style="text-decoration:underline">dict#clear</strong></div>
<div style="margin-bottom:1em"><code>dict#clear()</code></div>
Clears all the key-value pairs in the dictionary.
</p>
<p>
<div><strong style="text-decoration:underline">dict#erase</strong></div>
<div style="margin-bottom:1em"><code>dict#erase(key):map</code></div>
Erases a key-value pair that mathces the provided <code>key</code>.
</p>
<p>
The <code>key</code> is either <code>number</code>, <code>string</code> or <code>symbol</code>.
</p>
<p>
<div><strong style="text-decoration:underline">dict#get</strong></div>
<div style="margin-bottom:1em"><code>dict#get(key, default?):map:[raise]</code></div>
Seeks a value that is associated with the specified <code>key</code>.
</p>
<p>
The method would return <code>nil</code> as its default value when the specified key doesn't exist in the dictionary. It would use different value if the argument <code>default</code> is specified.
</p>
<p>
Since the <code>default</code> value is also processed with implicit mapping, you have to apply <code>object#nomap()</code> method to it if you want to specify a list or an iterator as a default value.
</p>
<p>
When the attribute <code>:raise</code> is specified, an error occurs in the case of the key's absence.
</p>
<p>
Another measure to get a value associated with a key is to use an index operator. The following two codes have the same effect.
</p>
<ul>
<li><code>v = d['foo']</code></li>
<li><code>v = d.get('foo'):raise</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">dict#haskey</strong></div>
<div style="margin-bottom:1em"><code>dict#haskey(key):map</code></div>
Returns <code>true</code> if the specified <code>key</code> exists in the dictionary.
</p>
<p>
<div><strong style="text-decoration:underline">dict#items</strong></div>
<div style="margin-bottom:1em"><code>dict#items() {block?}</code></div>
Returns an iterator of key-value pairs in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">dict#keys</strong></div>
<div style="margin-bottom:1em"><code>dict#keys() {block?}</code></div>
Returns an iterator of keys in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">dict#len</strong></div>
<div style="margin-bottom:1em"><code>dict#len()</code></div>
Returns the number of key-value pairs in the dictionary.
</p>
<p>
<div><strong style="text-decoration:underline">dict#put</strong></div>
<div style="margin-bottom:1em"><code>dict#put(key, value):map:reduce:[overwrite,strict,timid]</code></div>
Adds a new key-value pair.
</p>
<p>
If the specified key already exists in the dictionary, it would be overwritten. This behavior can be customized with the following attributes:
</p>
<ul>
<li><code>:overwrite</code> .. overwrite the existing one (default)</li>
<li><code>:strict</code> .. raises an error</li>
<li><code>:timid</code> .. keep the existing one</li>
</ul>
<p>
Another measure to add a key-value pair is to use an index operator. The following two codes have the same effect.
</p>
<ul>
<li><code>d['foo'] = 3</code></li>
<li><code>d.put('foo', 3)</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">dict#values</strong></div>
<div style="margin-bottom:1em"><code>dict#values() {block?}</code></div>
Returns an iterator of values in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">5.12</span><a name="anchor-5-12"></a>directory Class</h2>
<h3><span class="caption-index-3">5.12.1</span><a name="anchor-5-12-1"></a>Overview</h3>
<p>
The <code>directory</code> class handles information necessary to seek directory structure in a path. Its instance usually works with functions in <code>path</code> module: <code>path.dir()</code> and <code>path.walk()</code>.
</p>
<p>
Though the instance can be created by <code>directory()</code> function, you don't have to use it in many cases because a casting from <code>string</code> to <code>directory</code> instance works implicitly in a function call.
</p>
<h3><span class="caption-index-3">5.12.2</span><a name="anchor-5-12-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">directory</strong></div>
<div style="margin-bottom:1em"><code>directory(pathname:string):map {block?}</code></div>
Creates a <code>directory</code> instance from the specified path name.
</p>
<h2><span class="caption-index-2">5.13</span><a name="anchor-5-13"></a>environment Class</h2>
<h3><span class="caption-index-3">5.13.1</span><a name="anchor-5-13-1"></a>Overview</h3>
<p>
The <code>environment</code> class provides measures to operate variables in an environment, which is a fundamental mechanism to store variables.
</p>
<h3><span class="caption-index-3">5.13.2</span><a name="anchor-5-13-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">environment#getprop!</strong></div>
<div style="margin-bottom:1em"><code>environment#getprop!(symbol:symbol):map</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">environment#lookup</strong></div>
<div style="margin-bottom:1em"><code>environment#lookup(symbol:symbol, escalate:boolean =&gt; true):map</code></div>
Looks up a specified symbol in the environment and returns the associated value. In default, if the symbol is not defined in the environment, it will be searched in environments outside of the current one. Set escalate flag to false in order to disable such an escalation behaviour. Returns false when the symbol could not be found.
</p>
<p>
<div><strong style="text-decoration:underline">environment#setprop!</strong></div>
<div style="margin-bottom:1em"><code>environment#setprop!(symbol:symbol, value):map</code></div>

</p>
<h2><span class="caption-index-2">5.14</span><a name="anchor-5-14"></a>error Class</h2>
<h3><span class="caption-index-3">5.14.1</span><a name="anchor-5-14-1"></a>Overview</h3>
<p>
The <code>error</code> class provides measures to access error information.
</p>
<p>
There is no measures to create an <code>error</code> instance. They're instantiated and passed to a block of <code>catch()</code> function when an error occurs within a <code>try</code> block in a <code>try-catch</code> sequence.
</p>
<p>
In the following code, <code>e</code> is an instance that contains information about an error that has occured in the <code>try</code> block.
</p>
<pre><code>try {
    // any jobs
} catch {|e:error|
    // ...
}
</code></pre>
<h3><span class="caption-index-3">5.14.2</span><a name="anchor-5-14-2"></a>Predefined Variable</h3>
<p>
<table>
<tr>
<th>
Variable</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>error.ArgumentError</code></td>

<td>
Argument error.</td>
</tr>


<tr>
<td>
<code>error.ArithmeticError</code></td>

<td>
Arithmetic error.</td>
</tr>


<tr>
<td>
<code>error.AttributeError</code></td>

<td>
Invalid attribute is specified.</td>
</tr>


<tr>
<td>
<code>error.CodecError</code></td>

<td>
An error that is related to codec process.</td>
</tr>


<tr>
<td>
<code>error.CommandError</code></td>

<td>
An error that could happen in command line.</td>
</tr>


<tr>
<td>
<code>error.DeclarationError</code></td>

<td>
An error in a function\'s declarations.</td>
</tr>


<tr>
<td>
<code>error.FormatError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.IOError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.ImportError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.IndexError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.IteratorError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.KeyError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.MemberAccessError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.MemoryError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.NameError</code></td>

<td>
</td>
</tr>


<tr>
<td>
<code>error.NotImplementedError</code></td>

<td>
An error that could occur when a called function has no implemented body but an entry.</td>
</tr>


<tr>
<td>
<code>error.OutOfRange</code></td>

<td>
Index number is out of range.</td>
</tr>


<tr>
<td>
<code>error.ResourceError</code></td>

<td>
Resource error.</td>
</tr>


<tr>
<td>
<code>error.RuntimeError</code></td>

<td>
Runtime error.</td>
</tr>


<tr>
<td>
<code>error.SyntaxError</code></td>

<td>
Syntax error.</td>
</tr>


<tr>
<td>
<code>error.SystemError</code></td>

<td>
System error.</td>
</tr>


<tr>
<td>
<code>error.TypeError</code></td>

<td>
Type error.</td>
</tr>


<tr>
<td>
<code>error.ValueError</code></td>

<td>
Invalid value is specified.</td>
</tr>


<tr>
<td>
<code>error.ZeroDivisionError</code></td>

<td>
Zero-division occured in division or modulo operations.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.14.3</span><a name="anchor-5-14-3"></a>Property</h3>
<p>
An <code>error</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>lineno</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
The number of line where the expression that causes this error starts.</td>
</tr>

<tr>
<td>
<code>linenobtm</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
The number of line where the expression that causes this error ends.</td>
</tr>

<tr>
<td>
<code>postext</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
A text that consists of a source name and a line number.</td>
</tr>

<tr>
<td>
<code>source</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
The name of the file that causes this error.</td>
</tr>

<tr>
<td>
<code>text</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
An error message. If an attribute <code>:lineno</code> is specified, it would contain a line number.</td>
</tr>

<tr>
<td>
<code>trace</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
An iterator that generates <code>expr</code> instances that indicate stack trace.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.15</span><a name="anchor-5-15"></a>expr Class</h2>
<h3><span class="caption-index-3">5.15.1</span><a name="anchor-5-15-1"></a>Overview</h3>
<p>
The <code>expr</code> class provides inromation about the language's syntax expression.
</p>
<h3><span class="caption-index-3">5.15.2</span><a name="anchor-5-15-2"></a>Property</h3>
<p>
An <code>expr</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>attrfront</code></td>
<td>
<code>list</code></td>
<td>
R</td>

<td>
Exists in "identifier" and "caller".</td>
</tr>

<tr>
<td>
<code>attrs</code></td>
<td>
<code>list</code></td>
<td>
R</td>

<td>
Exists in "identifier" and "caller".</td>
</tr>

<tr>
<td>
<code>attrsopt</code></td>
<td>
<code>list</code></td>
<td>
R</td>

<td>
Exists in "identifier" and "caller".</td>
</tr>

<tr>
<td>
<code>block</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "caller".</td>
</tr>

<tr>
<td>
<code>blockparam</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
Exists in "block".</td>
</tr>

<tr>
<td>
<code>body</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Exists in "suffixed".</td>
</tr>

<tr>
<td>
<code>car</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "compound".</td>
</tr>

<tr>
<td>
<code>cdr</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "compound".</td>
</tr>

<tr>
<td>
<code>child</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "unary".</td>
</tr>

<tr>
<td>
<code>children</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
Exists in "collector".</td>
</tr>

<tr>
<td>
<code>left</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "binary".</td>
</tr>

<tr>
<td>
<code>lineno</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>linenobtm</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>operator</code></td>
<td>
<code>operator</code></td>
<td>
R</td>

<td>
Exists in "unaryop", "binaryop" and "assign".</td>
</tr>

<tr>
<td>
<code>postext</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>right</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "binary".</td>
</tr>

<tr>
<td>
<code>source</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>suffix</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Exists in "suffixed".</td>
</tr>

<tr>
<td>
<code>symbol</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Exists in "identifier".</td>
</tr>

<tr>
<td>
<code>trailer</code></td>
<td>
<code>expr</code></td>
<td>
R</td>

<td>
Exists in "caller".</td>
</tr>

<tr>
<td>
<code>typename</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>typesym</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>value</code></td>
<td>
<code>any</code></td>
<td>
R</td>

<td>
Exists in "value".</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.15.3</span><a name="anchor-5-15-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">expr</strong></div>
<div style="margin-bottom:1em"><code>expr(src:stream:r):map {block?}</code></div>
Parses a Gura script from the stream <code>src</code> and creates an <code>expr</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|expr:expr|</code>, where <code>expr</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.15.4</span><a name="anchor-5-15-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">expr#eval</strong></div>
<div style="margin-bottom:1em"><code>expr#eval(env?:environment) {block?}</code></div>
Evaluates the <code>expr</code> instance.
</p>
<p>
If the argument <code>env</code> is specified, that environment is used for evaluation. If omitted, the current scope is used.
</p>
<p>
<div><strong style="text-decoration:underline">expr.parse</strong></div>
<div style="margin-bottom:1em"><code>expr.parse(script:string):static:map {block?}</code></div>
Parses a Gura script in the string <code>script</code> and creates an <code>expr</code> instance.
</p>
<p>
If <code>block</code> is specified, it will be evaluated with block parameter in a format of <code>|expr:expr|</code> where <code>expr</code> is the created instance.
</p>
<p>
<div><strong style="text-decoration:underline">expr#textize</strong></div>
<div style="margin-bottom:1em"><code>expr#textize(style?:symbol, indent?:string)</code></div>
Composes a script text from a content of <code>expr</code>.
</p>
<p>
Argument <code>style</code> specifies the text style output, which takes the following symbols:
</p>
<ul>
<li><code>`crammed</code> .. Puts all the text in one line and removes volatile spaces.</li>
<li><code>`oneline</code> .. Puts all the text in one line.</li>
<li><code>`brief</code> .. Omits content of blocks and long strings with "<code>..</code>".</li>
<li><code>`fancy</code> .. Prints in the most readable style. This is the default.</li>
</ul>
<p>
The argument <code>indent</code> specifies a string used for indentation. Its default is a sequence of four spaces.
</p>
<p>
<div><strong style="text-decoration:underline">expr#tofunction</strong></div>
<div style="margin-bottom:1em"><code>expr#tofunction(`args*)</code></div>
Converts the <code>expr</code> into a function.
</p>
<p>
If the <code>expr</code> is a block that has a block parameter, that would be used as an argument list of the created function. Otherwise, the argument <code>args</code> declares the argument list.
</p>
<p>
It would be an error if <code>args</code> is specified and a block parameter exists as well.
</p>
<p>
<div><strong style="text-decoration:underline">expr#unquote</strong></div>
<div style="margin-bottom:1em"><code>expr#unquote()</code></div>
Returns <code>expr</code> instance that has removed quote operator from the original <code>expr</code>.
</p>
<p>
<div><strong style="text-decoration:underline">expr#write</strong></div>
<div style="margin-bottom:1em"><code>expr#write(dst:stream:w, style?:symbol, indent?:string)</code></div>
Outputs a script that describes the expression to the specified <code>stream</code>.
</p>
<p>
Argument <code>style</code> specifies the text style output, which takes the following symbols:
</p>
<ul>
<li><code>`crammed</code> .. Puts all the text in one line and removes volatile spaces.</li>
<li><code>`oneline</code> .. Puts all the text in one line.</li>
<li><code>`brief</code> .. Omits content of blocks and long strings with "<code>..</code>".</li>
<li><code>`fancy</code> .. Prints in the most readable style. This is the default.</li>
</ul>
<p>
The argument <code>indent</code> specifies a string used for indentation. Its default is a sequence of four spaces.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isunary</strong></div>
<div style="margin-bottom:1em"><code>expr#isunary()</code></div>
Returns <code>true</code> if expr is an expression of unary.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isunaryop</strong></div>
<div style="margin-bottom:1em"><code>expr#isunaryop()</code></div>
Returns <code>true</code> if expr is an expression of unaryop.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isquote</strong></div>
<div style="margin-bottom:1em"><code>expr#isquote()</code></div>
Returns <code>true</code> if expr is an expression of quote.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isbinary</strong></div>
<div style="margin-bottom:1em"><code>expr#isbinary()</code></div>
Returns <code>true</code> if expr is an expression of binary.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isbinaryop</strong></div>
<div style="margin-bottom:1em"><code>expr#isbinaryop()</code></div>
Returns <code>true</code> if expr is an expression of binaryop.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isassign</strong></div>
<div style="margin-bottom:1em"><code>expr#isassign()</code></div>
Returns <code>true</code> if expr is an expression of assign.
</p>
<p>
<div><strong style="text-decoration:underline">expr#ismember</strong></div>
<div style="margin-bottom:1em"><code>expr#ismember()</code></div>
Returns <code>true</code> if expr is an expression of member.
</p>
<p>
<div><strong style="text-decoration:underline">expr#iscollector</strong></div>
<div style="margin-bottom:1em"><code>expr#iscollector()</code></div>
Returns <code>true</code> if expr is an expression of collector.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isroot</strong></div>
<div style="margin-bottom:1em"><code>expr#isroot()</code></div>
Returns <code>true</code> if expr is an expression of root.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isblock</strong></div>
<div style="margin-bottom:1em"><code>expr#isblock()</code></div>
Returns <code>true</code> if expr is an expression of block.
</p>
<p>
<div><strong style="text-decoration:underline">expr#islister</strong></div>
<div style="margin-bottom:1em"><code>expr#islister()</code></div>
Returns <code>true</code> if expr is an expression of lister.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isiterer</strong></div>
<div style="margin-bottom:1em"><code>expr#isiterer()</code></div>
Returns <code>true</code> if expr is an expression of iterer.
</p>
<p>
<div><strong style="text-decoration:underline">expr#iscompound</strong></div>
<div style="margin-bottom:1em"><code>expr#iscompound()</code></div>
Returns <code>true</code> if expr is an expression of compound.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isindexer</strong></div>
<div style="margin-bottom:1em"><code>expr#isindexer()</code></div>
Returns <code>true</code> if expr is an expression of indexer.
</p>
<p>
<div><strong style="text-decoration:underline">expr#iscaller</strong></div>
<div style="margin-bottom:1em"><code>expr#iscaller()</code></div>
Returns <code>true</code> if expr is an expression of caller.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isvalue</strong></div>
<div style="margin-bottom:1em"><code>expr#isvalue()</code></div>
Returns <code>true</code> if expr is an expression of value.
</p>
<p>
<div><strong style="text-decoration:underline">expr#isidentifier</strong></div>
<div style="margin-bottom:1em"><code>expr#isidentifier()</code></div>
Returns <code>true</code> if expr is an expression of identifier.
</p>
<p>
<div><strong style="text-decoration:underline">expr#issuffixed</strong></div>
<div style="margin-bottom:1em"><code>expr#issuffixed()</code></div>
Returns <code>true</code> if expr is an expression of suffixed.
</p>
<h2><span class="caption-index-2">5.16</span><a name="anchor-5-16"></a>formatter Class</h2>
<h3><span class="caption-index-3">5.16.1</span><a name="anchor-5-16-1"></a>Overview</h3>
<p>
The <code>formatter</code> class provides information about a format specifier.
</p>
<p>
The function <code>printf()</code> has the following declaration:
</p>
<pre><code>printf('name: %s, age: %d\n', name, age)
</code></pre>
<p>
The first argument is a string containing format specifiers like <code>%s</code> and <code>%d</code> that determine the manner on how the correspoding values <code>name</code> and <code>age</code> should be formatted. In the formatting mechanism, when the specifiers <code>%s</code> and <code>%d</code> appear, it would call methods <code>name.__format_s__()</code> and <code>age.__format_s__()</code> respectively which are format handlers responsible of formatting these values. In general, a format handler has a format like <code>__format_X__(fmt:formatter)</code> where <code>X</code> is the symbol of the specifier and <code>fmt</code> is a <code>formatter</code> instance that carries information about the associated specifier such as minimum width and a padding character. The handler must return a <code>string</code> as its result.
</p>
<p>
The table below summarizes associations between specifiers and the method name of their format handlers:
</p>
<p>
<table>
<tr>
<th>
Specifier</th>
<th>
Method Name</th>
</tr>

<tr>
<td>
<code>%d</code></td>
<td>
<code>__format_d__</code></td>
</tr>

<tr>
<td>
<code>%u</code></td>
<td>
<code>__format_u__</code></td>
</tr>

<tr>
<td>
<code>%b</code></td>
<td>
<code>__format_b__</code></td>
</tr>

<tr>
<td>
<code>%o</code></td>
<td>
<code>__format_o__</code></td>
</tr>

<tr>
<td>
<code>%x</code></td>
<td>
<code>__format_x__</code></td>
</tr>

<tr>
<td>
<code>%e</code></td>
<td>
<code>__format_e__</code></td>
</tr>

<tr>
<td>
<code>%f</code></td>
<td>
<code>__format_f__</code></td>
</tr>

<tr>
<td>
<code>%g</code></td>
<td>
<code>__format_g__</code></td>
</tr>

<tr>
<td>
<code>%s</code></td>
<td>
<code>__format_s__</code></td>
</tr>

<tr>
<td>
<code>%c</code></td>
<td>
<code>__format_c__</code></td>
</tr>

</table>

</p>
<p>
This feature is supposed to be used when you want your original class's instance properly formatted in <code>printf</code>. Below is an example to implement a format handler for the specifier <code>%d</code>:
</p>
<pre><code>A = class {

    // any implementations

    __format_d__(fmt:format) = {
        // returns a string for %d specifier.
    }
}

a = A()
printf('%d', a) // a.__format_d__() is called
</code></pre>
<h3><span class="caption-index-3">5.16.2</span><a name="anchor-5-16-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">formatter#getminwidth</strong></div>
<div style="margin-bottom:1em"><code>formatter#getminwidth()</code></div>
Returns an expected minimum width for the field.
</p>
<p>
For example, with <code>'%3d'</code>, this method would return <code>3</code>.
</p>
<p>
<div><strong style="text-decoration:underline">formatter#getpadding</strong></div>
<div style="margin-bottom:1em"><code>formatter#getpadding()</code></div>
Returns a string containing a padding character, a space or <code>'0'</code>.
</p>
<p>
In default, a space is used for padding. For example, with <code>'%3d'</code>, this method would return <code>' '</code>.
</p>
<p>
When a character <code>'0'</code> appears after <code>'%'</code>, that becomes the padding character. For example, with <code>'%03d'</code>, this method would return <code>'0'</code>.
</p>
<p>
<div><strong style="text-decoration:underline">formatter#getplusmode</strong></div>
<div style="margin-bottom:1em"><code>formatter#getplusmode()</code></div>
Returns a symbol that indicates an expected action when a positive number appears.
</p>
<ul>
<li><code>`none</code> .. No character ahead of the number.</li>
<li><code>`space</code> .. A space should be inserted.</li>
<li><code>`plus</code> .. A plus character should be inserted.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">formatter#getprecision</strong></div>
<div style="margin-bottom:1em"><code>formatter#getprecision()</code></div>
Returns an expected precision for the field.
</p>
<p>
For example, with <code>'%.3d'</code>, this method would return <code>3</code>.
</p>
<p>
<div><strong style="text-decoration:underline">formatter#isleftalign</strong></div>
<div style="margin-bottom:1em"><code>formatter#isleftalign()</code></div>
Returns <code>true</code> if the field is expected to be aligned on left.
</p>
<p>
For example, with <code>'%-3d'</code>, this method would return <code>true</code>.
</p>
<p>
<div><strong style="text-decoration:underline">formatter#issharp</strong></div>
<div style="margin-bottom:1em"><code>formatter#issharp()</code></div>
Returns <code>true</code> if the specifier sequence includes <code>'#'</code> flag, which means some literal prefixes such as <code>0x</code> are expected to be appended at the top.
</p>
<p>
For example, with <code>'%#x'</code>, this method would return <code>true</code>.
</p>
<p>
<div><strong style="text-decoration:underline">formatter#isuppercase</strong></div>
<div style="margin-bottom:1em"><code>formatter#isuppercase()</code></div>
Returns <code>true</code> if alphabet characters are expected to be shown in upper case.
</p>
<p>
Upper case characters are requested when a specifier such as <code>'%X'</code>, <code>'%E'</code> and <code>'%G'</code> is specified.
</p>
<h2><span class="caption-index-2">5.17</span><a name="anchor-5-17"></a>function Class</h2>
<h3><span class="caption-index-3">5.17.1</span><a name="anchor-5-17-1"></a>Overview</h3>
<p>
The <code>function</code> class provides measure to inspect information about the instance.
</p>
<p>
All the functions are instances of <code>function</code> class, so an implementation of a function means a realization of a <code>function</code> instance. You can also create the instance using <code>function()</code> constructor. The following two codes have the same result:
</p>
<pre><code>f(a:number, b:number, c:number) = {
    (a + b + c) / 3
}

f = function(a:number, b:number, c:number) {
    (a + b + c) / 3
}
</code></pre>
<p>
Using <code>function()</code>, you can use variables prefixed by a dollar character so that they are automatically added to the argument list. In such a case, the variables are added to the argument list in the same order as they appear in the function body. The code below creates a function with a declaration <code>f($a, $b, $c)</code>.
</p>
<pre><code>f = function {
    ($a + $b + $c) / 3
}
</code></pre>
<p>
You can use <code>&amp;</code> as an alias of <code>function()</code> as shown below:
</p>
<pre><code>f = &amp;{
    ($a + $b + $c) / 3
}
</code></pre>
<h3><span class="caption-index-3">5.17.2</span><a name="anchor-5-17-2"></a>Property</h3>
<p>
A <code>function</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>decls</code></td>
<td>
<code>iterator</code></td>
<td>
R</td>

<td>
An iterator of <code>declaration</code> instances that provide information about argument declaration the function defines.</td>
</tr>

<tr>
<td>
<code>expr</code></td>
<td>
<code>expr</code></td>
<td>
R/W</td>

<td>
An expression of the function.</td>
</tr>

<tr>
<td>
<code>format</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
A string showing a declared format of the function.</td>
</tr>

<tr>
<td>
<code>fullname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
A full name of the function that is prefixed by a name of the module or the class it belongs to.</td>
</tr>

<tr>
<td>
<code>name</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
A <code>string</code> instance that represents the function's name.</td>
</tr>

<tr>
<td>
<code>symbol</code></td>
<td>
<code>symbol</code></td>
<td>
R/W</td>

<td>
A <code>symbol</code> instance that represents the function's name.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.17.3</span><a name="anchor-5-17-3"></a>Operator</h3>
<p>
You can print a function's help from the interactive prompt using the unary operator "<code>~</code>". Below is an example to print the help of <code>printf()</code> function:
</p>
<pre><code>&gt;&gt;&gt; ~printf
</code></pre>
<h3><span class="caption-index-3">5.17.4</span><a name="anchor-5-17-4"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">function</strong></div>
<div style="margin-bottom:1em"><code>function(`args*) {block}</code></div>
Creates a <code>function</code> instance with an argument list of <code>args</code> and a procedure body provided by <code>block</code>.
</p>
<p>
Following two codes have the same effect with each other.
</p>
<ul>
<li><code>f = function(a, b, c) { /* any job */ }</code></li>
<li><code>f(a, b, c) = { /* any job */ }</code></li>
</ul>
<h3><span class="caption-index-3">5.17.5</span><a name="anchor-5-17-5"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">function.getdecls</strong></div>
<div style="margin-bottom:1em"><code>function.getdecls(func:function):static:map</code></div>
Creates an iterator of <code>declaration</code> instances that provide information about argument declaration that the function instance <code>func</code> defines.
</p>
<p>
This class method returns the same information as the property <code>function#decls</code>.
</p>
<p>
<div><strong style="text-decoration:underline">function.getexpr</strong></div>
<div style="margin-bottom:1em"><code>function.getexpr(func:function):static:map</code></div>
Returns an expression of the function instance <code>func</code>.
</p>
<p>
It would return <code>nil</code> if the function is implemented with binary programs, not scripts.
</p>
<p>
This class method returns the same information as the property <code>function#expr</code>.
</p>
<p>
<div><strong style="text-decoration:underline">function.getformat</strong></div>
<div style="margin-bottom:1em"><code>function.getformat(func:function):static:map</code></div>
Returns a string showing a declared format of the function instance <code>func</code>.
</p>
<p>
This class method returns the same information as the property <code>function#format</code>.
</p>
<p>
<div><strong style="text-decoration:underline">function.getfullname</strong></div>
<div style="margin-bottom:1em"><code>function.getfullname(func:function):static:map</code></div>
Returns a full name of the function instance <code>func</code>, which is prefixed by a name of the module or the class the instance belongs to.
</p>
<p>
This class method returns the same information as the property <code>function#fullname</code>.
</p>
<p>
<div><strong style="text-decoration:underline">function.getname</strong></div>
<div style="margin-bottom:1em"><code>function.getname(func:function):static:map</code></div>
Returns a name of the function instance <code>func</code> in <code>string</code> type.
</p>
<p>
This class method returns the same information as the property <code>function#name</code>.
</p>
<p>
<div><strong style="text-decoration:underline">function.getsymbol</strong></div>
<div style="margin-bottom:1em"><code>function.getsymbol(func:function):static:map</code></div>
Returns a name of the function instance <code>func</code> in <code>symbol</code> type.
</p>
<p>
This class method returns the same information as the property <code>function#symbol</code>.
</p>
<p>
<div><strong style="text-decoration:underline">function#mathdiff</strong></div>
<div style="margin-bottom:1em"><code>function#mathdiff(var?:symbol):reduce</code></div>
Returns a <code>function</code> instance that computes derivation of the target function, which is expected to contain only mathematical procedures. An error occurs if the target function has any elements that have nothing to do with mathematics.
</p>
<p>
In default, it differentiates the target function with respect to its first argument. Below is an example:
</p>
<pre><code>&gt;&gt;&gt; f(x) = math.sin(x)
&gt;&gt;&gt; g = f.mathdiff()    // g is a function to compute math.cos(x)
</code></pre>
<p>
Specify a symbol to argument <code>var</code> when you want to differentiate with respect to another variable.
</p>
<p>
You can check the result of derivation by seeing property <code>function#expr</code> like below:
</p>
<pre><code>&gt;&gt;&gt; g.expr
`math.cos(x)
</code></pre>
<h2><span class="caption-index-2">5.18</span><a name="anchor-5-18"></a>gear@averagepool1d Class</h2>
<h3><span class="caption-index-3">5.18.1</span><a name="anchor-5-18-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.18.2</span><a name="anchor-5-18-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@averagepool1d</strong></div>
<div style="margin-bottom:1em"><code>gear@averagepool1d(size:number, strides?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@averagepool1d</code> instance.
</p>
<p>
The <code>size</code> is a gear size.
</p>
<p>
The <code>strides</code> is a strides of sliding window. Default is one.
</p>
<p>
The <code>padding</code> is a padding style <code>`valid</code> or <code>`same</code>. Default is <code>`same</code>.
</p>
<p>
The <code>channel_pos</code> specifies where channel dimension is positioned and takes <code>`first</code> or <code>`last</code>. Default is <code>`last</code>. 
</p>
<h3><span class="caption-index-3">5.18.3</span><a name="anchor-5-18-3"></a>Property</h3>
<p>
A <code>gear@averagepool1d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.19</span><a name="anchor-5-19"></a>gear@averagepool2d Class</h2>
<h3><span class="caption-index-3">5.19.1</span><a name="anchor-5-19-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.19.2</span><a name="anchor-5-19-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@averagepool2d</strong></div>
<div style="margin-bottom:1em"><code>gear@averagepool2d(size[]:number, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@averagepool2d</code> instance.
</p>
<h3><span class="caption-index-3">5.19.3</span><a name="anchor-5-19-3"></a>Property</h3>
<p>
A <code>gear@averagepool2d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.20</span><a name="anchor-5-20"></a>gear@averagepool3d Class</h2>
<h3><span class="caption-index-3">5.20.1</span><a name="anchor-5-20-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.20.2</span><a name="anchor-5-20-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@averagepool3d</strong></div>
<div style="margin-bottom:1em"><code>gear@averagepool3d(size[]:number, strides[]?:number, padding?:symbol, format?:symbol):map {block?}</code></div>
Creates a <code>gear@averagepool3d</code> instance.
</p>
<h3><span class="caption-index-3">5.20.3</span><a name="anchor-5-20-3"></a>Property</h3>
<p>
A <code>gear@averagepool3d</code> instance has the following properties:
</p>
<h2><span class="caption-index-2">5.21</span><a name="anchor-5-21"></a>gear@conv1d Class</h2>
<h3><span class="caption-index-3">5.21.1</span><a name="anchor-5-21-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.21.2</span><a name="anchor-5-21-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@conv1d</strong></div>
<div style="margin-bottom:1em"><code>gear@conv1d(array:array, strides?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@conv1d</code> instance.
</p>
<p>
The <code>array</code> is an <code>array</code> instance that has one of the following shapes:
</p>
<ul>
<li><code>[size]</code> .. 1-dimension</li>
<li><code>[size, channel_num]</code> .. 2-dimensions and <code>channel_pos</code> is <code>`last</code></li>
<li><code>[channel_num, size]</code> .. 2-dimensions and <code>channel_pos</code> is <code>`first</code></li>
<li><code>[filter_num, size]</code> .. 2-dimensions and <code>channel_pos</code> is <code>`none</code></li>
<li><code>[filter_num, size, channel_num]</code> .. 3-dimensions and <code>channel_pos</code> is <code>`last</code></li>
<li><code>[filter_num, channel_num, size]</code> .. 3-dimensions and <code>channel_pos</code> is <code>`first</code></li>
</ul>
<p>
where <code>size</code> is the size of the filter's kernel, <code>channel_num</code> is the number of channels and <code>filter_num</code> is the number of filters.
</p>
<p>
The <code>strides</code> is a strides for a sliding window. Default is one.
</p>
<p>
The <code>padding</code> is a padding style and takes <code>`valid</code> or <code>`same</code>. Default is <code>`same</code>. When <code>valid</code> is specified, there is no padding. When <code>same</code> is specified, zero values are padded so that the result array has the size of the division of the original size by <code>strides</code>.
</p>
<p>
The <code>channel_pos</code> is a channel position and takes <code>`none</code>, <code>`first</code> or <code>`last</code>. If not specified, <code>`none` for an array without channel dimension</code>and <code>`last</code> for others are to be set.
</p>
<h3><span class="caption-index-3">5.21.3</span><a name="anchor-5-21-3"></a>Property</h3>
<p>
A <code>gear@conv1d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>array</code></td>
<td>
<code>array</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>channel_num</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>filter_num</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.22</span><a name="anchor-5-22"></a>gear@conv2d Class</h2>
<h3><span class="caption-index-3">5.22.1</span><a name="anchor-5-22-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.22.2</span><a name="anchor-5-22-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@conv2d</strong></div>
<div style="margin-bottom:1em"><code>gear@conv2d(array:array, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@conv2d</code> instance.
</p>
<p>
The given <code>array</code> instance shoud have one of the following shapes:
</p>
<ul>
<li><code>[row_size, col_size]</code> .. 2-dimensions</li>
<li><code>[row_size, col_size, channel_num]</code> .. 3-dimensions and <code>channel_pos</code> is <code>`last</code></li>
<li><code>[channel_num, row_size, col_size]</code> .. 3-dimensions and <code>channel_pos</code> is <code>`first</code></li>
<li><code>[filter_num, row_size, col_size]</code> .. 3-dimensions and <code>channel_pos</code> is <code>`none</code></li>
<li><code>[filter_num, row_size, col_size, channel_num]</code> .. 4-dimensions and <code>channel_pos</code> is <code>`last</code></li>
<li><code>[filter_num, channel_num, row_size, col_size]</code> .. 4-dimensions and <code>channel_pos</code> is <code>`first</code></li>
</ul>
<p>
where <code>row_size</code> and <code>col_size</code> are the size of the filter's kernel, <code>channel_num</code> is the number of channels and <code>filter_num</code> is the number of filters.
</p>
<p>
The <code>strides</code> is a list of strides for a sliding window in row and column. Default is <code>[1, 1]</code>.
</p>
<p>
The <code>padding</code> is a padding style and takes <code>`valid</code> or <code>`same</code>. Default is <code>`same</code>. When <code>valid</code> is specified, there is no padding. When <code>same</code> is specified, zero values are padded so that the result array has the size of the division of the original size by <code>strides</code>.
</p>
<p>
The <code>channel_pos</code> is a channel position and takes <code>`none</code>, <code>`first</code> or <code>`last</code>. If not specified, <code>`none` for an array without channel dimension</code>and <code>`last</code> for others are to be set.
</p>
<h3><span class="caption-index-3">5.22.3</span><a name="anchor-5-22-3"></a>Property</h3>
<p>
A <code>gear@conv2d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>array</code></td>
<td>
<code>array</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>channel_num</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>filter_num</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.23</span><a name="anchor-5-23"></a>gear@conv3d Class</h2>
<h3><span class="caption-index-3">5.23.1</span><a name="anchor-5-23-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.23.2</span><a name="anchor-5-23-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@conv3d</strong></div>
<div style="margin-bottom:1em"><code>gear@conv3d(array:array, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@conv3d</code> instance.
</p>
<p>
The given <code>array</code> instance shoud have one of the following shapes:
</p>
<ul>
<li><code>[plane_size, row_size, col_size]</code> .. 3-dimensions</li>
<li><code>[plane_size, row_size, col_size, channel_num]</code> .. 4-dimensions and <code>channel_pos</code> is <code>`last</code></li>
<li><code>[channel_num, plane_size, row_size, col_size]</code> .. 4-dimensions and <code>channel_pos</code> is <code>`first</code></li>
<li><code>[filter_num, plane_size, row_size, col_size]</code> .. 4-dimensions and <code>channel_pos</code> is <code>`none</code></li>
<li><code>[filter_num, plane_size, row_size, col_size, channel_num]</code> .. 5-dimensions and <code>channel_pos</code> is <code>`last</code></li>
<li><code>[filter_num, channel_num, plane_size, row_size, col_size]</code> .. 5-dimensions and <code>channel_pos</code> is <code>`first</code></li>
</ul>
<p>
where <code>plane_size</code>, <code>row_size</code> and <code>col_size</code> are the size of the filter's kernel, <code>channel_num</code> is the number of channels and <code>filter_num</code> is the number of filters.
</p>
<p>
The <code>strides</code> is a list of strides for a sliding window in plane, row and column. Default is <code>[1, 1, 1]</code>.
</p>
<p>
The <code>padding</code> is a padding style and takes <code>`valid</code> or <code>`same</code>. Default is <code>`same</code>. When <code>valid</code> is specified, there is no padding. When <code>same</code> is specified, zero values are padded so that the result array has the size of the division of the original size by <code>strides</code>.
</p>
<p>
The <code>channel_pos</code> is a channel position and takes <code>`none</code>, <code>`first</code> or <code>`last</code>. If not specified, <code>`none` for an array without channel dimension</code>and <code>`last</code> for others are to be set.
</p>
<h3><span class="caption-index-3">5.23.3</span><a name="anchor-5-23-3"></a>Property</h3>
<p>
A <code>gear@conv3d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>array</code></td>
<td>
<code>array</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>channel_num</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>filter_num</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.24</span><a name="anchor-5-24"></a>gear@maxpool1d Class</h2>
<h3><span class="caption-index-3">5.24.1</span><a name="anchor-5-24-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.24.2</span><a name="anchor-5-24-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@maxpool1d</strong></div>
<div style="margin-bottom:1em"><code>gear@maxpool1d(size:number, strides?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@maxpool1d</code> instance.
</p>
<p>
The <code>size</code> is a gear size.
</p>
<p>
The <code>strides</code> is a strides of sliding window. Default is one.
</p>
<p>
The <code>padding</code> is a padding style <code>`valid</code> or <code>`same</code>. Default is <code>`same</code>.
</p>
<p>
The <code>channel_pos</code> specifies where channel dimension is positioned and takes <code>`first</code> or <code>`last</code>. Default is <code>`last</code>. 
</p>
<h3><span class="caption-index-3">5.24.3</span><a name="anchor-5-24-3"></a>Property</h3>
<p>
A <code>gear@maxpool1d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.25</span><a name="anchor-5-25"></a>gear@maxpool2d Class</h2>
<h3><span class="caption-index-3">5.25.1</span><a name="anchor-5-25-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.25.2</span><a name="anchor-5-25-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@maxpool2d</strong></div>
<div style="margin-bottom:1em"><code>gear@maxpool2d(size[]:number, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
Creates a <code>gear@maxpool2d</code> instance.
</p>
<h3><span class="caption-index-3">5.25.3</span><a name="anchor-5-25-3"></a>Property</h3>
<p>
A <code>gear@maxpool2d</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>channel_pos</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>padding</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>

<tr>
<td>
<code>strides</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.26</span><a name="anchor-5-26"></a>gear@maxpool3d Class</h2>
<h3><span class="caption-index-3">5.26.1</span><a name="anchor-5-26-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.26.2</span><a name="anchor-5-26-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@maxpool3d</strong></div>
<div style="margin-bottom:1em"><code>gear@maxpool3d(size[]:number, strides[]?:number, padding?:symbol, format?:symbol):map {block?}</code></div>
Creates a <code>gear@maxpool3d</code> instance.
</p>
<h3><span class="caption-index-3">5.26.3</span><a name="anchor-5-26-3"></a>Property</h3>
<p>
A <code>gear@maxpool3d</code> instance has the following properties:
</p>
<h2><span class="caption-index-2">5.27</span><a name="anchor-5-27"></a>gear@relu Class</h2>
<h3><span class="caption-index-3">5.27.1</span><a name="anchor-5-27-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.27.2</span><a name="anchor-5-27-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@relu</strong></div>
<div style="margin-bottom:1em"><code>gear@relu() {block?}</code></div>
Creates a <code>gear@relu</code> instance.
</p>
<h2><span class="caption-index-2">5.28</span><a name="anchor-5-28"></a>gear@sigmoid Class</h2>
<h3><span class="caption-index-3">5.28.1</span><a name="anchor-5-28-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.28.2</span><a name="anchor-5-28-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@sigmoid</strong></div>
<div style="margin-bottom:1em"><code>gear@sigmoid() {block?}</code></div>
Creates a <code>gear@sigmoid</code> instance.
</p>
<h2><span class="caption-index-2">5.29</span><a name="anchor-5-29"></a>gear@softmax Class</h2>
<h3><span class="caption-index-3">5.29.1</span><a name="anchor-5-29-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.29.2</span><a name="anchor-5-29-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@softmax</strong></div>
<div style="margin-bottom:1em"><code>gear@softmax(axis?:number):map {block?}</code></div>
Creates a <code>gear@softmax</code> instance.
</p>
<h3><span class="caption-index-3">5.29.3</span><a name="anchor-5-29-3"></a>Property</h3>
<p>
A <code>gear@softmax</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>axis</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">5.30</span><a name="anchor-5-30"></a>gear@tanh Class</h2>
<h3><span class="caption-index-3">5.30.1</span><a name="anchor-5-30-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.30.2</span><a name="anchor-5-30-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gear@tanh</strong></div>
<div style="margin-bottom:1em"><code>gear@tanh() {block?}</code></div>
Creates a <code>gear@tanh</code> instance.
</p>
<h2><span class="caption-index-2">5.31</span><a name="anchor-5-31"></a>help Class</h2>
<h3><span class="caption-index-3">5.31.1</span><a name="anchor-5-31-1"></a>Overview</h3>
<p>
The <code>help</code> class provides measures to access help information associated with a <code>function</code> instance.
</p>
<p>
You can get a <code>help</code> instance from a <code>function</code> instance or a <code>class</code> by calling <code>help@function()</code> or <code>help@class()</code> respectively.
</p>
<h3><span class="caption-index-3">5.31.2</span><a name="anchor-5-31-2"></a>Property</h3>
<p>
A <code>help</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>doc</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
The help text.</td>
</tr>

<tr>
<td>
<code>format</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
A name of the syntax format in which the help text is described such as <code>'markdown'</code>.</td>
</tr>

<tr>
<td>
<code>lang</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
A symbol of the natural language in which the help text is written. For example, <code>`en</code> for English and <code>`ja</code> for Japanese.</td>
</tr>

<tr>
<td>
<code>title</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
The title of the help.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.31.3</span><a name="anchor-5-31-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">help.text@iterator</strong></div>
<div style="margin-bottom:1em"><code>help.text@iterator(lang:symbol):static {block?}</code></div>
Returns a help text for functions that return an iterator.
</p>
<p>
The argument <code>lang</code> is a symbol that specifies the language in which the text is written, e.g. <code>`en</code> for English and <code>`ja</code> for Japanese.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">help.text@block</strong></div>
<div style="margin-bottom:1em"><code>help.text@block(lang:symbol, varname:string, typename:string):static {block?}</code></div>
Returns a help text that for functions that take a block .
</p>
<p>
The argument <code>lang</code> is a symbol that specifies the language in which the text is written, e.g. <code>`en</code> for English and <code>`ja</code> for Japanese.
</p>
<p>
In the text, variable names would be replaced by <code>varname</code> and type names by <code>typename</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">help.presenter</strong></div>
<div style="margin-bottom:1em"><code>help.presenter(format:string):static:void {block}</code></div>
Registers a presentation procedure with a name specified by the argument <code>format</code>.
</p>
<p>
The procedure is written in the block that takes block parameters: <code>|help:help|</code>.
</p>
<h2><span class="caption-index-2">5.32</span><a name="anchor-5-32"></a>image Class</h2>
<h3><span class="caption-index-3">5.32.1</span><a name="anchor-5-32-1"></a>Overview</h3>
<p>
The <code>image</code> class provides following measures to handle graphic image data:
</p>
<ul>
<li>Reads image data from a file.</li>
<li>Writes image data to a file.</li>
<li>Apply some modifications on image data including rotation, resize and color conversion.</li>
</ul>
<p>
Acceptable image data formats can be extended by importing modules. Below is a table to show image formats and name of modules that handle them. The string listed in "imagetype" column shows a name that is used by functions <code>image()</code>, <code>image#read()</code> and <code>image#write()</code> to explicitly specify the image data format in a process of reading and writing files.
</p>
<p>
<table>
<tr>
<th>
Image Format</th>
<th>
Module Name</th>
<th>
imagetype</th>
</tr>

<tr>
<td>
BMP</td>
<td>
<code>bmp</code></td>
<td>
<code>'bmp'</code></td>
</tr>

<tr>
<td>
GIF</td>
<td>
<code>gif</code></td>
<td>
<code>'gif'</code></td>
</tr>

<tr>
<td>
JPEG</td>
<td>
<code>jpeg</code></td>
<td>
<code>'jpeg'</code></td>
</tr>

<tr>
<td>
Microsoft Icon</td>
<td>
<code>msico</code></td>
<td>
<code>'msico'</code></td>
</tr>

<tr>
<td>
PNG</td>
<td>
<code>png</code></td>
<td>
<code>'png'</code></td>
</tr>

<tr>
<td>
PPM</td>
<td>
<code>ppm</code></td>
<td>
<code>'ppm'</code></td>
</tr>

<tr>
<td>
TIFF</td>
<td>
<code>tiff</code></td>
<td>
<code>'tiff'</code></td>
</tr>

</table>

</p>
<h3><span class="caption-index-3">5.32.2</span><a name="anchor-5-32-2"></a>Property</h3>
<p>
An <code>image</code> instance has the following properties:
</p>
<p>
Takes one of the following symbols indicating what elements are stored in the memory:
</p>
<ul>
<li><code>`rgb</code> .. red, green and blue</li>
<li><tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>format</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Takes one of the following symbols indicating what elements are stored in the memory:</td>
</tr>
 <tr>
<td>
<code>height</code></td>
<td>
<code>number</code></td>
<td>
R</td>
 <td>
Image height.</td>
</tr>
 <tr>
<td>
<code>palette</code></td>
<td>
<code>palette</code></td>
<td>
R/W</td>
 <td>
A <code>palette</code> instance associated with this image. If there's no palette associated, this property returns <code>nil</code>.</td>
</tr>
 <tr>
<td>
<code>width</code></td>
<td>
<code>number</code></td>
<td>
R</td>
 <td>
Image width.</td>
</tr>
</li>
</ul>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>format</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Takes one of the following symbols indicating what elements are stored in the memory:</td>
</tr>
 <tr>
<td>
<code>height</code></td>
<td>
<code>number</code></td>
<td>
R</td>
 <td>
Image height.</td>
</tr>
 <tr>
<td>
<code>palette</code></td>
<td>
<code>palette</code></td>
<td>
R/W</td>
 <td>
A <code>palette</code> instance associated with this image. If there's no palette associated, this property returns <code>nil</code>.</td>
</tr>
 <tr>
<td>
<code>width</code></td>
<td>
<code>number</code></td>
<td>
R</td>
 <td>
Image width.</td>
</tr>
</table>

</p>
<h3><span class="caption-index-3">5.32.3</span><a name="anchor-5-32-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">image</strong></div>
<div style="margin-bottom:1em"><code>image(args+):map {block?}</code></div>
Returns an image instance with specified characteristics. There are three forms to call the function as below:
</p>
<ul>
<li><code>image(format:symbol)</code> .. Creates an image instance of the specified format without buffer allocated.</li>
<li><code>image(format:symbol, width:number, height:number, color?:color)</code> .. Allocates an image buffer with the specified size and fills it with the color.</li>
<li><code>image(stream:stream, format?:symbol, imagetype?:string)</code> .. Reads image data from the stream and allocates necessary buffer in which the read data is stored.</li>
</ul>
<p>
The argument <code>format</code> specifies what elements are stored in the memory and takes one of the following symbols:
</p>
<ul>
<li><code>`rgb</code> .. red, green and blue</li>
<li><code>`rgba</code> .. red, green, blue and alpha</li>
</ul>
<p>
In the third form, the format of the image data is determined by the byte sequence of the stream data and its file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code>imagetype</code>.
</p>
<h3><span class="caption-index-3">5.32.4</span><a name="anchor-5-32-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">image#allocbuff</strong></div>
<div style="margin-bottom:1em"><code>image#allocbuff(width:number, height:number, color?:color):reduce</code></div>
Allocates a specified size of buffer in the <code>image</code> instance that is supposed to has no buffer allocated.
</p>
<p>
The allocated buffer will be filled with <code>color</code>. If omitted, it will be filled with zero value.
</p>
<p>
An error occurs in following cases:
</p>
<ul>
<li>It fails to allocate necessary buffer.</li>
<li>The <code>image</code> instance already has allocated buffer.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">image#blur</strong></div>
<div style="margin-bottom:1em"><code>image#blur(radius:number, sigma?:number) {block?}</code></div>
Returns a new image that blurs the original image with the given parameters.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#clear</strong></div>
<div style="margin-bottom:1em"><code>image#clear():reduce</code></div>
Fills the buffer in the <code>image</code> instance with zero value.
</p>
<p>
This has the same effect with calling <code>image#fill()</code> with <code>color.zero</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#crop</strong></div>
<div style="margin-bottom:1em"><code>image#crop(x:number, y:number, width?:number, height?:number):map {block?}</code></div>
Returns a new image instance of the extracted area of the source image.
</p>
<p>
The extracted area is specified by the following arguments:
</p>
<ul>
<li><code>x</code> .. The left position.</li>
<li><code>y</code> .. The top position.</li>
<li><code>width</code> .. The width. If it's omitted or specified with <code>nil</code>, the whole area on the right of <code>x</code> will be extracted.</li>
<li><code>height</code> .. The height. If it's omitted or specified with <code>nil</code>, the whole area on the bottom of <code>y</code> will be extracted.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#delpalette</strong></div>
<div style="margin-bottom:1em"><code>image#delpalette():reduce</code></div>
Deletes a <code>palette</code> instance that belongs to the <code>image</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#extract</strong></div>
<div style="margin-bottom:1em"><code>image#extract(x:number, y:number, width:number, height:number, element:symbol, dst):reduce</code></div>
Extracts the element values within the specified area of the image, and store them into a list. The argument <code>x</code> and <code>y</code> specifies the left-top position, and <code>width</code>, and <code>height</code> does the size of the area.
</p>
<p>
The argument <code>element</code> takes the following symbol that specifies which element should be extracted:
</p>
<ul>
<li><code>`r</code> .. red</li>
<li><code>`g</code> .. green</li>
<li><code>`b</code> .. blue</li>
<li><code>`a</code> .. alpha</li>
</ul>
<p>
The argument <code>dst</code> specifies the variable into which the extracted data is stored, which must be a list that has enough space to store the data.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#fill</strong></div>
<div style="margin-bottom:1em"><code>image#fill(color:color):reduce</code></div>
Fills the whole image with the specified color.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#fillrect</strong></div>
<div style="margin-bottom:1em"><code>image#fillrect(x:number, y:number, width:number, height:number, color:color):map:reduce</code></div>
Fills the specified area with the specified color. The argument <code>x</code> and <code>y</code> specifies the left-top position, and <code>width</code>, and <code>height</code> does the size of the area.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#flip</strong></div>
<div style="margin-bottom:1em"><code>image#flip(orient:symbol):map {block?}</code></div>
Returns a new <code>image</code> instance that flips the source image horizontally or vertically. You can specify the following symbol to the <code>orient</code> argument.
</p>
<ul>
<li><code>`horz</code> .. flips horizontally.</li>
<li><code>`vert</code> .. flips vertically.</li>
<li><code>`both</code> .. flips both horizontally and vertically. This has the same effect with rotating the image 180 degrees.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#getpixel</strong></div>
<div style="margin-bottom:1em"><code>image#getpixel(x:number, y:number):map {block?}</code></div>
Returns a color of a pixel data at the specified position.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|c:color|</code>, where <code>c</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#grayscale</strong></div>
<div style="margin-bottom:1em"><code>image#grayscale() {block?}</code></div>
Returns a new image instance that converts the source image into gray scale.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#mapcolorlevel</strong></div>
<div style="margin-bottom:1em"><code>image#mapcolorlevel(map@r:array@uint8, map@g?:array@uint8, map@b?:array@uint8) {block?}</code></div>
Returns a new image that converts color levels according to the given table.
</p>
<p>
Each of the arguments <code>map@r</code>, <code>map@g</code> and <code>map@b</code> is an instance of array@uchar containing 256 numbers that range between 0 and 255 and corresponds to elements red, green and blue respectively. An element value in the source image becomes an index of the list and the indexed value will be stored as a converted element value.
</p>
<p>
If you want to apply a mapping table to all the elements, call the method with a single argument like <code>image#mapcolorlevel(map)</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#paste</strong></div>
<div style="margin-bottom:1em"><code>image#paste(x:number, y:number, src:image, width?:number, height?:number, xoffset:number =&gt; 0, yoffset:number =&gt; 0, a:number =&gt; 255):map:reduce</code></div>
Pastes the source image <code>src</code> onto the target image instance at the specified position.
</p>
<p>
The argument <code>width</code>, <code>height</code>, <code>xoffset</code> and <code>yoffset</code> specify the source image's area to be pasted. If they're omitted, the whole image will be pasted.
</p>
<p>
The argument <code>a</code> specifies the alpha value that is put on the target image.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#putpixel</strong></div>
<div style="margin-bottom:1em"><code>image#putpixel(x:number, y:number, color:color):map:reduce</code></div>
Puts a color on the specified position.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#size</strong></div>
<div style="margin-bottom:1em"><code>image#size()</code></div>
Returns the image size as a list <code>[width, height]</code>.
</p>
<p>
<div><strong style="text-decoration:underline">image#store</strong></div>
<div style="margin-bottom:1em"><code>image#store(x:number, y:number, width:number, height:number, element:symbol, src):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">image#read</strong></div>
<div style="margin-bottom:1em"><code>image#read(stream:stream:r, imagetype?:string):map:reduce</code></div>
Reads image data from a stream.
</p>
<p>
The format of the image data is determined by the byte sequence of the stream data and its file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code>imagetype</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#reducecolor</strong></div>
<div style="margin-bottom:1em"><code>image#reducecolor(palette?:palette) {block?}</code></div>
Creates an image that reduces colors in the original image with a set of colors in the given palette. The specified palette would be associated with the created image.
</p>
<p>
If no argument is specified, the associated palette would be used. In this case, an error occurs if there's no palette associated.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#replacecolor</strong></div>
<div style="margin-bottom:1em"><code>image#replacecolor(colorOrg:color, color:color, tolerance?:number):reduce</code></div>
Replaces pixels that have a color matching <code>colorOrg</code> with the <code>color</code>.
</p>
<p>
The argument <code>tolerance</code> specifies an acceptable distance for the matching. If omitted, only an exact match is acceptable.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#resize</strong></div>
<div style="margin-bottom:1em"><code>image#resize(width?:number, height?:number):map:[box,ratio] {block?}</code></div>
Resizes the image to the size specified by <code>width</code> and <code>height</code> and returns the result.
</p>
<ul>
<li>When both <code>width</code> and <code>height</code> are specified, the image would be resized to the size.</li>
<li>When <code>width</code> is specified and <code>height</code> is omitted or <code>nil</code>, the resized height would be calculated from the width so that they keep the same ratio as the original.</li>
<li>When <code>width</code> is <code>nil</code> and <code>height</code> is specified, the resized width would be calculated from the height so that they keep the same ratio as the original.</li>
</ul>
<p>
The following attributes are acceptable:
</p>
<ul>
<li><code>:box</code> .. When only <code>width</code> is specified, the same value is set to <code>height</code>.</li>
<li><code>:ratio</code> .. Treats values of <code>width</code> and <code>height</code> as magnifying ration instead of pixel size.</li>
</ul>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#rotate</strong></div>
<div style="margin-bottom:1em"><code>image#rotate(rotate:number, background?:color):map {block?}</code></div>
Creates an image that rotates the original image by the specified angle.
</p>
<p>
The argument <code>angle</code> specifies the rotation angle in degree unit, and positive numbers for counterclockwise direction and negative for clockwise direction.
</p>
<p>
The created instance has a size that exactly fits the rotated image. The argument <code>background</code> specifies the color of pixels to fill the empty area that appears after rotation. If omitted, the color that has all elements set to zero is used for filling.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#scan</strong></div>
<div style="margin-bottom:1em"><code>image#scan(x?:number, y?:number, width?:number, height?:number, scandir?:symbol) {block?}</code></div>
Returns an iterator that scans pixels in the image.
</p>
<p>
The arguments <code>x</code>, <code>y</code>, <code>width</code> and <code>height</code> specify the image area to scan. The argument <code>scandir</code> specifies the scan direction and takes one of the following symbol:
</p>
<p>
<table>
<tr>
<th>
Symbol</th>
<th>
Start Pos</th>
<th>
Direction</th>
</tr>

<tr>
<td>
<code>`left_top_horz</code></td>
<td>
left-top</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>`left_top_vert</code></td>
<td>
left-top</td>
<td>
vertical</td>
</tr>

<tr>
<td>
<code>`left_bottom_horz</code></td>
<td>
left-bottom</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>`left_bottom_vert</code></td>
<td>
left-bottom</td>
<td>
vertical</td>
</tr>

<tr>
<td>
<code>`right_top_horz</code></td>
<td>
right-top</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>`right_top_vert</code></td>
<td>
right-top</td>
<td>
vertical</td>
</tr>

<tr>
<td>
<code>`right_bottom_horz</code></td>
<td>
right-bottom</td>
<td>
horizontal</td>
</tr>

<tr>
<td>
<code>`right_bottom_vert</code></td>
<td>
right-bottom</td>
<td>
vertical</td>
</tr>

</table>

</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">image#setalpha</strong></div>
<div style="margin-bottom:1em"><code>image#setalpha(a:number, color?:color, tolerance?:number):reduce</code></div>
Replaces the alpha element of all the pixels in the image with the value specified by <code>a</code>.
</p>
<p>
If the argument <code>color</code> is specified, alpha element of pixels that match with that color would be replaced. The argument <code>tolerance</code> specifies the distance within which the color is determined as matched.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#thumbnail</strong></div>
<div style="margin-bottom:1em"><code>image#thumbnail(width?:number, height?:number):map:[box] {block?}</code></div>
Resizes the image so that it fits within a rectangular area specified by <code>width</code> and <code>height</code> and returns the result.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|img:image|</code>, where <code>img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">image#write</strong></div>
<div style="margin-bottom:1em"><code>image#write(stream:stream:w, imagetype?:string):map:reduce</code></div>
Writes image data to a stream.
</p>
<p>
The format of the image data is determined by the stream's file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code>imagetype</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<h2><span class="caption-index-2">5.33</span><a name="anchor-5-33"></a>iterator/list Class</h2>
<h3><span class="caption-index-3">5.33.1</span><a name="anchor-5-33-1"></a>Overview</h3>
<p>
The <code>iterator</code> class provides measures to operate an iterator, which iterates values that come from containers and streams.
</p>
<p>
The <code>list</code> class provides measures to handle a list structure, which stores values on memory that can be accessed by indexer.
</p>
<h3><span class="caption-index-3">5.33.2</span><a name="anchor-5-33-2"></a>Iterator-specific Features</h3>
<h4><span class="caption-index-4">5.33.2.1</span><a name="anchor-5-33-2-1"></a>Function to Create iterator Instance</h4>
<p>
<div><strong style="text-decoration:underline">iterator</strong></div>
<div style="margin-bottom:1em"><code>iterator(value+) {block?}</code></div>
Creates an iterator that combines iterators given in the argument.
</p>
<p>
If an argument is not an iterator, that would be added as an element.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h4><span class="caption-index-4">5.33.2.2</span><a name="anchor-5-33-2-2"></a>Method Specific to iterator Class</h4>
<p>
<div><strong style="text-decoration:underline">iterator#delay</strong></div>
<div style="margin-bottom:1em"><code>iterator#delay(delay:number) {block?}</code></div>
Creates an iterator that returns each element with an interval time specified by the argument <code>delay</code> in seconds.
</p>
<p>
<div><strong style="text-decoration:underline">iterator#finite</strong></div>
<div style="margin-bottom:1em"><code>iterator#finite():reduce</code></div>
Marks the iterator as a finite one by clearing its infinite flag.
</p>
<p>
This method returns the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">iterator#infinite</strong></div>
<div style="margin-bottom:1em"><code>iterator#infinite():reduce</code></div>
Marks the iterator as an infinite one by setting its infinite flag.
</p>
<p>
This method returns the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">iterator#isinfinite</strong></div>
<div style="margin-bottom:1em"><code>iterator#isinfinite()</code></div>
Returns <code>true</code> if the iterator is infinite one.
</p>
<p>
The trait of iterator's infinity is used to avoid an endless process by evaluating an infinite iterator. An attempt to evaluate an infinite iterator such as creation of a list from it would occur an error.
</p>
<p>
<div><strong style="text-decoration:underline">iterator#next</strong></div>
<div style="margin-bottom:1em"><code>iterator#next()</code></div>
Returns a next element of the iterator. This operation updates the iterator's internal status.
</p>
<p>
<div><strong style="text-decoration:underline">iterator#repeater</strong></div>
<div style="margin-bottom:1em"><code>iterator#repeater()</code></div>
Makes the iterator behave as a "repeater". This would allow the iterator be evaulated when it appears as an element of another "repeater" iterator.
</p>
<p>
Below is an example:
</p>
<pre><code>x = repeat(3):iter {
    ['apple', 'orange', 'grape'].each()
}
println(x)
// Just prints iterator instance three times
// since x can't evaluate the internal iterator.

x = repeat(3):iter {
    ['apple', 'orange', 'grape'].each().repeater()
}
println(x)
// Prints 'apple', 'orange' and  'grape' three times
// after evaluating the internal iterator.
</code></pre>
<h3><span class="caption-index-3">5.33.3</span><a name="anchor-5-33-3"></a>List-specific Features</h3>
<h4><span class="caption-index-4">5.33.3.1</span><a name="anchor-5-33-3-1"></a>Creating List</h4>
<p>
There are several ways to create a list.
</p>
<pre><code>[3, 1, 4, 1, 5, 9]
@{3, 1, 4, 1, 5, 9}
</code></pre>
<h4><span class="caption-index-4">5.33.3.2</span><a name="anchor-5-33-3-2"></a>Index Access</h4>
<p>
You can read and write element values in a list with an indexer by giving it an index number starting from zero. Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F]

println(x[2]) // prints `C
x[4] = `e     // replaces `E with `e
</code></pre>
<h4><span class="caption-index-4">5.33.3.3</span><a name="anchor-5-33-3-3"></a>Function to Create list Instance</h4>
<p>
<div><strong style="text-decoration:underline">list</strong></div>
<div style="margin-bottom:1em"><code>list(value+)</code></div>
Creates a new list from given values in its argument list. If a given value is a list or an iteartor, elements it contains are added to the created list.
</p>
<p>
<div><strong style="text-decoration:underline">xlist</strong></div>
<div style="margin-bottom:1em"><code>xlist(value+)</code></div>
Creates a new list from given values except for <code>nil</code> in its argument list. If a given value is a list or an iteartor, elements it contains are added to the created list.
</p>
<p>
<div><strong style="text-decoration:underline">set</strong></div>
<div style="margin-bottom:1em"><code>set(iter+:iterator):[and,or,xor]</code></div>
Creates a new list that contains unique values from given iterators in its argument list.
</p>
<p>
In default, all the elements in each iterators are added to the created list. Specifying the following attributes would apply a filtering condition.
</p>
<ul>
<li><code>:and</code> .. Elements that exist in all the iterators are added.</li>
<li><code>:or</code> .. All the elements are added. This is the default behavior.</li>
<li><code>:xor</code> .. Elements that exist in only one iterator are added.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">xset</strong></div>
<div style="margin-bottom:1em"><code>xset(iter+:iterator):[and,or,xor]</code></div>
Creates a new list that contains unique values except for <code>nil</code> from given iterators in its argument list.
</p>
<p>
In default, all the elements in each iterators are added to the created list. Specifying the following attributes would apply a filtering condition.
</p>
<ul>
<li><code>:and</code> .. Elements that exist in all the iterators are added.</li>
<li><code>:or</code> .. All the elements are added. This is the default behavior.</li>
<li><code>:xor</code> .. Elements that exist in only one iterator are added.</li>
</ul>
<h4><span class="caption-index-4">5.33.3.4</span><a name="anchor-5-33-3-4"></a>Method Specific to list Class</h4>
<p>
<div><strong style="text-decoration:underline">list#add</strong></div>
<div style="margin-bottom:1em"><code>list#add(elem+):reduce</code></div>
Add specified items to the list.
</p>
<p>
<div><strong style="text-decoration:underline">list#append</strong></div>
<div style="margin-bottom:1em"><code>list#append(elem+):reduce</code></div>
Adds specified items to the list. If the item is a list or an iterator, each element in such an item is added to the list.
</p>
<p>
<div><strong style="text-decoration:underline">list#clear</strong></div>
<div style="margin-bottom:1em"><code>list#clear():reduce</code></div>
Clear the content of the list.
</p>
<p>
<div><strong style="text-decoration:underline">list#combination</strong></div>
<div style="margin-bottom:1em"><code>list#combination(n:number) {block?}</code></div>
Creates an iterator that generates lists that contain elements picked up from the original list in a combination manner.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">list#erase</strong></div>
<div style="margin-bottom:1em"><code>list#erase(idx*:number):reduce</code></div>
Erases elements at the specified indices.
</p>
<p>
<div><strong style="text-decoration:underline">list#first</strong></div>
<div style="margin-bottom:1em"><code>list#first()</code></div>
Returns a first value in the list. An error occurs when the list is empty.
</p>
<p>
<div><strong style="text-decoration:underline">list#get</strong></div>
<div style="margin-bottom:1em"><code>list#get(index:number):flat:map</code></div>
Returns a value stored at the specified index in the list. An error occurs when the index is out of range.
</p>
<p>
<div><strong style="text-decoration:underline">list#insert</strong></div>
<div style="margin-bottom:1em"><code>list#insert(idx:number, elem+):reduce</code></div>
Insert specified items to the list from the selected index.
</p>
<p>
<div><strong style="text-decoration:underline">list#isempty</strong></div>
<div style="margin-bottom:1em"><code>list#isempty()</code></div>
Return true if the list is empty.
</p>
<p>
<div><strong style="text-decoration:underline">list#last</strong></div>
<div style="margin-bottom:1em"><code>list#last()</code></div>
Returns a last value in the list. An error occurs when the list is empty.
</p>
<p>
<div><strong style="text-decoration:underline">list#permutation</strong></div>
<div style="margin-bottom:1em"><code>list#permutation(n?:number) {block?}</code></div>
Creates an iterator that generates lists that contain elements picked up from the original list in a permutation manner.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">list#put</strong></div>
<div style="margin-bottom:1em"><code>list#put(index:number, value:nomap):map:reduce</code></div>
Stores a value at the specified index in the list. An error occurs when the index is out of range.
</p>
<p>
<div><strong style="text-decoration:underline">list#shift</strong></div>
<div style="margin-bottom:1em"><code>list#shift():[raise]</code></div>
Shifts the elements of the list. If the content of the list is [1, 2, 3, 4], it becomes [2, 3, 4] after calling this method. In default, no error occurs even when the list is empty. To raise an error for executing this method on an empty list, specify :raise attribute.
</p>
<p>
<div><strong style="text-decoration:underline">list#shuffle</strong></div>
<div style="margin-bottom:1em"><code>list#shuffle():reduce</code></div>
Shuffle the order of the list content based on random numbers.
</p>
<p>
<div><strong style="text-decoration:underline">list.zip</strong></div>
<div style="margin-bottom:1em"><code>list.zip(values+):static {block?}</code></div>
Creates an iterator generating lists that bind given argument values. When the value is a list or an iterator, each item in it would be zipped.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h3><span class="caption-index-3">5.33.4</span><a name="anchor-5-33-4"></a>Method Common to Both list and iterator Classes</h3>
<p>
<div><strong style="text-decoration:underline">iterable#after</strong></div>
<div style="margin-bottom:1em"><code>iterable#after(criteria) {block?}</code></div>
Creates an iterator that picks up elements that appear at positions after the criteria is evaluated to be <code>true</code>.
</p>
<p>
You can specify a function, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#align</strong></div>
<div style="margin-bottom:1em"><code>iterable#align(n:number, value?) {block?}</code></div>
Creates an iterator that returns the specified number of elements in the source iterator. If the number is larger than the length of the source iterator, the lacking part is filled with <code>value</code>. If the argument <code>value</code> is omitted, <code>nil</code> is used for the filling.
</p>
<p>
Below is an example to specify a number less than the source length:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F].align(3)
// x generates `A, `B, `C.
</code></pre>
<p>
Below is an example to specify a number that exceeds the source length:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F].align(8)
// x generates `A, `B, `C, `D, `E, `F, nil, nil.
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#and</strong></div>
<div style="margin-bottom:1em"><code>iterable#and()</code></div>
Calculates a logical AND result of all the values in the iterable.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#argmax</strong></div>
<div style="margin-bottom:1em"><code>iterable#argmax():[indices,last_index]</code></div>
Returns a position index where the maximum value is found at first.
</p>
<p>
The following attributes modify the behavior:
</p>
<ul>
<li><code>:last_index</code> .. returns an index where the maximum value is found at last.</li>
<li><code>:indices</code> .. returns a list of all indices where the maximum value is found.</li>
</ul>
<p>
Calling of methods <code>iterable#argmas()</code> and <code>iteraboe#max()</code> have the same effect when attributes are specified as follows:
</p>
<ul>
<li><code>iterable.argmax()</code> and <code>iterable.max():index</code></li>
<li><code>iterable.argmax():last_index</code> and <code>iterable.max():last_index</code></li>
<li><code>iterable.argmax():indices</code> and <code>iterable.max():indices</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">iterable#argmin</strong></div>
<div style="margin-bottom:1em"><code>iterable#argmin():[indices,last_index]</code></div>
Returns a position index where the minimum value is found at first.
</p>
<p>
The following attributes modify the behavior:
</p>
<ul>
<li><code>:last_index</code> .. returns an index where the minimum value is found at last.</li>
<li><code>:indices</code> .. returns a list of all indices where the minimum value is found.</li>
</ul>
<p>
Calling of methods <code>iterable#argmas()</code> and <code>iteraboe#max()</code> have the same effect when attributes are specified as follows:
</p>
<ul>
<li><code>iterable.argmax()</code> and <code>iterable.max():index</code></li>
<li><code>iterable.argmax():last_index</code> and <code>iterable.max():last_index</code></li>
<li><code>iterable.argmax():indices</code> and <code>iterable.max():indices</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">iterable#before</strong></div>
<div style="margin-bottom:1em"><code>iterable#before(criteria) {block?}</code></div>
Creates an iterator that extracts elements in the iterable before criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#contains</strong></div>
<div style="margin-bottom:1em"><code>iterable#contains(value)</code></div>
Returns <code>true</code> if the specified value appears in the iterable.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#count</strong></div>
<div style="margin-bottom:1em"><code>iterable#count(criteria?)</code></div>
Returns a number of elements that matches the given criteria which is a single-argument function or a value.
</p>
<p>
When a function is applied, it counts the number of true after evaluating element value with the function. If a value is applied, it counts the number of elements that are equal to the value.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#cycle</strong></div>
<div style="margin-bottom:1em"><code>iterable#cycle(n?:number) {block?}</code></div>
Creates an iterator that iterates elements in the source iterator cyclically.
</p>
<p>
The argument <code>n</code> specifies the number of elements the created iterator returns. If omitted, it would iterates elements infinitely.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E].cycle()
// x generates `A, `B, `C, `D, `E, `A, `B, `C, `D, `E, `A, `B, ..
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#each</strong></div>
<div style="margin-bottom:1em"><code>iterable#each() {block?}</code></div>
Creates an iterator that iterates each element in the list.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#filter</strong></div>
<div style="margin-bottom:1em"><code>iterable#filter(criteria?) {block?}</code></div>
Creates an iterable that filters values in the source iterable by a criteria.
</p>
<p>
A criteria can be an iterable or a function instance.
</p>
<ul>
<li>When the criteria is an iterable, the created iterator would scan the source and the criteria iterable simultaneously and would return a value of the source when the corresponding criteria value is evaluated as <code>true</code>.</li>
<li>When the criteria is a function instance, the created iterator would give it a value of the source as an argument and would return the value when the function has returned <code>true</code>.</li>
</ul>
<p>
Below is an example to use an iterable as its criteria:
</p>
<pre><code>x = [3, 1, 4, 1, 5, 9]
y = filter(x &gt; 3)
// (x &gt; 3) makes a list [false, false, true, false, true, true]
// y generates 4, 5, 9
</code></pre>
<p>
Below is an example to use a function as its criteria:
</p>
<pre><code>x = [3, 1, 4, 1, 5, 9]
y = filter(&amp;{$x &gt; 3})
// y generates 4, 5, 9
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#find</strong></div>
<div style="margin-bottom:1em"><code>iterable#find(criteria?):[index]</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">iterable#flatten</strong></div>
<div style="margin-bottom:1em"><code>iterable#flatten():[bfs,dfs] {block?}</code></div>
Creates an iterator that searches items recursively if they are lists or iterators.
</p>
<p>
Specifying an attribute could customize searching order as below:
</p>
<ul>
<li><code>:dfs</code> .. Searches in depth-first order. This is the default behavior.</li>
<li><code>:bfs</code> .. Searches in breadth-first order.</li>
</ul>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [[`A, `B, `C], [`D, `E, [`F, `G, `H], `I, `J], `K, `L]

y = x.flattten():dfs
// y generates `A, `B, `C, `D, `E, `F, `G, `H, `I, `J, `K, `L

y = x.flatten():bfs
// y generates `K, `L, `A, `B, `C, `D, `E, `I, `J, `F, `G, `H
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#fold</strong></div>
<div style="margin-bottom:1em"><code>iterable#fold(n:number, nstep?:number):map:[iteritem,neat] {block?}</code></div>
Creates an iterator that packs <code>n</code> elements of the source iterator into a list and returns it as its element.
</p>
<p>
The argument <code>nstep</code> specifies the shift amount to the next packing.If omitted, the next packing is shifted by <code>n</code> elements.
</p>
<p>
Specifying the attribute <code>:iteritem</code> returns an iterator as its element instead of a list
</p>
<p>
If the last packing doesn't satisfy <code>n</code> elements, its list would be shorter than <code>n</code>. When specifying the attribute <code>:neat</code>, such an immature list would be eliminated.
</p>
<p>
Following is an example to fold elements by 3:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].fold(3)
// x generates [`A, `B, `C], [`D, `E, `F], [`G, `H].
</code></pre>
<p>
Following is an example to fold elements by 3 with a step of 2:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].fold(3, 2)
// x generates [`A, `B, `C], [`C, `D, `E], [`E, `F, `G], [`G, `H].
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#format</strong></div>
<div style="margin-bottom:1em"><code>iterable#format(format:string):map {block?}</code></div>
Creates an iterator that converts element values in the source iterable into strings depending on formatter specifier in <code>format</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#head</strong></div>
<div style="margin-bottom:1em"><code>iterable#head(n:number):map {block?}</code></div>
Creates an iterator that takes the first <code>n</code> elements from the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#join</strong></div>
<div style="margin-bottom:1em"><code>iterable#join(sep?:string):map</code></div>
Joins all the elements in the iterable as strings while inserting the specified separator <code>sep</code> and returns the result.
</p>
<p>
If an element is not a <code>string</code> value, it would be converted to a <code>string</code> before being joined.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#joinb</strong></div>
<div style="margin-bottom:1em"><code>iterable#joinb()</code></div>
Joins all the <code>binary</code> values in the iterable and returns the result.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#len</strong></div>
<div style="margin-bottom:1em"><code>iterable#len()</code></div>
Returns the length of the iterable.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#map</strong></div>
<div style="margin-bottom:1em"><code>iterable#map(func:function) {block?}</code></div>
Creates an iterator that generates element values after applying the specfied function on them. The function must take one argument.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#max</strong></div>
<div style="margin-bottom:1em"><code>iterable#max():[index,indices,last_index]</code></div>
Returns the maximum value in the iterable.
</p>
<p>
It would return a position index where the maximum value is found when one of the following attributes is specified:
</p>
<ul>
<li><code>:index</code> .. an index of the maximum value.</li>
<li><code>:last_index</code> .. an index where the maximum value is found at last.</li>
<li><code>:indices</code> .. a list of all indices where the maximum value is found.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">iterable#mean</strong></div>
<div style="margin-bottom:1em"><code>iterable#mean()</code></div>
Calculates an average of elements in the iterable.
</p>
<p>
It can work on an iterable with elements of type that supports addition and division operators. Below is a list of acceptable value types:
</p>
<ul>
<li><code>number</code></li>
<li><code>complex</code></li>
<li><code>rational</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">iterable#min</strong></div>
<div style="margin-bottom:1em"><code>iterable#min():[index,indices,last_index]</code></div>
Returns the minimum value in the iterable.
</p>
<p>
It would return a position index where the minimum value is found when one of the following attributes is specified:
</p>
<ul>
<li><code>:index</code> .. an index of the minimum value.</li>
<li><code>:last_index</code> .. an index where the minimum value is found at last.</li>
<li><code>:indices</code> .. a list of all indices where the minimum value is found.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">iterable#nilto</strong></div>
<div style="margin-bottom:1em"><code>iterable#nilto(replace) {block?}</code></div>
Creates an iterator that converts <code>nil</code> in the source iterable to the specified value.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#offset</strong></div>
<div style="margin-bottom:1em"><code>iterable#offset(n:number) {block?}</code></div>
Creates an iterator that returns skips the first <code>n</code> elements in the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].offset(3)
// x generates `D, `E, `F, `G, `H
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#or</strong></div>
<div style="margin-bottom:1em"><code>iterable#or()</code></div>
Calculates a logical OR result of all the values in the iterable.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#pack</strong></div>
<div style="margin-bottom:1em"><code>iterable#pack(format:string) {block?}</code></div>
Creates a <code>binary</code> instance that has packed elements in the iterable according to specifiers in the <code>format</code>.
</p>
<p>
A specifier has a format of "<code>nX</code>" where <code>X</code> is a format character that represents a packing format and <code>n</code> is a number of packing size. The number can be omitted, and it would be treated as <code>1</code> in that case.
</p>
<p>
Following format characters would take a <code>number</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>b</code> .. A one-byte signed number.</li>
<li><code>B</code> .. A one-byte unsigned number.</li>
<li><code>h</code> .. A two-byte signed number.</li>
<li><code>H</code> .. A two-byte unsigned number.</li>
<li><code>i</code> .. A four-byte signed number.</li>
<li><code>I</code> .. A four-byte unsigned number.</li>
<li><code>l</code> .. A four-byte signed number.</li>
<li><code>L</code> .. A four-byte unsigned number.</li>
<li><code>q</code> .. A eight-byte signed number.</li>
<li><code>Q</code> .. A eight-byte unsigned number.</li>
<li><code>f</code> .. A float-typed number occupying four bytes.</li>
<li><code>d</code> .. A double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code>n</code> means the number of values to be packed.
</p>
<p>
Following format characters would take a <code>string</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>s</code> .. Packs a sequence of UTF-8 codes in the string. The packing size <code>n</code> means the size of the room in bytes where the character codes are to be packed. Only the sequence within the allocated room would be packed. If the string length is smaller than the room, the lacking part would be filled with zero.</li>
<li><code>c</code> .. Picks the first byte of the string and packs it as a one-byte unsigned number. The packing size <code>n</code> means the number of values to be packed.</li>
</ul>
<p>
Following format character would take no value from the argument list.
</p>
<ul>
<li><code>x</code> .. Fills the binary with zero. The packing size <code>n</code> means the size of the room in bytes to be filled with zero.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code>@</code> .. System-dependent order.</li>
<li><code>=</code> .. System-dependent order.</li>
<li><code>&lt;</code> .. Little endian</li>
<li><code>&gt;</code> .. Big endian</li>
<li><code>!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code>*</code>" for the number of packing size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code>{</code>" and "<code>}</code>" in the format to change coding character set while packing a string with format character "<code>s</code>" from UTF-8.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#pingpong</strong></div>
<div style="margin-bottom:1em"><code>iterable#pingpong(n?:number):[sticky,sticky@top,sticky@btm] {block?}</code></div>
Creates an iterator that iterates elements in the source iterator from top to bottom, and then from bottom to top repeatedly.
</p>
<p>
The argument <code>n</code> specifies the number of elements the created iterator returns. If omitted, it would iterates elements infinitely.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E].pingpong()
// x generates `A, `B, `C, `D, `E, `D, `C, `B, `A, `B, ..
</code></pre>
<p>
The following attributes specify whether the elements on top and bottom are duplicated:
</p>
<ul>
<li><code>:sticky</code> .. Duplicate the top and bottom elements.</li>
<li><code>:sticky@top</code> .. Duplicate the top element.</li>
<li><code>:sticky@btm</code> .. Duplicate the bottom element.</li>
</ul>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E].pingpong():sticky
// x generates `A, `B, `C, `D, `E, `E, `D, `C, `B, `A, `A, `B, ..
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#print</strong></div>
<div style="margin-bottom:1em"><code>iterable#print(stream?:stream:w):void</code></div>
Prints elements to the specified <code>stream</code>.
</p>
<p>
If omitted, they are printed to the standard output.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#printf</strong></div>
<div style="margin-bottom:1em"><code>iterable#printf(format:string, stream?:stream:w):void</code></div>
Prints items in the iterable by using the format.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#println</strong></div>
<div style="margin-bottom:1em"><code>iterable#println(stream?:stream:w):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">iterable#rank</strong></div>
<div style="margin-bottom:1em"><code>iterable#rank(directive?) {block?}</code></div>
Creates an iterable of rank numbers for elements after sorting them.
</p>
<p>
In default, they are sorted in an ascending order. This means that, if two elements <code>x</code> and <code>y</code> has the relationship of <code>x &lt; y</code>, <code>x</code> would be placed before <code>y</code>. You can change the order by specifying the argument <code>directive</code> with the following symbols:
</p>
<ul>
<li><code>`ascend</code> .. Sorts in an ascending order. This is the default.</li>
<li><code>`descend</code> .. Sorts in a descending order.</li>
</ul>
<p>
You can also put a function to the argument <code>directive</code> that takes two arguments <code>x</code> and <code>y</code> and is expected to return numbers below:
</p>
<ul>
<li><code>x == y</code> .. Zero.</li>
<li><code>x &lt; y</code> .. A number less than zero.</li>
<li><code>x &gt; y</code> .. A number greater than zero.</li>
</ul>
<p>
When an attribute :stable is specified, the original order shall be kept for elements that are determined as the same.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#reduce</strong></div>
<div style="margin-bottom:1em"><code>iterable#reduce(accum) {block}</code></div>
Evaluates a block with a parameter format <code>|value, accum|</code> and leaves the result as the next <code>accum</code> value.
</p>
<p>
It returns the final <code>accum</code> value as its result.
</p>
<p>
Below is an example to calculate summation of the elements:
</p>
<pre><code>x = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
n = x.reduce(0) {|value, accum| value + accum}
// n is 55
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#replace</strong></div>
<div style="margin-bottom:1em"><code>iterable#replace(value, replace) {block?}</code></div>
Creates an iterator that replaces the <code>value</code> in the original iterablewith the value of <code>replace</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#reverse</strong></div>
<div style="margin-bottom:1em"><code>iterable#reverse() {block?}</code></div>
Creates an iterator that iterates elements in the source iterable from tail to top.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#roundoff</strong></div>
<div style="margin-bottom:1em"><code>iterable#roundoff(threshold:number =&gt; 1e-10) {block?}</code></div>
Creates an iterator that replaces a number with zero if it is less than the specified <code>threshold</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#runlength</strong></div>
<div style="margin-bottom:1em"><code>iterable#runlength() {block?}</code></div>
Creates an iterator that counts the number of consecutive same value and generates elements in a form of <code>[cnt, value]</code> where <code>cnt</code> indicates how many <code>value</code> appears in a row.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `A, `B, `C, `C, `C, `D, `D].runlength()
// x generates [2, `A], [1, `B], [3, `C], [2, `D]
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#since</strong></div>
<div style="margin-bottom:1em"><code>iterable#since(criteria) {block?}</code></div>
Creates an iterator that picks up each element in the iterable since criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#skip</strong></div>
<div style="margin-bottom:1em"><code>iterable#skip(n:number) {block?}</code></div>
Creates an iterator that skips <code>n</code> elements before picking up next element.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].skip(2)
// x generates `A, `D, `G
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#skipnil</strong></div>
<div style="margin-bottom:1em"><code>iterable#skipnil() {block?}</code></div>
Creates an iterator that skips <code>nil</code> in the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre><code>x = [`A, nil, `C, nil, nil, `F, nil, `H].skipnil()
// x generates `A, `C, `F, `H
</code></pre>
<p>
<div><strong style="text-decoration:underline">iterable#sort</strong></div>
<div style="margin-bottom:1em"><code>iterable#sort(directive?, keys[]?):[stable] {block?}</code></div>
Creates an iterator of elements after sorting them.
</p>
<p>
In default, they are sorted in an ascending order. This means that, if two elements <code>x</code> and <code>y</code> has the relationship of <code>x &lt; y</code>, <code>x</code> would be placed before <code>y</code>. You can change the order by specifying the argument <code>directive</code> with the following symbols:
</p>
<ul>
<li><code>`ascend</code> .. Sorts in an ascending order. This is the default.</li>
<li><code>`descend</code> .. Sorts in a descending order.</li>
</ul>
<p>
You can also put a function to the argument <code>directive</code> that takes two arguments <code>x</code> and <code>y</code> and is expected to return numbers below:
</p>
<ul>
<li><code>x == y</code> .. Zero.</li>
<li><code>x &lt; y</code> .. A number less than zero.</li>
<li><code>x &gt; y</code> .. A number greater than zero.</li>
</ul>
<p>
When an attribute :stable is specified, the original order shall be kept for elements that are determined as the same. If the argument <code>keys</code> is specified, it would be used as a key instead of element values.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#std</strong></div>
<div style="margin-bottom:1em"><code>iterable#std():[p]</code></div>
Calculates a standard deviation of elements in the iterable.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#sum</strong></div>
<div style="margin-bottom:1em"><code>iterable#sum()</code></div>
Calculates a summation of elements in the iterable.
</p>
<p>
It can work on an iterable with elements of a value type that supports addition operator. Below is a list of acceptable value types:
</p>
<ul>
<li><code>number</code></li>
<li><code>complex</code></li>
<li><code>string</code></li>
<li><code>rational</code></li>
<li><code>timedelta</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">iterable#tail</strong></div>
<div style="margin-bottom:1em"><code>iterable#tail(n:number) {block?}</code></div>
Creates an iterator that takes the last <code>n</code> elements from the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#until</strong></div>
<div style="margin-bottom:1em"><code>iterable#until(criteria) {block?}</code></div>
Creates an iterator that picks up each element in the list until criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#var</strong></div>
<div style="margin-bottom:1em"><code>iterable#var():[p]</code></div>
Calculates a variance of elements in the iterable.
</p>
<p>
<div><strong style="text-decoration:underline">iterable#while</strong></div>
<div style="margin-bottom:1em"><code>iterable#while (criteria) {block?}</code></div>
Creates an iterator that picks up each element in the list while criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">5.34</span><a name="anchor-5-34"></a>memory Class</h2>
<h3><span class="caption-index-3">5.34.1</span><a name="anchor-5-34-1"></a>Overview</h3>
<p>
An instance of the <code>memory</code> class represents a memory that is stored in <code>array</code> instances.
</p>
<h3><span class="caption-index-3">5.34.2</span><a name="anchor-5-34-2"></a>Property</h3>
<p>
A <code>memory</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>p</code></td>
<td>
<code>pointer</code></td>
<td>
R</td>

<td>
Returns a <code>pointer</code> instance that accesses the memory. This result is equivalent to that of calling the method <code>memory#pointer()</code>.</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the memory size in bytes.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.34.3</span><a name="anchor-5-34-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">memory</strong></div>
<div style="margin-bottom:1em"><code>memory(bytes:number):map {block?}</code></div>

</p>
<h3><span class="caption-index-3">5.34.4</span><a name="anchor-5-34-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">memory#array@int8</strong></div>
<div style="margin-bottom:1em"><code>memory#array@int8():map {block?}</code></div>
Creates an <code>array@int8</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@uint8</strong></div>
<div style="margin-bottom:1em"><code>memory#array@uint8():map {block?}</code></div>
Creates an <code>array@uint8</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@int16</strong></div>
<div style="margin-bottom:1em"><code>memory#array@int16():map {block?}</code></div>
Creates an <code>array@int16</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@uint16</strong></div>
<div style="margin-bottom:1em"><code>memory#array@uint16():map {block?}</code></div>
Creates an <code>array@uint16</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@int32</strong></div>
<div style="margin-bottom:1em"><code>memory#array@int32():map {block?}</code></div>
Creates an <code>array@int32</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@uint32</strong></div>
<div style="margin-bottom:1em"><code>memory#array@uint32():map {block?}</code></div>
Creates an <code>array@uint32</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@int64</strong></div>
<div style="margin-bottom:1em"><code>memory#array@int64():map {block?}</code></div>
Creates an <code>array@int64</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@uint64</strong></div>
<div style="margin-bottom:1em"><code>memory#array@uint64():map {block?}</code></div>
Creates an <code>array@uint64</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@float</strong></div>
<div style="margin-bottom:1em"><code>memory#array@float():map {block?}</code></div>
Creates an <code>array@float</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#array@double</strong></div>
<div style="margin-bottom:1em"><code>memory#array@double():map {block?}</code></div>
Creates an <code>array@double</code> instance that accesses the content of the target <code>memory</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">memory#dump</strong></div>
<div style="margin-bottom:1em"><code>memory#dump(stream?:stream:w):void:[upper]</code></div>
Prints a hexadecimal dump from the content of the <code>memory</code> to the standard output. If the argument <code>stream</code> is specified, the result would be output to the stream.
</p>
<p>
In default, hexadecimal digit are printed with lower-case characters. Specifying an attribute <code>:upper</code> would output them with upper-case characters instead.
</p>
<p>
Example:
</p>
<pre><code>&gt;&gt;&gt; b'A quick brown fox jumps over the lazy dog.'.dump():upper
41 20 71 75 69 63 6B 20 62 72 6F 77 6E 20 66 6F  A quick brown fo
78 20 6A 75 6D 70 73 20 6F 76 65 72 20 74 68 65  x jumps over the
20 6C 61 7A 79 20 64 6F 67 2E                     lazy dog.
</code></pre>
<p>
<div><strong style="text-decoration:underline">memory#pointer</strong></div>
<div style="margin-bottom:1em"><code>memory#pointer(offset?:number) {block?}</code></div>
Returns a <code>pointer</code> instance that has an initial offset specified by the argument <code>offset</code>. If the argument is omitted, it would return a <code>pointer</code> instance that points to the top of the memory.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|p:pointer|</code>, where <code>p</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">5.35</span><a name="anchor-5-35"></a>nil Class</h2>
<h3><span class="caption-index-3">5.35.1</span><a name="anchor-5-35-1"></a>Overview</h3>
<p>
The <code>nil</code> class is the class of <code>nil</code> value that is usually used as an invalid value. In a logical operation, the <code>nil</code> value is recognized as <code>false</code>. 
</p>
<h2><span class="caption-index-2">5.36</span><a name="anchor-5-36"></a>number Class</h2>
<h3><span class="caption-index-3">5.36.1</span><a name="anchor-5-36-1"></a>Overview</h3>
<p>
The <code>number</code> class is a type of number values. A number literal would create a <code>number</code> instance.
</p>
<h3><span class="caption-index-3">5.36.2</span><a name="anchor-5-36-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">number.roundoff</strong></div>
<div style="margin-bottom:1em"><code>number.roundoff(threshold:number =&gt; 1e-10)</code></div>

</p>
<h2><span class="caption-index-2">5.37</span><a name="anchor-5-37"></a>operator Class</h2>
<h3><span class="caption-index-3">5.37.1</span><a name="anchor-5-37-1"></a>Overview</h3>
<p>
The <code>operator</code> class provides measures to assign operators with a user-defined procedure.
</p>
<h3><span class="caption-index-3">5.37.2</span><a name="anchor-5-37-2"></a>Property</h3>
<p>
An <code>operator</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>symbol</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
A <code>symbol</code> instance that represents the operator's type.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.37.3</span><a name="anchor-5-37-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">operator</strong></div>
<div style="margin-bottom:1em"><code>operator(symbol:symbol):map {block?}</code></div>
Creates an <code>operator</code> instance that is associated with the specified symbol.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|op:operator|</code>, where <code>op</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Below is an example to create an <code>operator</code> instance that is associated with the plus symbol.
</p>
<pre><code>op = operator(`+)
</code></pre>
<h3><span class="caption-index-3">5.37.4</span><a name="anchor-5-37-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">operator#assign</strong></div>
<div style="margin-bottom:1em"><code>operator#assign(type_l:expr, type_r?:expr):map:void {block}</code></div>
Associates the <code>operator</code> instance with a procedure described in <code>block</code> that takes values as a block parameter and returns its operation result.
</p>
<p>
Some <code>operator</code> instances have two forms of expression: unary and binary. This method assignes the procedure to one of them according to how it takes its arguments as below:
</p>
<ul>
<li><code>operator#assign(type:expr)</code> .. Assigns procedure to the unary form.</li>
<li><code>operator#assign(type_l:expr, type_r:expr)</code> .. Assignes procedure to the binary form.</li>
</ul>
<p>
They take different format of block parameters as below:
</p>
<ul>
<li><code>|value|</code> .. For unary form.</li>
<li><code>|value_l, value_r|</code> .. For binary form.</li>
</ul>
<p>
Below is an example to assign a procedure to a unary form of operator <code>-</code>.
</p>
<pre><code>operator(`-).assign(`string) = {|value|
    // any job
}
</code></pre>
<p>
Below is an example to assign a procedure to a binary form of operator <code>-</code>.
</p>
<pre><code>operator(`-).assign(`string, `number) = {|value_l, value_r|
    // any job
}
</code></pre>
<p>
<div><strong style="text-decoration:underline">operator#entries</strong></div>
<div style="margin-bottom:1em"><code>operator#entries(type?:symbol)</code></div>
Returns a list that contains type expressions that the operator can accept as its arguments.
</p>
<p>
The argument <code>type</code> takes a symbol <code>`binary</code> or <code>`unary</code>.
</p>
<ul>
<li>If it's omitted or specified with <code>`binary</code>, the method would return a list of pairs of type expressions for its left element and right one.</li>
<li>If it's specified with <code>`unary</code>, the method would return a list of type expressions for its single element.</li>
</ul>
<h2><span class="caption-index-2">5.38</span><a name="anchor-5-38"></a>palette Class</h2>
<h3><span class="caption-index-3">5.38.1</span><a name="anchor-5-38-1"></a>Overview</h3>
<p>
The <code>palette</code> instance has a set of <code>color</code> instance.
</p>
<h3><span class="caption-index-3">5.38.2</span><a name="anchor-5-38-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">palette</strong></div>
<div style="margin-bottom:1em"><code>palette(type) {block?}</code></div>
Creates a <code>palette</code> instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|plt:palette|</code>, where <code>plt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
This function can be called in the following two forms:
</p>
<ul>
<li><code>palette(n:number)</code> .. Creates an instance with the specified number of entries. All the entries are initialized with a color of black.</li>
<li><code>palette(type:symbol)</code> .. Creates an instance initialized with a pre-defined set of entries associated with the specified symbol.</li>
</ul>
<p>
In the second form, it can take one of the following symbols:
</p>
<ul>
<li><code>`basic</code> .. A palette with 16 basic colors that are: <code>color.black</code>, <code>color.maroon</code>, <code>color.green</code>, <code>color.olive</code>, <code>color.navy</code>, <code>color.purple</code>, <code>color.teal</code>, <code>color.gray</code>, <code>color.silver</code>, <code>color.red</code>, <code>color.lime</code>, <code>color.yellow</code>,  <code>color.blue</code>, <code>color.fuchsia</code>, <code>color.aqua</code> and <code>color.white</code>.</li>
<li><code>`win256</code> .. A palette with 256 colors defined by Windows.</li>
<li><code>`websafe</code> .. A palette with 216 colors that assure to be displayed correctly in any Web environments. It actually has 256 entries though the last 40 entries are initialized with black.</li>
</ul>
<h3><span class="caption-index-3">5.38.3</span><a name="anchor-5-38-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">palette#each</strong></div>
<div style="margin-bottom:1em"><code>palette#each() {block?}</code></div>
Creates an iterator that iterates each element in the palette.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">palette#nearest</strong></div>
<div style="margin-bottom:1em"><code>palette#nearest(color:color):map:[index]</code></div>
Returns a <code>color</code> instance in the palette that is the nearest with the specified color.
</p>
<p>
If the attribute <code>:index</code> is specified, it would return an index of the nearst entry instead of its <code>color</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">palette#shrink</strong></div>
<div style="margin-bottom:1em"><code>palette#shrink():reduce:[align]</code></div>
Shrinks the size of the palette to a number powered by two that is enough to contain unique entries. The ordef of existing entries will be kept intact.
</p>
<p>
<div><strong style="text-decoration:underline">palette#updateby</strong></div>
<div style="margin-bottom:1em"><code>palette#updateby(image_or_palette):reduce:[align,shrink]</code></div>
Updates palette entries according to color data in an image or a palette.
</p>
<p>
The order of existing entries will be kept intact. If attribute shrink is specified, the whole size will be shrinked to a number powered by two that is enough to contain unique entries.
</p>
<h2><span class="caption-index-2">5.39</span><a name="anchor-5-39"></a>pointer Class</h2>
<h3><span class="caption-index-3">5.39.1</span><a name="anchor-5-39-1"></a>Overview</h3>
<p>
The <code>pointer</code> class provides measures to read and write content in a <code>binary</code> and <code>memory</code> instance.
</p>
<h3><span class="caption-index-3">5.39.2</span><a name="anchor-5-39-2"></a>Property</h3>
<p>
A <code>pointer</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>offset</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
The current offset.</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the size of data accessible from the current offset.</td>
</tr>

<tr>
<td>
<code>size@all</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the entire size of the target binary or memory. This equals to <code>p.offset + p.size</code> where <code>p</code> is a <code>pointer</code> instance.</td>
</tr>

<tr>
<td>
<code>target</code></td>
<td>
<code>any</code></td>
<td>
R</td>

<td>
An instance that is associated with the pointer. Currently, this can be an instance of <code>binary</code> or <code>memory</code>.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.39.3</span><a name="anchor-5-39-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">pointer</strong></div>
<div style="margin-bottom:1em"><code>pointer(org:pointer):map {block?}</code></div>
Creates a <code>pointer</code> instance that is cloned from the given instance <code>org</code>. You can use this to cast a <code>binary</code> and <code>memory</code> instance to the <code>pointer</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|ptr:pointer|</code>, where <code>ptr</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.39.4</span><a name="anchor-5-39-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">pointer#copyfrom</strong></div>
<div style="margin-bottom:1em"><code>pointer#copyfrom(src:pointer, bytes?:number):map:reduce</code></div>
Copies data from <code>src</code> to the target pointer.
</p>
<p>
If the argument <code>bytes</code> is specified, it would limit the size of data to be copied. Otherwise, all the data pointerd by <code>src</code> is to be copied.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#copyto</strong></div>
<div style="margin-bottom:1em"><code>pointer#copyto(dst:pointer, bytes?:number):map:reduce</code></div>
Copies data from the target pointer to <code>dst</code>.
</p>
<p>
If the argument <code>bytes</code> is specified, it would limit the size of data to be copied. Otherwise, all the data pointerd by the target instance is to be copied.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#decode</strong></div>
<div style="margin-bottom:1em"><code>pointer#decode(codec:codec, bytes?:number) {block?}</code></div>
Decodes the content of the <code>pointer</code> as a sequence of string characters using <code>codec</code> and returns the result in <code>string</code>.
</p>
<p>
If the argument <code>bytes</code> is specified, it would limit the size of data to be decoded. Otherwise, all the data pointerd by the target instance is to be decoded.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#dump</strong></div>
<div style="margin-bottom:1em"><code>pointer#dump(stream?:stream:w, bytes?:number):reduce:[upper]</code></div>
Prints a hexadecimal dump from the content of the <code>pointer</code> to the standard output. If the argument <code>stream</code> is specified, the result would be output to the stream.
</p>
<p>
If the argument <code>bytes</code> is specified, it would limit the size of data to be dumped. Otherwise, all the data pointerd by the target instance is to be dumped.
</p>
<p>
In default, hexadecimal digit are printed with lower-case characters. Specifying an attribute <code>:upper</code> would output them with upper-case characters instead.
</p>
<p>
Example:
</p>
<pre><code>&gt;&gt;&gt; b'A quick brown fox jumps over the lazy dog.'.p.dump():upper
41 20 71 75 69 63 6B 20 62 72 6F 77 6E 20 66 6F  A quick brown fo
78 20 6A 75 6D 70 73 20 6F 76 65 72 20 74 68 65  x jumps over the
20 6C 61 7A 79 20 64 6F 67 2E                     lazy dog.
</code></pre>
<p>
<div><strong style="text-decoration:underline">pointer#encodeuri</strong></div>
<div style="margin-bottom:1em"><code>pointer#encodeuri(bytes?:number) {block?}</code></div>
Returns a string in which non-URIC characters are converted to percent-encoded string.
</p>
<p>
For example, <code>b'"Hello"'.p.encodeuri()</code> would return <code>'%22Hello%22'</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@int8</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@int8():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of int8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@uint8</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@uint8():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of uint8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@int16</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@int16():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of int16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@uint16</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@uint16():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of uint16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@int32</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@int32():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of int32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@uint32</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@uint32():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of uint32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@int64</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@int64():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of int64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@uint64</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@uint64():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of uint64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@float</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@float():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of float from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#each@double</strong></div>
<div style="margin-bottom:1em"><code>pointer#each@double():[be] {block?}</code></div>
Creates an iterator that extracts numbers in size of double from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#forward</strong></div>
<div style="margin-bottom:1em"><code>pointer#forward(distance:number):reduce</code></div>
Put the pointer offset forward by <code>distance</code>. If a negative number is specified for the argument, the offset would be put backward.
</p>
<p>
An error would occur when the pointer's offset becomes a negative value while it would be no error when the offset exceeds the target maximum range.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@int8</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@int8():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of int8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@uint8</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@uint8():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of uint8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@int16</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@int16():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of int16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@uint16</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@uint16():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of uint16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@int32</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@int32():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of int32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@uint32</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@uint32():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of uint32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@int64</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@int64():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of int64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@uint64</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@uint64():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of uint64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@float</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@float():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of float from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#get@double</strong></div>
<div style="margin-bottom:1em"><code>pointer#get@double():[be,nil,stay] {block?}</code></div>
Returns an extracted number in size of double from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code>:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|n:number|</code>, where <code>n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#head</strong></div>
<div style="margin-bottom:1em"><code>pointer#head():reduce</code></div>
Moves the pointer position to the beginning.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#hex</strong></div>
<div style="margin-bottom:1em"><code>pointer#hex(bytes?:number):[carray,cstr,upper] {block?}</code></div>
Converts the binary data into a hexadecimal string.
</p>
<p>
In default, the result string is a sequence of joined hexadecimal values without any space. You can specify the following attribute to change the format:
</p>
<ul>
<li><code>:cstr</code> .. Format of C string.</li>
<li><code>:carray</code> .. Format of C array.</li>
</ul>
<p>
Alphabet characters are described in lower characters unless the attribute <code>:upper</code> is specified.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|str:string|</code>, where <code>str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Example:
</p>
<p>
<table>
<tr>
<th>
Code</th>
<th>
Result</th>
</tr>

<tr>
<td>
<code>b'\x01\x23\xab\xcd'.p.hex()</code></td>
<td>
<code>'0123abcd'</code></td>
</tr>

<tr>
<td>
<code>b'\x01\x23\xab\xcd'.p.hex():upper</code></td>
<td>
<code>'0123ABCD'</code></td>
</tr>

<tr>
<td>
<code>b'\x01\x23\xab\xcd'.p.hex():cstr</code></td>
<td>
<code>'\\x01\\x23\\xab\\xcd'</code></td>
</tr>

<tr>
<td>
<code>b'\x01\x23\xab\xcd'.p.hex():carray</code></td>
<td>
<code>'0x01, 0x23, 0xab, 0xcd'</code></td>
</tr>

</table>

</p>
<p>
<div><strong style="text-decoration:underline">pointer#pack</strong></div>
<div style="margin-bottom:1em"><code>pointer#pack(format:string, values+):reduce:[stay]</code></div>
Packs <code>values</code> in the argument list according to specifiers in the <code>format</code> into a binary and adds it to where the pointer points. The pointer offset is automatically incremented by the added length unless <code>:stay</code> attribute is specified.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
A specifier has a format of "<code>nX</code>" where <code>X</code> is a format character that represents a packing format and <code>n</code> is a number of packing size. The number can be omitted, and it would be treated as <code>1</code> in that case.
</p>
<p>
Following format characters would take a <code>number</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>b</code> .. One-byte signed number.</li>
<li><code>B</code> .. One-byte unsigned number.</li>
<li><code>h</code> .. Two-byte signed number.</li>
<li><code>H</code> .. Two-byte unsigned number.</li>
<li><code>i</code> .. Four-byte signed number.</li>
<li><code>I</code> .. Four-byte unsigned number.</li>
<li><code>l</code> .. Four-byte signed number.</li>
<li><code>L</code> .. Four-byte unsigned number.</li>
<li><code>q</code> .. Eight-byte signed number.</li>
<li><code>Q</code> .. Eight-byte unsigned number.</li>
<li><code>f</code> .. Float-typed number occupying four bytes.</li>
<li><code>d</code> .. Double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code>n</code> means the number of values to be packed.
</p>
<p>
Following format characters would take a <code>string</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code>s</code> .. Packs a sequence of UTF-8 codes in the string. The packing size <code>n</code> means the size of the room in bytes where the character codes are to be packed. Only the sequence within the allocated room would be packed. If the string length is smaller than the room, the lacking part would be filled with zero.</li>
<li><code>c</code> .. Picks the first byte of the string and packs it as a one-byte unsigned number. The packing size <code>n</code> means the number of values to be packed.</li>
</ul>
<p>
Following format character would take no value from the argument list.
</p>
<ul>
<li><code>x</code> .. Fills the binary with zero. The packing size <code>n</code> means the size of the room in bytes to be filled with zero.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code>@</code> .. System-dependent order.</li>
<li><code>=</code> .. System-dependent order.</li>
<li><code>&lt;</code> .. Little endian</li>
<li><code>&gt;</code> .. Big endian</li>
<li><code>!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code>*</code>" for the number of packing size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code>{</code>" and "<code>}</code>" in the format to change coding character set from UTF-8 while packing a string with format character "<code>s</code>".
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@int8</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@int8(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of int8.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@uint8</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@uint8(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of uint8.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@int16</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@int16(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of int16.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@uint16</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@uint16(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of uint16.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@int32</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@int32(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of int32.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@uint32</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@uint32(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of uint32.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@int64</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@int64(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of int64.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@uint64</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@uint64(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of uint64.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@float</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@float(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of float.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#put@double</strong></div>
<div style="margin-bottom:1em"><code>pointer#put@double(n:number):map:reduce:[be,stay]</code></div>
Stores the specified number to the current pointer position in size of double.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code>:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#reader</strong></div>
<div style="margin-bottom:1em"><code>pointer#reader() {block?}</code></div>
Creates a <code>stream</code> instance with which you can read data from the memory pointerd by the pointer. If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#seek</strong></div>
<div style="margin-bottom:1em"><code>pointer#seek(offset:number):reduce</code></div>
Moves the pointer position to the specified <code>offset</code>.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#tail</strong></div>
<div style="margin-bottom:1em"><code>pointer#tail():reduce</code></div>
Moves the pointer position to the end.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#unpack</strong></div>
<div style="margin-bottom:1em"><code>pointer#unpack(format:string, values*:number):[nil,stay] {block?}</code></div>
Extracts values from data sequence pointed by the <code>pointer</code> instance according to specifiers in the <code>format</code> and returns a list containing the values.
</p>
<p>
A specifier has a format of "<code>nX</code>" where <code>X</code> is a format character that represents a packing format and <code>n</code> is a number of packing size. The number can be omitted, and it would be treated as <code>1</code> in that case.
</p>
<p>
Following format characters would extract an integer or float value of specified size from the binary and returns a <code>number</code> value.
</p>
<ul>
<li><code>b</code> .. One-byte signed number.</li>
<li><code>B</code> .. One-byte unsigned number.</li>
<li><code>h</code> .. Two-byte signed number.</li>
<li><code>H</code> .. Two-byte unsigned number.</li>
<li><code>i</code> .. Four-byte signed number.</li>
<li><code>I</code> .. Four-byte unsigned number.</li>
<li><code>l</code> .. Four-byte signed number.</li>
<li><code>L</code> .. Four-byte unsigned number.</li>
<li><code>q</code> .. Eight-byte signed number.</li>
<li><code>Q</code> .. Eight-byte unsigned number.</li>
<li><code>f</code> .. Float-typed number occupying four bytes.</li>
<li><code>d</code> .. Double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code>n</code> means the number of values to be extracted.
</p>
<p>
Following format characters would extract a string sequence from the binary and returns a <code>string</code> value.
</p>
<ul>
<li><code>s</code> .. Extracts a sequence of UTF-8 codes and returns <code>string</code> instance containing it. The unpacking size <code>n</code> means the size of the room in bytes where the character codes are to be unpacked.</li>
<li><code>c</code> .. Extracts a one-byte unsigned number and returns a <code>string</code> instance containing it. The unpacking size <code>n</code> means the number of values to be extracted.</li>
</ul>
<p>
Following format character would not return any value.
</p>
<ul>
<li><code>x</code> .. Advances the address by one byte. If the unpacking size <code>n</code> is specifies, it would advance the address by <code>n</code> bytes.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code>@</code> .. System-dependent order.</li>
<li><code>=</code> .. System-dependent order.</li>
<li><code>&lt;</code> .. Little endian</li>
<li><code>&gt;</code> .. Big endian</li>
<li><code>!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code>*</code>" for the number of unpacking size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code>{</code>" and "<code>}</code>" in the format to change coding character set from UTF-8 while extracting a string with format character "<code>s</code>".
</p>
<p>
An error occurs if the binary size is smaller than the format reqeusts. If the attribute <code>:nil</code> is specified, <code>nil</code> value would be returned for such a case.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|list:list|</code>, where <code>list</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#unpacks</strong></div>
<div style="margin-bottom:1em"><code>pointer#unpacks(format:string, values*:number):map {block?}</code></div>
Returns an iterator that extracts values from data pointed by the <code>pointer</code> instance according to specifiers in <code>format</code>.
</p>
<p>
For detailed information about specifiers, see the help of <code>pointer#unpack()</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|iter:iterator|</code>, where <code>iter</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">pointer#writer</strong></div>
<div style="margin-bottom:1em"><code>pointer#writer() {block?}</code></div>
Creates a <code>stream</code> instance with which you can append data to the memory pointed by the pointer. If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.39.5</span><a name="anchor-5-39-5"></a>Cast Operation</h3>
<p>
A function that expects a <code>pointer</code> instance in its argument can also take a value of <code>binary</code> and <code>memory</code>.
</p>
<p>
With the above casting feature, you can call a function <code>f(p:pointer)</code> that takes a <code>pointer</code> instance in its argument as below:
</p>
<ul>
<li><code>b = b'\x01\x23\x45\x67\x89\xab', f(b)</code></li>
<li><code>m = memory(32), f(m)</code> </li>
</ul>
<h2><span class="caption-index-2">5.40</span><a name="anchor-5-40"></a>rational Class</h2>
<h3><span class="caption-index-3">5.40.1</span><a name="anchor-5-40-1"></a>Overview</h3>
<p>
The <code>rational</code> class provides measures to handle rational numbers.
</p>
<p>
You can create a <code>rational</code> instance with following ways:
</p>
<ul>
<li>Use <code>rational()</code> function.</li>
<li>Append <code>r</code> suffix after a number literal.</li>
</ul>
<p>
Below are examples to realize a common fraction two-thirds:
</p>
<pre><code>rational(2, 3)
2r / 3
2 / 3r
</code></pre>
<h3><span class="caption-index-3">5.40.2</span><a name="anchor-5-40-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">rational</strong></div>
<div style="margin-bottom:1em"><code>rational(numer:number, denom?:number):map {block?}</code></div>
Creates a rational value from given numerator <code>numer</code> and denominator <code>denom</code>.
</p>
<p>
If the argument <code>denom</code> is omitted, one is set as its denominator.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|r:rational|</code>, where <code>r</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.40.3</span><a name="anchor-5-40-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">rational.reduce</strong></div>
<div style="margin-bottom:1em"><code>rational.reduce()</code></div>
Reduces the rational number by dividing its numerator and denominator by their GCD.
</p>
<h2><span class="caption-index-2">5.41</span><a name="anchor-5-41"></a>semaphore Class</h2>
<h3><span class="caption-index-3">5.41.1</span><a name="anchor-5-41-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.41.2</span><a name="anchor-5-41-2"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">semaphore</strong></div>
<div style="margin-bottom:1em"><code>semaphore()</code></div>

</p>
<h3><span class="caption-index-3">5.41.3</span><a name="anchor-5-41-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">semaphore#release</strong></div>
<div style="margin-bottom:1em"><code>semaphore#release()</code></div>
Releases the owership of the semaphore that is grabbed by semaphore#wait().
</p>
<p>
<div><strong style="text-decoration:underline">semaphore#session</strong></div>
<div style="margin-bottom:1em"><code>semaphore#session() {block}</code></div>
Forms a critical session by grabbing the semaphore's ownership, executing the block and releasing that ownership. It internally proccesses the same job as semaphore#wait() and semaphore#release() before and after the block execution
</p>
<p>
<div><strong style="text-decoration:underline">semaphore#wait</strong></div>
<div style="margin-bottom:1em"><code>semaphore#wait()</code></div>
Watis for the semaphore being released by other threads, and ghen grabs that ownership.
</p>
<h2><span class="caption-index-2">5.42</span><a name="anchor-5-42"></a>stream Class</h2>
<h3><span class="caption-index-3">5.42.1</span><a name="anchor-5-42-1"></a>Overview</h3>
<p>
The <code>stream</code> class provides methods to read and write data through a stream, an abstract structure to handle a byte sequence. It also provides information of the stream such as the pathname and the creation date and time.
</p>
<p>
You can specify a proper <code>codec</code> when creating the <code>stream</code> instance, which is used to decode/encode character codes that appear in the stream. Features of <code>codec</code> would affect on functions and methods that handle text data like follows:
</p>
<ul>
<li>Decode<ul>
<li>readlines()</li>
<li>stream#readchar()</li>
<li>stream#readline()</li>
<li>stream#readlines()</li>
<li>stream#readtext()</li>
</ul>
</li>
<li>Encode<ul>
<li>operator <code>&lt;&lt;</code></li>
<li>stream#print()</li>
<li>stream#printf()</li>
<li>stream#println()</li>
</ul>
</li>
</ul>
<h3><span class="caption-index-3">5.42.2</span><a name="anchor-5-42-2"></a>Property</h3>
<p>
A <code>stream</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>codec</code></td>
<td>
<code>codec</code></td>
<td>
R</td>

<td>
A <code>codec</code> instance associated with the stream.</td>
</tr>

<tr>
<td>
<code>identifier</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Identifier of the stream.</td>
</tr>

<tr>
<td>
<code>name</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Name of the stream.</td>
</tr>

<tr>
<td>
<code>readable</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
Indicates whether the stream is readable.</td>
</tr>

<tr>
<td>
<code>stat</code></td>
<td>
<code>any</code></td>
<td>
R</td>

<td>
Status of the stream.</td>
</tr>

<tr>
<td>
<code>writable</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
Indicates whether the stream is writable.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.42.3</span><a name="anchor-5-42-3"></a>Operator</h3>
<p>
You can use the operator "<code>&lt;&lt;</code>" to output a content of a value to a <code>stream</code>. It comes like "<code>stream &lt;&lt; obj</code>" where <code>obj</code> is converted to a string before output to the stream.
</p>
<pre><code>sys.stdout &lt;&lt; 'Hello World.'
</code></pre>
<p>
Since the operator returns the <code>stream</code> instance specified on the left as its result, you can chain multiple operations as below:
</p>
<pre><code>sys.stdout &lt;&lt; 'First' &lt;&lt; 'Second'
</code></pre>
<h3><span class="caption-index-3">5.42.4</span><a name="anchor-5-42-4"></a>Cast Operation</h3>
<p>
A function that expects a <code>stream</code> instance in its argument can also take a value of <code>string</code> and <code>binary</code> as below:
</p>
<ul>
<li><code>string</code> .. Recognized the <code>string</code> as a path name from which <code>stream</code> instance is created.</li>
<li><code>binary</code> .. Creates a <code>stream</code> instance that reads or modifies the content of the specified <code>binary</code> data. If the <code>binary</code> data is a constant one, which might be created from a binary literal such as <code>b'\x00\x12\x34\x56'</code>, the stream is created with read-only attribute.</li>
</ul>
<p>
Using the above casting feature, you can call a function <code>f(stream:stream)</code> that takes a <code>stream</code> instance in its argument as below:
</p>
<ul>
<li><code>f(stream('foo.txt'))</code> .. The most explicit way.</li>
<li><code>f('foo.txt')</code> .. Implicit casting from <code>string</code> to <code>stream</code>.</li>
<li><code>f(b'\x00\x12\x34\x56')</code> .. Implicit casting from <code>binary</code> to <code>stream</code> that reads the content.</li>
</ul>
<h3><span class="caption-index-3">5.42.5</span><a name="anchor-5-42-5"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">stream</strong></div>
<div style="margin-bottom:1em"><code>stream(pathname:string, mode?:string, codec?:codec):map {block?}</code></div>
Creates a <code>stream</code> instance from the specified <code>pathname</code>.
</p>
<p>
The argument <code>mode</code> takes one of the strings that specifies what access should be allowed with the stream. If omitted, the stream would be opened with read mode.
</p>
<ul>
<li><code>'r'</code> .. read</li>
<li><code>'w'</code> .. write</li>
<li><code>'a'</code> .. append</li>
</ul>
<p>
The argument <code>codec</code> specifies a name of the character codec that converts between the stream's character code and UTF-8, which is a code used in the iterpreter's internal process.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
You can also call <code>open()</code> function that is just an alias of <code>stream()</code> to create a <code>stream</code> instance.
</p>
<h3><span class="caption-index-3">5.42.6</span><a name="anchor-5-42-6"></a>Utility Function</h3>
<p>
<div><strong style="text-decoration:underline">readlines</strong></div>
<div style="margin-bottom:1em"><code>readlines(stream?:stream:r):[chop] {block?}</code></div>
Creates an iterator that reads text from the specified stream line by line.
</p>
<p>
If attribute <code>:chop</code> is specified, it eliminates an end-of-line character that appears at the end of each line.
</p>
<p>
This function decodes character codes in the stream using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h3><span class="caption-index-3">5.42.7</span><a name="anchor-5-42-7"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">stream#addcr</strong></div>
<div style="margin-bottom:1em"><code>stream#addcr(flag?:boolean):reduce</code></div>
The codec's encoder in the stream has a feature to add a CR code (<code>0x0d</code>) before a LF code (<code>0x0a</code>) so that the lines are joined with CR-LF codes in the encoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">stream#close</strong></div>
<div style="margin-bottom:1em"><code>stream#close():void</code></div>
Closes the stream.
</p>
<p>
<div><strong style="text-decoration:underline">stream#compare</strong></div>
<div style="margin-bottom:1em"><code>stream#compare(stream:stream:r):map</code></div>
Returns <code>true</code> if there's no difference between the binary sequences of the target stream instance and that of <code>stream</code> in the argument.
</p>
<p>
<div><strong style="text-decoration:underline">stream.copy</strong></div>
<div style="margin-bottom:1em"><code>stream.copy(src:stream:r, dst:stream:w, bytesunit:number =&gt; 65536):static:map:void:[finalize] {block?}</code></div>
Copies the content in <code>src</code> to the stream <code>dst</code>.
</p>
<p>
The copy process is done by the following steps:
</p>
<ol>
<li>Reads data from stream <code>src</code> into a buffer with the size specified by <code>bytesunit</code>.</li>
<li>(1) If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code> where <code>buff</code> contains the read data. When the block's result is a <code>binary</code> instance, the content would be written to the stream <code>dst</code>. Otherwise, the read data would be written to stream <code>dst</code>. (2) If <code>block</code> is not specified, the read data would be written to stream <code>dst</code>.</li>
<li>Continues from step 1 to 2 until data from <code>src</code> runs out.</li>
</ol>
<p>
If the attribute <code>:finalize</code> is specified, some finalizing process such as copying the time stamp and attributes will be applied at the end.
</p>
<p>
This works the same way as <code>stream#copyfrom()</code> and <code>stream#copyto()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">stream#copyfrom</strong></div>
<div style="margin-bottom:1em"><code>stream#copyfrom(src:stream:r, bytesunit:number =&gt; 65536):map:reduce:[finalize] {block?}</code></div>
Copies the content in <code>src</code> to target stream instance.
</p>
<p>
The copy process is done by the following steps:
</p>
<ol>
<li>Reads data from stream <code>src</code> into a buffer with the size specified by <code>bytesunit</code>.</li>
<li>(1) If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code> where <code>buff</code> contains the read data. When the block's result is a <code>binary</code> instance, the content would be written to the target stream. Otherwise, the read data would be written to the target stream. (2) If <code>block</code> is not specified, the read data would be written to the target stream.</li>
<li>Continues from step 1 to 2 until data from <code>src</code> runs out.</li>
</ol>
<p>
If the attribute <code>:finalize</code> is specified, some finalizing process such as copying the time stamp and attributes will be applied at the end.
</p>
<p>
This works the same way as <code>stream.copy()</code> and <code>stream#copyto()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">stream#copyto</strong></div>
<div style="margin-bottom:1em"><code>stream#copyto(dst:stream:w, bytesunit:number =&gt; 65536):map:reduce:[finalize] {block?}</code></div>
Copies the content in the target stream to the stream <code>dst</code>.
</p>
<p>
The copy process is done by the following steps:
</p>
<ol>
<li>Reads data from the target stream into a buffer with the size specified by <code>bytesunit</code>.</li>
<li>(1) If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code> where <code>buff</code> contains the read data. When the block's result is a <code>binary</code> instance, the content would be written to the stream <code>dst</code>. Otherwise, the read data would be written to stream <code>dst</code>. (2) If <code>block</code> is not specified, the read data would be written to stream <code>dst</code>.</li>
<li>Continues from step 1 to 2 until data from the target stream runs out.</li>
</ol>
<p>
If the attribute <code>:finalize</code> is specified, some finalizing process such as copying the time stamp and attributes will be applied at the end.
</p>
<p>
This works the same way as <code>stream.copy()</code> and <code>stream#copyfrom()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">stream#delcr</strong></div>
<div style="margin-bottom:1em"><code>stream#delcr(flag?:boolean):reduce</code></div>
The codec's decoder in the stream has a feature to delete a CR code (<code>0x0d</code>) before a LF code (<code>0x0a</code>) so that the lines are joined with LF code in the decoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code>flag</code> set to <code>true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code>flag</code> set to <code>false</code>.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">stream#deserialize</strong></div>
<div style="margin-bottom:1em"><code>stream#deserialize()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">stream#flush</strong></div>
<div style="margin-bottom:1em"><code>stream#flush():void</code></div>
Flushes cached data to the stream.
</p>
<p>
<div><strong style="text-decoration:underline">stream#peek</strong></div>
<div style="margin-bottom:1em"><code>stream#peek(bytes?:number)</code></div>
Reads specified length of data from the stream and returns a <code>binary</code> instance that contains it. This doesn't move the stream's current file position.
</p>
<p>
<div><strong style="text-decoration:underline">stream#print</strong></div>
<div style="margin-bottom:1em"><code>stream#print(values*):map:void</code></div>
Prints out <code>values</code> to the <code>stream</code> instance after converting them to strings.
</p>
<p>
This function encodes character codes in the string using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
<div><strong style="text-decoration:underline">stream#printf</strong></div>
<div style="margin-bottom:1em"><code>stream#printf(format:string, values*):map:void</code></div>
Prints out <code>values</code> to the <code>stream</code> instance according to formatter specifiers in <code>format</code>.
</p>
<p>
Refer to the help of <code>printf()</code> function to see information about formatter specifiers.
</p>
<p>
This function encodes character codes in the string using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
<div><strong style="text-decoration:underline">stream#println</strong></div>
<div style="margin-bottom:1em"><code>stream#println(values*):map:void</code></div>
Prints out <code>values</code> and an end-of-line character to the <code>stream</code> instanceafter converting them to strings.
</p>
<p>
This function encodes character codes in the string using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
<div><strong style="text-decoration:underline">stream#read</strong></div>
<div style="margin-bottom:1em"><code>stream#read(bytes?:number) {block?}</code></div>
Reads specified length of data from the stream and returns a <code>binary</code> instance that contains it. If the argument <code>bytes</code> is omitted, all the data available from the stream would be read.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|buff:binary|</code>, where <code>buff</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">stream#readchar</strong></div>
<div style="margin-bottom:1em"><code>stream#readchar() {block?}</code></div>
Reads one character from the stream and returns a <code>string</code> instance that contains it.
</p>
<p>
This method decodes character codes in the stream using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|ch:string|</code>, where <code>ch</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">stream#readline</strong></div>
<div style="margin-bottom:1em"><code>stream#readline():[chop] {block?}</code></div>
Reads one line from the stream and returns a <code>string</code> instance that contains it.
</p>
<p>
If the attribute <code>:chop</code> is specified, it would remove the last new line character from the result. This method decodes character codes in the stream using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|line:string|</code>, where <code>line</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">stream#readlines</strong></div>
<div style="margin-bottom:1em"><code>stream#readlines(nlines?:number):[chop] {block?}</code></div>
Creates an iterator that reads text from the specified stream line by line.
</p>
<p>
The argument <code>nlines</code> specifies how many lines should be read from the stream. If omitted, it would read all the lines.
</p>
<p>
If attribute <code>:chop</code> is specified, it eliminates an end-of-line character that appears at the end of each line.
</p>
<p>
This method decodes character codes in the stream using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">stream#readtext</strong></div>
<div style="margin-bottom:1em"><code>stream#readtext() {block?}</code></div>
Reads the whole data in the stream as a text sequence and returns a <code>string</code> instance that contains it. This method decodes character codes in the stream using <code>codec</code> instance that is specified when the <code>stream</code> instance is created.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|text:string|</code>, where <code>text</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">stream#seek</strong></div>
<div style="margin-bottom:1em"><code>stream#seek(offset:number, origin?:symbol):reduce</code></div>
Seeks the current file position to the offset specified by the argument <code>offset</code>.
</p>
<p>
The argument <code>origin</code> specifies the meaning of <code>offset</code> value as follows:
</p>
<ul>
<li><code>set` ... `offset` is an absolute offset from the begining of the stream.</code></li>
<li><code>cur` ... `offset` is a relative offset from the current position.</code></li>
</ul>
<p>
This method returns the target stream instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">stream#serialize</strong></div>
<div style="margin-bottom:1em"><code>stream#serialize(value):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">stream#setcodec</strong></div>
<div style="margin-bottom:1em"><code>stream#setcodec(codec:codec:nil):reduce</code></div>
Sets <code>codec</code> instance to the target stream. If <code>nil</code> is specified for the argument, the current <code>codec</code> instance would be removed.
</p>
<p>
This method returns the target stream instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">stream#tell</strong></div>
<div style="margin-bottom:1em"><code>stream#tell()</code></div>
Returns the current file position at which read/write operation works.
</p>
<p>
<div><strong style="text-decoration:underline">stream#write</strong></div>
<div style="margin-bottom:1em"><code>stream#write(ptr:pointer, bytes?:number):reduce</code></div>
Writes binary data pointer by <code>ptr</code> to the stream. The argument <code>bytes</code> limits the number of data that is to be written to the stream.
</p>
<h2><span class="caption-index-2">5.43</span><a name="anchor-5-43"></a>string Class</h2>
<h3><span class="caption-index-3">5.43.1</span><a name="anchor-5-43-1"></a>Overview</h3>
<p>
The <code>string</code> class provides measures to operate on strings.
</p>
<p>
You can create a <code>string</code> instance by embracing a sequence of characters with a pair of single- or double-quotes.
</p>
<pre><code>'Hello World'

"Hello World"
</code></pre>
<p>
If you need to declare a string that contains multiple lines, embrace it with a pair of sequences of three single- or double-quotes.
</p>
<pre><code>R"""
first line
second line
third line
"""
</code></pre>
<h3><span class="caption-index-3">5.43.2</span><a name="anchor-5-43-2"></a>Suffix Management</h3>
<p>
When an string literal is suffixed by a character <code>$</code>, a handler registered by <code>string.translate()</code> function that is supposed to translate the string into other natural languages would be evaluated.
</p>
<h3><span class="caption-index-3">5.43.3</span><a name="anchor-5-43-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">string#align</strong></div>
<div style="margin-bottom:1em"><code>string#align(width:number, padding:string =&gt; ' '):map:[center,left,right] {block?}</code></div>
Align the string to the left, right or center within the specified <code>width</code> and returns the result.
</p>
<p>
The following attributes specify the alignment position:
</p>
<ul>
<li><code>:center</code> .. Aligns to the center. This is the default.</li>
<li><code>:left</code> .. Aligns to the left</li>
<li><code>:right</code> .. Aligns to the right</li>
</ul>
<p>
If the string width is narrower than the specified <code>width</code>, nothing would be done.
</p>
<p>
It uses a string specified by the argument <code>padding</code> to fill lacking spaces. If omitted, a white space is used for padding.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. A kanji-character occupies two characters in width.
</p>
<p>
<div><strong style="text-decoration:underline">string.binary</strong></div>
<div style="margin-bottom:1em"><code>string.binary() {block?}</code></div>
Converts the string into <code>binary</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">string#capitalize</strong></div>
<div style="margin-bottom:1em"><code>string#capitalize() {block?}</code></div>
Returns a string that capitalizes the first character.
</p>
<p>
<div><strong style="text-decoration:underline">string#chop</strong></div>
<div style="margin-bottom:1em"><code>string#chop(suffix*:string):[eol,icase] {block?}</code></div>
Returns a string that removes a last character.
</p>
<p>
If an attribute <code>:eol</code> is specified, only the end-of-line character shall be removed. In this case, if the end-of-line has a sequence of CR-LF, CR code shall be removed as well.
</p>
<p>
<div><strong style="text-decoration:underline">string#decodeuri</strong></div>
<div style="margin-bottom:1em"><code>string#decodeuri() {block?}</code></div>
Returns a string in which percent-encoded characters are decoded.
</p>
<p>
<div><strong style="text-decoration:underline">string#each</strong></div>
<div style="margin-bottom:1em"><code>string#each():map:[utf32,utf8] {block?}</code></div>
Creates an iterator generating strings of each character in the original one.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">string#eachline</strong></div>
<div style="margin-bottom:1em"><code>string#eachline(nlines?:number):[chop] {block?}</code></div>
Creates an iterator generating strings of each line in the original one.
</p>
<p>
In default, end-of-line characters are involved in the result. You can eliminates them by specifying <code>:chop</code> attribute.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">string#embed</strong></div>
<div style="margin-bottom:1em"><code>string#embed(dst?:stream:w):[lasteol,noindent]</code></div>
Evaluates a string that contains embedded scripts and renders the result to the specified stream.
</p>
<p>
If the stream is omitted, the function returns the rendered result as a string.
</p>
<p>
Calling this method is equivalent to calling a method <code>string#template()</code> to create a <code>template</code> instance on which a method <code>template#render()</code> is applied afterward.
</p>
<p>
<div><strong style="text-decoration:underline">string.encode</strong></div>
<div style="margin-bottom:1em"><code>string.encode(codec:codec) {block?}</code></div>
Encodes the string with the given <code>codec</code> and return the result as a <code>binary</code>.
</p>
<p>
<div><strong style="text-decoration:underline">string#encodeuri</strong></div>
<div style="margin-bottom:1em"><code>string#encodeuri() {block?}</code></div>
Returns a string in which non-URIC characters are percent-encoded.
</p>
<p>
<div><strong style="text-decoration:underline">string#endswith</strong></div>
<div style="margin-bottom:1em"><code>string#endswith(suffix:string, endpos?:number):map:[icase,rest]</code></div>
Returns <code>true</code> if the string ends with suffix.
</p>
<p>
If attribute <code>:rest</code> is specified, it returns the rest part if the string ends with suffix, or <code>nil</code> otherewise. You can specify a bottom position for the matching by an argument <code>endpos</code>.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching.
</p>
<p>
<div><strong style="text-decoration:underline">string#escapehtml</strong></div>
<div style="margin-bottom:1em"><code>string#escapehtml():[quote] {block?}</code></div>
Converts some characters into HTML entity symbols. If attribute <code>:quote</code> is specified, a double-quotation character would be converted to an entity symbol "&quot;".
</p>
<p>
<div><strong style="text-decoration:underline">string#find</strong></div>
<div style="margin-bottom:1em"><code>string#find(sub:string, pos:number =&gt; 0):map:[icase,rev]</code></div>
Finds a sub string from the string and returns its position.
</p>
<p>
Number of position starts from zero. You can specify a position to start finding by an argument pos. It returns nil if finding fails.
</p>
<p>
With an attribute <code>:icase</code>, case of characters are ignored while finding.
</p>
<p>
When an attribute <code>:rev</code>, finding starts from tail of the string
</p>
<p>
<div><strong style="text-decoration:underline">string#fold</strong></div>
<div style="margin-bottom:1em"><code>string#fold(len:number, step?:number):[neat] {block?}</code></div>
Creates an iterator that folds the source string by the specified length.
</p>
<p>
The argument <code>step</code> specifies the length of advancement for the next folding point. If omitted, it would be the same amount as <code>len</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">string#foldw</strong></div>
<div style="margin-bottom:1em"><code>string#foldw(width:number):[padding] {block?}</code></div>
Creates an iterator that folds the source string by the specified width.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">string#format</strong></div>
<div style="margin-bottom:1em"><code>string#format(values*):map</code></div>
Taking the string instance as a printf-styled formatter string, it converts <code>values</code> into a string depending on formatter specifiers in it.
</p>
<p>
<div><strong style="text-decoration:underline">string#isempty</strong></div>
<div style="margin-bottom:1em"><code>string#isempty()</code></div>
Returns <code>true</code> if the string is empty.
</p>
<p>
<div><strong style="text-decoration:underline">string#left</strong></div>
<div style="margin-bottom:1em"><code>string#left(len?:number):map</code></div>
Extracts the specified length of string from left of the source string.
</p>
<p>
If the argument is omitted, it would return whole the source string.
</p>
<p>
<div><strong style="text-decoration:underline">string#len</strong></div>
<div style="margin-bottom:1em"><code>string#len()</code></div>
Returns the length of the string in characters.
</p>
<p>
<div><strong style="text-decoration:underline">string#lower</strong></div>
<div style="margin-bottom:1em"><code>string#lower()</code></div>
Converts upper-case to lower-case characters.
</p>
<p>
<div><strong style="text-decoration:underline">string#mid</strong></div>
<div style="margin-bottom:1em"><code>string#mid(pos:number, len?:number):map {block?}</code></div>
Extracts the specified length of string from the position <code>pos</code> and returns the result.
</p>
<p>
If the argument <code>len</code> is omitted, it returns a string from <code>pos</code> to the end. The number of an argument <code>pos</code> starts from zero.
</p>
<p>
Below are examples:
</p>
<pre><code>'Hello world'.mid(3, 2) // 'lo'
'Hello world'.mid(5)    // 'world'
</code></pre>
<p>
<div><strong style="text-decoration:underline">string.print</strong></div>
<div style="margin-bottom:1em"><code>string.print(stream?:stream:w):void</code></div>
Prints out the string to the specified <code>stream</code>.
</p>
<p>
If the argument is omitted, it would print to the standard output.
</p>
<p>
<div><strong style="text-decoration:underline">string.println</strong></div>
<div style="margin-bottom:1em"><code>string.println(stream?:stream:w):void</code></div>
Prints out the string and a line-break to the specified <code>stream</code>.
</p>
<p>
If the argument is omitted, it would print to the standard output.
</p>
<p>
<div><strong style="text-decoration:underline">string#reader</strong></div>
<div style="margin-bottom:1em"><code>string#reader() {block?}</code></div>
Returns a <code>stream</code> instance that reads the string content as a binary sequence.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#replace</strong></div>
<div style="margin-bottom:1em"><code>string#replace(match:string, sub:string, count?:number):map:[icase] {block?}</code></div>
Replaces sub strings that matches the string <code>match</code> with a string specified by <code>sub</code> and returns the result.
</p>
<p>
The argument <code>count</code> limits the maximum number of substitution. If omitted, there's no limit of the work.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching strings.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|result:string, replaced:boolean|</code>, where <code>result</code> is the result string and <code>replaced</code> indicates if there is any change between the result and its original string. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#replaces</strong></div>
<div style="margin-bottom:1em"><code>string#replaces(map[]:string, count?:number):map:[icase] {block?}</code></div>
Replaces string parts according to a list of pairs of a matching and a substituting string and returns the result.
</p>
<p>
The argument <code>map</code> is a <code>list</code> of match-substitution paris like <code>[match1, sub1, match2, sub2, ..]</code> with which a sub string that matches <code>match</code><em>n</em> would be replaced with <code>sub</code><em>n</em>.
</p>
<p>
The argument <code>count</code> limits the maximum number of substitution. If omitted, there's no limit of the work.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching strings.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|result:string, replaced:boolean|</code>, where <code>result</code> is the result string and <code>replaced</code> indicates if there is any change between the result and its original string. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#right</strong></div>
<div style="margin-bottom:1em"><code>string#right(len?:number):map {block?}</code></div>
Extracts the specified length of string from right of the source string.
</p>
<p>
If the argument is omitted, it would return whole the source string.
</p>
<p>
<div><strong style="text-decoration:underline">string#split</strong></div>
<div style="margin-bottom:1em"><code>string#split(sep?:string, count?:number):[icase] {block?}</code></div>
Creates an iterator generating sub strings extracted from the original one separated by a specified string <code>sep</code>. With an attribute <code>:icase</code>, character cases are ignored while finding the separator.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">string#startswith</strong></div>
<div style="margin-bottom:1em"><code>string#startswith(prefix:string, pos:number =&gt; 0):map:[icase,rest]</code></div>
Returns <code>true</code> if the string starts with <code>prefix</code>.
</p>
<p>
If attribute <code>:rest</code> is specified, it returns the rest part if the string starts with prefix, or <code>nil</code> otherewise. You can specify a top position for the matching by an argument <code>pos</code>.
</p>
<p>
With an attribute <code>:icase</code>, character cases are ignored while matching.
</p>
<p>
<div><strong style="text-decoration:underline">string#strip</strong></div>
<div style="margin-bottom:1em"><code>string#strip():[both,left,right] {block?}</code></div>
Returns a string that removes space characters on the left, the right or the both sides of the original string.
</p>
<p>
The following attributes would specify which side of spaces should be removed:
</p>
<ul>
<li><code>:both</code> .. Removes spaces on both sides. This is the default.</li>
<li><code>:left</code> .. Removes spaces on the left side.</li>
<li><code>:right</code> .. Removes spaces on the right side.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">string#template</strong></div>
<div style="margin-bottom:1em"><code>string#template():[lasteol,noindent] {block?}</code></div>
Parses the content of the string as a text containing embedded scripts and returns a <code>template</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">string#tosymbol</strong></div>
<div style="margin-bottom:1em"><code>string#tosymbol() {block?}</code></div>
Convers the string into a symbol.
</p>
<p>
<div><strong style="text-decoration:underline">string.translator</strong></div>
<div style="margin-bottom:1em"><code>string.translator():static:void {block}</code></div>
Register a procedure evaluated when a string literal appears with a suffix symbol "<code>$</code>", which is meant to translate the string into another language.
</p>
<p>
The procedure is described in <code>block</code> takes a block parameter <code>|str:string|</code> where <code>str</code> is the original string, and is expected to return a string translated from the original.
</p>
<p>
<div><strong style="text-decoration:underline">string#unescapehtml</strong></div>
<div style="margin-bottom:1em"><code>string#unescapehtml() {block?}</code></div>
Converts escape sequences into readable characters.
</p>
<p>
<div><strong style="text-decoration:underline">string#upper</strong></div>
<div style="margin-bottom:1em"><code>string#upper() {block?}</code></div>
Converts lower-case to upper-case characters.
</p>
<p>
<div><strong style="text-decoration:underline">string#width</strong></div>
<div style="margin-bottom:1em"><code>string#width()</code></div>
Returns the width of the string.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. For example, a kanji-character of Japanese occupies two characters in width.
</p>
<p>
<div><strong style="text-decoration:underline">string#zentohan</strong></div>
<div style="margin-bottom:1em"><code>string#zentohan() {block?}</code></div>
Converts zenkaku to hankaku characters.
</p>
<h2><span class="caption-index-2">5.44</span><a name="anchor-5-44"></a>suffixmgr Class</h2>
<h3><span class="caption-index-3">5.44.1</span><a name="anchor-5-44-1"></a>Overview</h3>
<p>
The <code>suffixmgr</code> class provides measures to access suffix managers that are responsible to handle suffix symbols appended to number or string literals.
</p>
<p>
Below is an example to register a suffix <code>X</code> that converts a string into upper case after being appended to a string literal:
</p>
<pre><code>suffixmgr(`string).assign(`X) {|body| body.upper()}
</code></pre>
<p>
You can use that suffix like below:
</p>
<pre><code>'hello world'X
</code></pre>
<h5><span class="caption-index-5">5.44.1.0.1</span><a name="anchor-5-44-1-0-1"></a>Constructor</h5>
<p>
<div><strong style="text-decoration:underline">suffixmgr</strong></div>
<div style="margin-bottom:1em"><code>suffixmgr(type:symbol) {block?}</code></div>
Creates a reference to one of two suffix managers, number and string.
</p>
<ul>
<li>The number suffix manager works with number literals.</li>
<li>The string suffix manager works with string literals.</li>
</ul>
<p>
Specify the argument <code>type</code> with a symbol <code>`number</code> for a number suffix manager and <code>`string</code> for a string suffix manager.
</p>
<h5><span class="caption-index-5">5.44.1.0.2</span><a name="anchor-5-44-1-0-2"></a>Method</h5>
<p>
<div><strong style="text-decoration:underline">suffixmgr#assign</strong></div>
<div style="margin-bottom:1em"><code>suffixmgr#assign(suffix:symbol):void:[overwrite] {block}</code></div>
Assigns a procedure to a specified symbol in the suffix manager. The procedure is provided by the <code>block</code> that takes a block parameter <code>|value|</code> where <code>value</code> comes from the preceded literal.
</p>
<p>
An error occurs if the same suffix symbol has already been assigned. Specifying <code>:overwrite</code> attribute will forcibly overwrite an existing assignment.
</p>
<h2><span class="caption-index-2">5.45</span><a name="anchor-5-45"></a>symbol Class</h2>
<h3><span class="caption-index-3">5.45.1</span><a name="anchor-5-45-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.45.2</span><a name="anchor-5-45-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">symbol#eval</strong></div>
<div style="margin-bottom:1em"><code>symbol#eval(env?:environment)</code></div>
Evaluate a symbol object.
</p>
<h2><span class="caption-index-2">5.46</span><a name="anchor-5-46"></a>template Class</h2>
<h3><span class="caption-index-3">5.46.1</span><a name="anchor-5-46-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.46.2</span><a name="anchor-5-46-2"></a>Cast Operation</h3>
<p>
A function that expects a <code>template</code> instance in its argument can also take a value of <code>stream</code> as below:
</p>
<ul>
<li><code>stream</code> .. Creates a <code>template</code> instance by parsing the content of the stream.</li>
</ul>
<p>
As a <code>stream</code> is capable of being casted from <code>string</code> and <code>binary</code>, such values can also be passed to the argument that expects <code>template</code>.
</p>
<p>
Using the above casting feature, you can call a function <code>f(tmpl:template)</code> that takes a <code>template</code> instance in its argument as below:
</p>
<ul>
<li><code>f(template(stream('foo.txt')))</code> .. The most explicit way.</li>
<li><code>f(stream('foo.txt'))</code> .. Implicit casting: from <code>stream</code> to <code>template</code>.</li>
<li><code>f(template('foo.txt'))</code> .. Implicit casting: from <code>string</code> to <code>stream</code>.</li>
<li><code>f('foo.txt')</code> .. Implicit casting: from <code>string</code> to <code>stream</code>, then from <code>stream</code> to <code>template</code>.</li>
</ul>
<h3><span class="caption-index-3">5.46.3</span><a name="anchor-5-46-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">template</strong></div>
<div style="margin-bottom:1em"><code>template(src?:stream:r):map:[lasteol,noindent] {block?}</code></div>
Creates a <code>template</code> instance.
</p>
<p>
If the stream <code>src</code> is specified, the instance would be initialized with the parsed result of the script-embedded text from the stream.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code>:lasteol</code></li>
<li><code>:noindent</code></li>
</ul>
<h3><span class="caption-index-3">5.46.4</span><a name="anchor-5-46-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">template#parse</strong></div>
<div style="margin-bottom:1em"><code>template#parse(str:string):void:[lasteol,noindent]</code></div>
Creates a <code>template</code> instance by parsing a script-embedded text in a string.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code>:lasteol</code></li>
<li><code>:noindent</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">template#read</strong></div>
<div style="margin-bottom:1em"><code>template#read(src:stream:r):void:[lasteol,noindent]</code></div>
Creates a <code>template</code> instance by parsing a script-embedded text from a stream.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code>:lasteol</code></li>
<li><code>:noindent</code></li>
</ul>
<p>
<div><strong style="text-decoration:underline">template#render</strong></div>
<div style="margin-bottom:1em"><code>template#render(dst?:stream:w)</code></div>
Renders stored content to the specified stream.
</p>
<p>
If the stream is omitted, the function returns the rendered result as a string.
</p>
<h3><span class="caption-index-3">5.46.5</span><a name="anchor-5-46-5"></a>Method Called by Template Directive</h3>
<p>
<div><strong style="text-decoration:underline">template#block</strong></div>
<div style="margin-bottom:1em"><code>template#block(symbol:symbol):void</code></div>
Creates a template block which content is supposed to be replaced by a derived template.
</p>
<p>
This method is called by template directive <code>${=block()}</code> during both the initialization and presentation phase of a template process.
</p>
<ul>
<li><strong>Initialization:</strong> Creates a template block from the specified block that is then registered in the current template with the specified symbol.</li>
<li><strong>Presentation:</strong> Evaluates a template block registered with the specified symbol.</li>
</ul>
<p>
Consider an example. Assume that a block associated with symbol <code>`foo</code> is declared in a template file named <code>base.tmpl</code> as below:
</p>
<p>
<code>[base.tmpl]</code>
</p>
<pre><code>Block begins here.
${=block(`foo)}
Content of base.
${end}
Block ends here.
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
Below is another template named <code>derived.tmpl</code> that devies from <code>base.tmpl</code> and overrides the block <code>`foo</code>.
</p>
<p>
<code>[derived.tmpl]</code>
</p>
<pre><code>${=extends('base.tmpl')}

${=block(`foo)}
Content of derived.
${end}
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
<div><strong style="text-decoration:underline">template#call</strong></div>
<div style="margin-bottom:1em"><code>template#call(symbol:symbol, args*)</code></div>
Calls a template macro that has been created by directive <code>${=define}</code>.
</p>
<p>
This method is called by template directive <code>${=call()}</code> during the presentation phase of a template process.
</p>
<p>
Below is an exemple to call a template macro:
</p>
<pre><code>${=call(`show_person, 'Harry', 24)}
</code></pre>
<p>
This method would return <code>nil</code> if a line-break character is rendered at last and would return a null string otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">template#define</strong></div>
<div style="margin-bottom:1em"><code>template#define(symbol:symbol, `args*):void</code></div>
Creates a template macro from the specified block, which is supposed to be called by <code>${=call}</code> directive, and associates it with the specified symbol.
</p>
<p>
This method is called by template directive <code>${=define()}</code> during the initialization phase of a template process.
</p>
<p>
Below is an example to create a template macro:
</p>
<pre><code>${=define(`show_person, name:string, age:number)}
${name} is ${age} years old.
${end}
</code></pre>
<p>
<div><strong style="text-decoration:underline">template#embed</strong></div>
<div style="margin-bottom:1em"><code>template#embed(template:template)</code></div>
Renders the specified template at the current position.
</p>
<p>
This method is called by template directive <code>${=embed()}</code> during the presentation phase of a template process.
</p>
<p>
Below is an example to embed a template file named <code>foo.tmpl</code>.
</p>
<pre><code>${=embed('foo.tmpl')}
</code></pre>
<p>
As the template rendered by this method runs in a different context from the current one, macros and blocks that it defines are not reflected to the current context.
</p>
<p>
This method would return <code>nil</code> if a line-break character is rendered at last and would return a null string otherwise.
</p>
<p>
<div><strong style="text-decoration:underline">template#extends</strong></div>
<div style="margin-bottom:1em"><code>template#extends(template:template):void</code></div>
Declares the current template as a derived one from the specified template.
</p>
<p>
This method is called by template directive <code>${=extends()}</code> during the initialization phase of a template process.
</p>
<p>
The directive must appear in a template only once. An error occurs if the current template has already derived from another template.
</p>
<p>
Below is an example to declare the current template as one derived from <code>base.tmpl</code>.
</p>
<pre><code>${=extends('base.tmpl')}
</code></pre>
<p>
<div><strong style="text-decoration:underline">template#super</strong></div>
<div style="margin-bottom:1em"><code>template#super(symbol:symbol):void</code></div>
Evaluates a template block registered with the specified symbol in a template from which the current template has derived.
</p>
<p>
This method is called by template directive <code>${=super()}</code> during the presentation phase of a template process. The directive is intended to be used within a directive <code>${=block()}</code>.
</p>
<p>
Consider an example. Assume that a block associated with symbol <code>`foo</code> is declared in a template named <code>base.tmpl</code> as below:
</p>
<p>
<code>[base.tmpl]</code>
</p>
<pre><code>Block begins here.
${=block(`foo)}
Content of base.
${end}
Block ends here.
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
Below is another template named <code>derived.tmpl</code> that devies from <code>base.tmpl</code> and overrides the block <code>`foo</code>.
</p>
<p>
<code>[derived.tmpl]</code>
</p>
<pre><code>${=extends('base.tmpl')}

${=block(`foo)}
${=super(`foo)}
Content of derived.
${end}
</code></pre>
<p>
This template renders the following result:
</p>
<pre><code>Block begins here.
Content of base.
Content of derived.
Block ends here.
</code></pre>
<h2><span class="caption-index-2">5.47</span><a name="anchor-5-47"></a>timedelta Class</h2>
<h3><span class="caption-index-3">5.47.1</span><a name="anchor-5-47-1"></a>Overview</h3>
<p>
The <code>timedelta</code> instance provides a time delta information that works with <code>datetime</code> instance. You can shift time information of <code>datetime</code> by applying addition or subtraction of <code>timedelta</code> to it.
</p>
<h3><span class="caption-index-3">5.47.2</span><a name="anchor-5-47-2"></a>Property</h3>
<p>
A <code>timedelta</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>days</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Offset of days.</td>
</tr>

<tr>
<td>
<code>secs</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Offset of seconds.</td>
</tr>

<tr>
<td>
<code>usecs</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
Offset of micro seconds.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.47.3</span><a name="anchor-5-47-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">timedelta</strong></div>
<div style="margin-bottom:1em"><code>timedelta(days:number =&gt; 0, secs:number =&gt; 0, usecs:number =&gt; 0):map {block?}</code></div>
Returns a timedelta instance with specified values. The instance actually holds properties of days, secs and usecs.
</p>
<h2><span class="caption-index-2">5.48</span><a name="anchor-5-48"></a>uri Class</h2>
<h3><span class="caption-index-3">5.48.1</span><a name="anchor-5-48-1"></a>Overview</h3>
<p>
The <code>uri</code> instance analyzes a URI string and returns each part in it such as the scheme and path. A generic URI has the following format:
</p>
<pre><code>scheme:[//[user:password@]host:port]][/]path[?query][#fragment]
</code></pre>
<h3><span class="caption-index-3">5.48.2</span><a name="anchor-5-48-2"></a>Property</h3>
<p>
A <code>uri</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>host</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
Host part in the URI.</td>
</tr>

<tr>
<td>
<code>misc</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
Misc part in the URI.</td>
</tr>

<tr>
<td>
<code>password</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
Password part in the URI.</td>
</tr>

<tr>
<td>
<code>port</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
Port part in the URI.</td>
</tr>

<tr>
<td>
<code>scheme</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
Scheme part in the URI.</td>
</tr>

<tr>
<td>
<code>urlpath</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
URL path part in the URI, which contains the path, query and fragment part.</td>
</tr>

<tr>
<td>
<code>user</code></td>
<td>
<code>string</code></td>
<td>
R/W</td>

<td>
User part in the URI.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.48.3</span><a name="anchor-5-48-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">uri</strong></div>
<div style="margin-bottom:1em"><code>uri(str?:string):map {block?}</code></div>
Creates <code>uri</code> instance.
</p>
<p>
If the argument <code>str</code> is specified, it would be parsed as a URI which is stored in the instance.
</p>
<p>
If omitted, the instance would be initialized as an empty one.
</p>
<h3><span class="caption-index-3">5.48.4</span><a name="anchor-5-48-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">uri#getfragment</strong></div>
<div style="margin-bottom:1em"><code>uri#getfragment()</code></div>
Returns the fragment part contained in the URI path.
</p>
<p>
<div><strong style="text-decoration:underline">uri#getpath</strong></div>
<div style="margin-bottom:1em"><code>uri#getpath()</code></div>
Returns the path part contained in the URI path.
</p>
<p>
<div><strong style="text-decoration:underline">uri#getquery</strong></div>
<div style="margin-bottom:1em"><code>uri#getquery()</code></div>
Returns a <code>dict</code> instance that is made from the query part in the URI path.
</p>
<p>
<div><strong style="text-decoration:underline">uri.parsequery</strong></div>
<div style="margin-bottom:1em"><code>uri.parsequery(query:string):static:map</code></div>
This is a utility function to parse a query string and return a <code>dict</code> instance that contains key-value pairs for the query.
</p>
<h3><span class="caption-index-3">5.48.5</span><a name="anchor-5-48-5"></a>Cast Operation</h3>
<p>
A function that expects a <code>uri</code> instance in its argument can also take a value of <code>string</code> that is recognized as a URI string.
</p>
<p>
With the above casting feature, you can call a function <code>f(uri:uri)</code> that takes a <code>uri</code> instance in its argument as below:
</p>
<ul>
<li><code>f(uri('http://example.com'))</code> .. The most explicit way.</li>
<li><code>f('http://example.com')</code> .. Implicit casting: from <code>string</code> to <code>uri</code>. </li>
</ul>
<h2><span class="caption-index-2">5.49</span><a name="anchor-5-49"></a>vertex Class</h2>
<h3><span class="caption-index-3">5.49.1</span><a name="anchor-5-49-1"></a>Overview</h3>
<p>
The <code>vertex</code> class provides vertex information that consists of x, y, z and w values.
</p>
<h3><span class="caption-index-3">5.49.2</span><a name="anchor-5-49-2"></a>Property</h3>
<p>
An <code>vertex</code> instance has the following properties:
</p>
<p>
<table>
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>x</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
A value of X.</td>
</tr>

<tr>
<td>
<code>y</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
A value of Y.</td>
</tr>

<tr>
<td>
<code>z</code></td>
<td>
<code>number</code></td>
<td>
R/W</td>

<td>
A value of Z.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">5.49.3</span><a name="anchor-5-49-3"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">vertex</strong></div>
<div style="margin-bottom:1em"><code>vertex(x:number, y:number, z?:number):map {block?}</code></div>
Creates a <code>vertex</code> instance that has the given coordinates <code>x</code>, <code>y</code> and <code>z</code>. The argument <code>z</code> is optional and set to zero if omitted.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|v:vertex|</code>, where <code>v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">5.49.4</span><a name="anchor-5-49-4"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">vertex.cross</strong></div>
<div style="margin-bottom:1em"><code>vertex.cross (v1:vertex, v2:vertex):static:map {block?}</code></div>
Calculates cross product between <code>v1</code> and <code>v2</code> and returns the result as a <code>vertex</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">vertex.dot</strong></div>
<div style="margin-bottom:1em"><code>vertex.dot(v1:vertex, v2:vertex):static:map {block?}</code></div>
Calculates dot product between <code>v1</code> and <code>v2</code> and returns the result as a <code>number</code> instance.
</p>
<p>
<div><strong style="text-decoration:underline">vertex#list</strong></div>
<div style="margin-bottom:1em"><code>vertex#list() {block?}</code></div>
Creates a <code>list</code> that contains coordinate values <code>[x, y, z]</code> of the target <code>vertex</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|list:list|</code>, where <code>list</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">vertex.normal</strong></div>
<div style="margin-bottom:1em"><code>vertex.normal(v1:vertex, v2:vertex, v3:vertex):static:map:[unit] {block?}</code></div>
Calculates a normal vector for a face that consists of three vertices given and returns it as a <code>vertex</code> instance.
</p>
<p>
In default, it returns a vector before being regulated to have a length of one. Specifying the attribute <code>:unit</code> would apply the calculation.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|v:vertex|</code>, where <code>v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">vertex#rotate@x</strong></div>
<div style="margin-bottom:1em"><code>vertex#rotate@x(angle:number):[deg] {block?}</code></div>
Creates a <code>vertex</code> that is rotated from the target <code>vertex</code> around X-axis by the specified <code>angle</code> in radian. It would be rotated in a direction of tilting Y-axis toward Z-axis.
</p>
<p>
If the attribute <code>:deg</code> is specified, you can specify the <code>angle</code> in degree unit.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|v:vertex|</code>, where <code>v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">vertex#rotate@y</strong></div>
<div style="margin-bottom:1em"><code>vertex#rotate@y(angle:number):[deg] {block?}</code></div>
Creates a <code>vertex</code> that is rotated from the target <code>vertex</code> around Y-axis by the specified <code>angle</code> in radian. It would be rotated in a direction of tilting Z-axis toward X-axis.
</p>
<p>
If the attribute <code>:deg</code> is specified, you can specify the <code>angle</code> in degree unit.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|v:vertex|</code>, where <code>v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">vertex#rotate@z</strong></div>
<div style="margin-bottom:1em"><code>vertex#rotate@z(angle:number):[deg] {block?}</code></div>
Creates a <code>vertex</code> that is rotated from the target <code>vertex</code> around Z-axis by the specified <code>angle</code> in radian. It would be rotated in a direction of tilting X-axis toward Y-axis.
</p>
<p>
If the attribute <code>:deg</code> is specified, you can specify the <code>angle</code> in degree unit.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|v:vertex|</code>, where <code>v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">vertex#translate</strong></div>
<div style="margin-bottom:1em"><code>vertex#translate(tx:number, ty:number, tz?:number) {block?}</code></div>
Creates a <code>vertex</code> that is translated from the target <code>vertex</code> by the specified offsets <code>tx</code>, <code>ty</code> and <code>tz</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|v:vertex|</code>, where <code>v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p />

{% endraw %}
