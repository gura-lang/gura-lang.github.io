---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-04.html#naviitem-selected
nextpage: chapter-06.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">5</span>Built-in Class</h1>
<h2><span class="caption-index-2">5.1</span><a name="anchor-5-1"></a>argument Class</h2>
<h3><span class="caption-index-3">5.1.1</span><a name="anchor-5-1-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">argument</code> class provides measures to access argument information that is passed to a function. One of its purposes is to check if an attribute is specified in the function call. It also provides a method to control a leader-trailer sequence, a mechanism that flow controls such as <code class="highlighter-rouge">if-elsif-else</code> and <code class="highlighter-rouge">try-catch</code> utilize.
</p>
<p>
There's no constructor to realize an instance of <code class="highlighter-rouge">argument</code> class. Its instance is implicitly created when a function is called, and you can refer to it by a variable named <code class="highlighter-rouge">__arg__</code>.
</p>
<p>
Below is an example to use <code class="highlighter-rouge">argument</code> class:
</p>
<pre class="highlight"><code>func(v0, v1, v2):[attr1,attr2] = {
    printf('arg#%d %s\n', 0.., __arg__.values)
    printf('attr1:%s attr2:%s\n', __arg__.isset(`attr1), __arg__.isset(`attr2))
}
</code></pre>
<h3><span class="caption-index-3">5.1.2</span><a name="anchor-5-1-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">argument</code> instance has the following properties:
</p>
<div class="mb-2"><code>argument#function</code> &hellip; <code>function</code> [read-only]</div>
<div class="mb-2 ml-4">
The <code class="highlighter-rouge">function</code> instance that has created the argument.
</div>
<div class="mb-2"><code>argument#values</code> &hellip; <code>function</code> [read-only]</div>
<div class="mb-2 ml-4">
A list of argument values.
</div>
<h3><span class="caption-index-3">5.1.3</span><a name="anchor-5-1-3"></a>Method</h3>
<div class="mb-2"><code>argument#finalize_trailer():void</code></div>
<div class="mb-2 ml-4">
Signals finalizing status to trailers after the current function.
</div>
<div class="mb-2"><code>argument#isset(symbol:symbol)</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the function is called with an attribute that matches the specified symbol.
</div>
<div class="mb-2"><code>argument#quit_trailer():void</code></div>
<div class="mb-2 ml-4">
<p>
Cancels evaluation of following trailers.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>f(flag:boolean) = {
    !flag &amp;&amp; __arg__.quit_trailer() 
}

f(true) println('printed')
f(false) println('not printed')
</code></pre>

</div>
<h2><span class="caption-index-2">5.2</span><a name="anchor-5-2"></a>array Class</h2>
<h3><span class="caption-index-3">5.2.1</span><a name="anchor-5-2-1"></a>Overview</h3>
<p>
An instance of the <code class="highlighter-rouge">array</code> class stores multiple numeric values in a seamless binary sequence. It can directly be passed to functions in C libraries without any modification that expect arrays of <code class="highlighter-rouge">char</code>, <code class="highlighter-rouge">short</code>, <code class="highlighter-rouge">int</code>, <code class="highlighter-rouge">float</code>, <code class="highlighter-rouge">double</code> and so on.
</p>
<p>
There are several <code class="highlighter-rouge">array</code> classes that deal with different element types as shown below:
</p>
<table class="table">
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
<p>
In the specification described here, the class name is is represented as <code class="highlighter-rouge">array@T</code> where <code class="highlighter-rouge">T</code> means its element type.
</p>
<p>
Most of methods in <code class="highlighter-rouge">array</code> class are implemented in <code class="highlighter-rouge">arrayt</code> module while the class itself is provided by the intepreter. This is because array features cost much code size and it would be preferable to reduce the size of the intepreter body by separating the implementation of array methods. So, you have to import <code class="highlighter-rouge">arrayt</code> module before using the <code class="highlighter-rouge">array</code> class in your program.
</p>
<h3><span class="caption-index-3">5.2.2</span><a name="anchor-5-2-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">array</code> instance has the following properties:
</p>
<div class="mb-2"><code>array#T</code> &hellip; <code>array</code> [read-only]</div>
<div class="mb-2 ml-4">
Return an array with its row and column being tranposed.
</div>
<div class="mb-2"><code>array#elembytes</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the size of each element in bytes.
</div>
<div class="mb-2"><code>array#elemtype</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the type name of the elements as a <code class="highlighter-rouge">symbol</code> including: <code class="highlighter-rouge">`boolean</code>, <code class="highlighter-rouge">`int8</code>, <code class="highlighter-rouge">`uint8</code>, <code class="highlighter-rouge">`int16</code>, <code class="highlighter-rouge">`uint16</code>, <code class="highlighter-rouge">`int32</code>, <code class="highlighter-rouge">`uint32</code>, <code class="highlighter-rouge">`int64</code>, <code class="highlighter-rouge">`uint64</code>, <code class="highlighter-rouge">`half</code>, <code class="highlighter-rouge">`float</code>, <code class="highlighter-rouge">`double</code> and <code class="highlighter-rouge">`complex</code>.
</div>
<div class="mb-2"><code>array#major</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the major-mode in symbols <code class="highlighter-rouge">`row</code> or <code class="highlighter-rouge">`column</code>.
</div>
<div class="mb-2"><code>array#memoryid</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the id of memory.
</div>
<div class="mb-2"><code>array#ndim</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the number of dimensions.
</div>
<div class="mb-2"><code>array#p</code> &hellip; <code>pointer</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the pointer through which you can inspect and modify the content of the array as a binary data.
</div>
<div class="mb-2"><code>array#shape</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns a list of sizes of each dimension.
</div>
<div class="mb-2"><code>array#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the total number of elements.
</div>
<h3><span class="caption-index-3">5.2.3</span><a name="anchor-5-2-3"></a>Constructor</h3>
<div class="mb-2"><code>array(src?, elemtype?:symbol) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> instance that contains <code class="highlighter-rouge">double</code> type of elements from a <code class="highlighter-rouge">list</code> or an <code class="highlighter-rouge">iterator</code> specified as an argument <code class="highlighter-rouge">src</code> or from elements described in the block. The followings are examples to create an <code class="highlighter-rouge">array</code> instance:
</p>
<pre class="highlight"><code>array([[0, 1, 2], [3, 4, 5]])
array {{0, 1, 2}, {3, 4, 5}}
</code></pre>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The following examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">int32</code> elements:
</p>
<pre class="highlight"><code>array([[0, 1, 2], [3, 4, 5]], elemtype =&gt; `int32)
array(elemtype =&gt; `int32) {{0, 1, 2}, {3, 4, 5}}
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Functions named <code class="highlighter-rouge">array@T</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32 ([[0, 1, 2], [3, 4, 5]])
array@int32 {{0, 1, 2}, {3, 4, 5}}
</code></pre>

</div>
<div class="mb-2"><code>array.identity(n:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array of <code class="highlighter-rouge">double</code> type of elements that represents an identity matrix with specified size <code class="highlighter-rouge">n</code>.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.identity(3)
// x is array@double {{1, 0, 0}, {0, 1, 0}, {0, 0, 1}}
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">int32</code> elements:
</p>
<pre class="highlight"><code>array.identity(3, elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.identity</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32.identity(3)
</code></pre>

</div>
<div class="mb-2"><code>array.interval(begin:number, end:number, samples:number, elemtype?:symbol):static:map:[open,open_l,open_r] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a one-dimentional array with <code class="highlighter-rouge">double</code> type of element that contains a sequence of numbers according to the beginning, ending numbers and the number of samples between them.
</p>
<p>
In default, it creates a sequence with a range of <code class="highlighter-rouge">[begin, end]</code> meaning that the sequence contains the beginning and ending numbers. Following attributes would control the range:
</p>
<ul>
<li><code class="highlighter-rouge">:open</code> .. Numbers in range of <code class="highlighter-rouge">(begin, end)</code> that doesn't contain either <code class="highlighter-rouge">begin</code> or <code class="highlighter-rouge">end</code>.</li>
<li><code class="highlighter-rouge">:open_l</code> .. Numbers in range of <code class="highlighter-rouge">(begin, end]</code> that doesn't contain <code class="highlighter-rouge">begin</code>.</li>
<li><code class="highlighter-rouge">:open_r</code> .. Numbers in range of <code class="highlighter-rouge">[begin, end)</code> that doesn't contain <code class="highlighter-rouge">end</code>.</li>
</ul>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.interval(0, 3, 7)
// x is array@double {0, 0.5, 1, 1.5, 2, 2.5, 3}
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.interval(0, 3, 7, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.interval</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.interval(0, 3, 7)
</code></pre>

</div>
<div class="mb-2"><code>array.ones(dims[]:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array of <code class="highlighter-rouge">double</code> type of elements, which are initialized with one. The argument <code class="highlighter-rouge">dims</code> specifies the dimension of the created array.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.ones([3, 4])
// x is array@double {{1, 1, 1, 1}, {1, 1, 1, 1}, {1, 1, 1, 1}}
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">int32</code> elements:
</p>
<pre class="highlight"><code>array.ones([3, 4], elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.ones</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32.ones([3, 4])
</code></pre>

</div>
<div class="mb-2"><code>array.rands(dims[]:number, range?:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array of <code class="highlighter-rouge">double</code> type of elements which are initialized with random numbers. The argument <code class="highlighter-rouge">dims</code> specifies the dimension of the created array. When the argument <code class="highlighter-rouge">range</code> is specified, the generated elements are all integer numbers that are ranged within <code class="highlighter-rouge">[0, range)</code>. Otherwise, the generated elements are real numbers ranged within <code class="highlighter-rouge">[0, 1)</code>.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.rands([3, 4], 10)
// x is like array@double {{6, 7, 6, 9}, {3, 3, 6, 0}, {7, 9, 5, 5}}
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">int32</code> elements:
</p>
<pre class="highlight"><code>array.rands([3, 4], 10, elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.rands</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32.rands([3, 4], 10)
</code></pre>

</div>
<div class="mb-2"><code>array.rands@normal(dims[]:number, mu?:number, sigma?:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array of <code class="highlighter-rouge">double</code> type of elements which are initialized with normal distribution random numbers. The argument <code class="highlighter-rouge">dims</code> specifies the dimension of the created array. The arguments <code class="highlighter-rouge">mu</code> and <code class="highlighter-rouge">sigma</code> supply parameters for normal distribution where <code class="highlighter-rouge">mu</code> specifies the mean value and <code class="highlighter-rouge">sigma</code> the standard deviation. In default, the <code class="highlighter-rouge">mu</code> is zero and <code class="highlighter-rouge">sigma</code> one.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.rands@normal([3, 4], 1, 3)
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.rands@normal([3, 4], 1, 3, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.rands@normal</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32.rands@normal([3, 4], 1, 3)
</code></pre>

</div>
<div class="mb-2"><code>array.range(num:number, num_end?:number, step?:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array of <code class="highlighter-rouge">double</code> type of elements that are initialized with a sequence of integer numbers.
</p>
<p>
This function can generate three types of sequence like below:
</p>
<ul>
<li><code class="highlighter-rouge">array.range(num)</code> .. between <code class="highlighter-rouge">0</code> and <code class="highlighter-rouge">(num - 1)</code>.</li>
<li><code class="highlighter-rouge">array.range(num, num_end)</code> .. between <code class="highlighter-rouge">num</code> and <code class="highlighter-rouge">(num_end - 1)</code>.</li>
<li><code class="highlighter-rouge">array.range(num, num_end, step)</code> .. between <code class="highlighter-rouge">num</code> and <code class="highlighter-rouge">(num_end - 1)</code> incremented by <code class="highlighter-rouge">step</code>.</li>
</ul>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.range(5)
// x is array@double {0, 1, 2, 3, 4}
x = array.range(2, 5)
// x is array@double {2, 3, 4}
x = array.range(2, 10, 2)
// x is array@double {2, 4, 6, 8}
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">int32</code> elements:
</p>
<pre class="highlight"><code>array.range(5, elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.range</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32.range(5)
</code></pre>

</div>
<div class="mb-2"><code>array.rotation(angle:number, xtrans?:number, ytrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> of <code class="highlighter-rouge">double</code> type of elements representing a matrix to rotate a 2-D coord.
</p>
<p>
The rotation <code class="highlighter-rouge">angle</code> is specified in radian value. If the attribute <code class="highlighter-rouge">:deg</code> is specified, the <code class="highlighter-rouge">angle</code> is specified in degree value.
</p>
<p>
If one or both of <code class="highlighter-rouge">xtrans</code> and <code class="highlighter-rouge">ytrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.rotation(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation(math.pi / 6, 3, 5)
// x is a matrix to rotate by pi/6 and translate by [3, 5].
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.rotation(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.rotation</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.rotation(math.pi / 6)
</code></pre>

</div>
<div class="mb-2"><code>array.rotation@x(angle:number, xtrans?:number, ytrans?:number, ztrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> of <code class="highlighter-rouge">double</code> type of elements representing a matrix to rotate a 3-D coord around x-axis.
</p>
<p>
The rotation <code class="highlighter-rouge">angle</code> is specified in radian value. If the attribute <code class="highlighter-rouge">:deg</code> is specified, the <code class="highlighter-rouge">angle</code> is specified in degree value.
</p>
<p>
If one or more of <code class="highlighter-rouge">xtrans</code>, <code class="highlighter-rouge">ytrans</code> and <code class="highlighter-rouge">ztrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.rotation@x(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation@x(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation@x(math.pi / 6, 3, -2, 5)
// x is a matrix to rotate by pi/6 and translate by [3, -2, 5].
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.rotation@x(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.rotation@x</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.rotation@x(math.pi / 6)
</code></pre>

</div>
<div class="mb-2"><code>array.rotation@y(angle:number, xtrans?:number, ytrans?:number, ztrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> of <code class="highlighter-rouge">double</code> type of elements representing a matrix to rotate a 3-D coord around y-axis.
</p>
<p>
The rotation <code class="highlighter-rouge">angle</code> is specified in radian value. If the attribute <code class="highlighter-rouge">:deg</code> is specified, the <code class="highlighter-rouge">angle</code> is specified in degree value.
</p>
<p>
If one or more of <code class="highlighter-rouge">xtrans</code>, <code class="highlighter-rouge">ytrans</code> and <code class="highlighter-rouge">ztrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.rotation@y(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation@y(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation@y(math.pi / 6, 3, -2, 5)
// x is a matrix to rotate by pi/6 and translate by [3, -2, 5].
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.rotation@y(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.rotation@y</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.rotation@y(math.pi / 6)
</code></pre>

</div>
<div class="mb-2"><code>array.rotation@z(angle:number, xtrans?:number, ytrans?:number, ztrans?:number, elemtype?:symbol):static:map:[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> of <code class="highlighter-rouge">double</code> type of elements representing a matrix to rotate a 3-D coord around z-axis.
</p>
<p>
The rotation <code class="highlighter-rouge">angle</code> is specified in radian value. If the attribute <code class="highlighter-rouge">:deg</code> is specified, the <code class="highlighter-rouge">angle</code> is specified in degree value.
</p>
<p>
If one or more of <code class="highlighter-rouge">xtrans</code>, <code class="highlighter-rouge">ytrans</code> and <code class="highlighter-rouge">ztrans</code> are specified, it would create an array that works as translation as well as rotation.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.rotation@z(math.pi / 6)
// x is a matrix to rotate by pi/6.
x = array.rotation@z(30):deg
// x is a matrix to rotate by 30 degree, which is pi/6 in radian.
x = array.rotation@z(math.pi / 6, 3, -2, 5)
// x is a matrix to rotate by pi/6 and translate by [3, -2, 5].
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.rotation@z(math.pi / 6, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.rotation@z</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.rotation@z(math.pi / 6)
</code></pre>

</div>
<div class="mb-2"><code>array.scaling(xscale:number, yscale:number, zscale?:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> of <code class="highlighter-rouge">double</code> type of elements representing a matrix to scale a coord.
</p>
<p>
It creates a matrix that works on a 2-D coord if <code class="highlighter-rouge">xscale</code> and <code class="highlighter-rouge">yscale</code> are specified while it creates a matrix on a 3-D coord if <code class="highlighter-rouge">xscale</code>, <code class="highlighter-rouge">yscale</code> and <code class="highlighter-rouge">zscale</code> are specified.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.scaling(3, 4)
// x is a matrix to scale a 2-D coord by [3, 4].
x = array.scaling(3, 4, -2)
// x is a matrix to scale a 3-D coord by [3, 4, -2].
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.scaling(3, 4, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.scaling</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.scaling(3, 4
</code></pre>

</div>
<div class="mb-2"><code>array.translation(xtrans:number, ytrans:number, ztrans?:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">array</code> of <code class="highlighter-rouge">double</code> type of elements representing a matrix to translate a coord.
</p>
<p>
It creates a matrix that works on a 2-D coord if <code class="highlighter-rouge">xtrans</code> and <code class="highlighter-rouge">ytrans</code> are specified while it creates a matrix on a 3-D coord if <code class="highlighter-rouge">xtrans</code>, <code class="highlighter-rouge">ytrans</code> and <code class="highlighter-rouge">ztrans</code> are specified.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.translation(3, 4)
// x is a matrix to translate a 2-D coord by [3, 4].
x = array.translation(3, 4, -2)
// x is a matrix to translate a 3-D coord by [3, 4, -2].
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">float</code> elements:
</p>
<pre class="highlight"><code>array.translation(3, 4, elemtype =&gt; `float)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.translation</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@float.translation(3, 4
</code></pre>

</div>
<div class="mb-2"><code>array.zeros(dims[]:number, elemtype?:symbol):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array of <code class="highlighter-rouge">double</code> type of elements, which are initialized with zero. The argument <code class="highlighter-rouge">dims</code> specifies the dimension of the created array.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>x = array.zeros([3, 4])
// x is array@double {{0, 0, 0, 0}, {0, 0, 0, 0}, {0, 0, 0, 0}}
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Specifying the argument <code class="highlighter-rouge">elemtype</code> would create an array of element type other than <code class="highlighter-rouge">double</code>. The followings examples create an <code class="highlighter-rouge">array</code> instance of <code class="highlighter-rouge">int32</code> elements:
</p>
<pre class="highlight"><code>array.zeros([3, 4], elemtype =&gt; `int32)
</code></pre>
<p>
Available element types are:
</p>
<pre class="highlight"><code>`int8, `uint8, `int16, `uint16, `int32, `uint32, `int64, `uint64
`half, `float, `double, `complex
</code></pre>
<p>
Methods named <code class="highlighter-rouge">array@T.zeros</code> where <code class="highlighter-rouge">T</code> gets an element type name are also provided to create an <code class="highlighter-rouge">array</code> instance of a specific type more easily. Using these functions could simplify the code above like this:
</p>
<pre class="highlight"><code>array@int32.zeros([3, 4])
</code></pre>

</div>
<h3><span class="caption-index-3">5.2.4</span><a name="anchor-5-2-4"></a>Method</h3>
<div class="mb-2"><code>array#argmax(axis?:number):map:[last_index] {block?}</code></div>
<div class="mb-2 ml-4">
Returns index of a maximum number of elements in the target <code class="highlighter-rouge">array</code>.
</div>
<div class="mb-2"><code>array#argmin(axis?:number):map:[last_index] {block?}</code></div>
<div class="mb-2 ml-4">
Returns index of a minimum number of elements in the target <code class="highlighter-rouge">array</code>.
</div>
<div class="mb-2"><code>array.dot(a:array, b:array):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Calculates a dot product between two arrays that have one or two dimensions.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#dump(stream?:stream):void:[upper]</code></div>
<div class="mb-2 ml-4">
Prints out a binary dump of the array's content.
</div>
<div class="mb-2"><code>array#each():[flat] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that iterates each element in the array.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
The block parameter is <code class="highlighter-rouge">|elem:number, idx:number|</code> where <code class="highlighter-rouge">elem</code> is the element value.
</p>

</div>
<div class="mb-2"><code>array#elemcast(elemtype:symbol) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Cast value type of contained elements.
</p>
<p>
Available symbols for <code class="highlighter-rouge">elemtype</code> are as follows:
</p>
<ul>
<li><code class="highlighter-rouge">`boolean</code></li>
<li><code class="highlighter-rouge">`int8</code></li>
<li><code class="highlighter-rouge">`uint8</code></li>
<li><code class="highlighter-rouge">`int16</code></li>
<li><code class="highlighter-rouge">`uint16</code></li>
<li><code class="highlighter-rouge">`int32</code></li>
<li><code class="highlighter-rouge">`uint32</code></li>
<li><code class="highlighter-rouge">`int64</code></li>
<li><code class="highlighter-rouge">`uint64</code></li>
<li><code class="highlighter-rouge">`half</code></li>
<li><code class="highlighter-rouge">`float</code></li>
<li><code class="highlighter-rouge">`double</code></li>
<li><code class="highlighter-rouge">`complex</code></li>
</ul>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#fill(value:number):void</code></div>
<div class="mb-2 ml-4">
Fills array with a specified value.
</div>
<div class="mb-2"><code>array#flatten() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an <code class="highlighter-rouge">array</code> instance as a result that has flattened elements in the target <code class="highlighter-rouge">array</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#head(n:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an <code class="highlighter-rouge">array</code> instance as a result that has extracted <code class="highlighter-rouge">n</code> elements from the beginning of the target <code class="highlighter-rouge">array</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#invert(eps?:number) {block?}</code></div>
<div class="mb-2 ml-4">
Returns an <code class="highlighter-rouge">array</code> instance as a result that has elements of inverted matrix of the target <code class="highlighter-rouge">array</code>. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</div>
<div class="mb-2"><code>array#iselemsame(array:array)</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the target <code class="highlighter-rouge">array</code> instance has the same elements with the specified <code class="highlighter-rouge">array</code>.
</div>
<div class="mb-2"><code>array#issquare()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the target <code class="highlighter-rouge">array</code> consists square matrices.
</div>
<div class="mb-2"><code>array#max(axis?:number):map:[index,last_index] {block?}</code></div>
<div class="mb-2 ml-4">
Finds a maximum number of elements in the target <code class="highlighter-rouge">array</code>.
</div>
<div class="mb-2"><code>array#mean(axis?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Calculates an mean value of elements in the array.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#min(axis?:number):map:[index,last_index] {block?}</code></div>
<div class="mb-2 ml-4">
Finds a minimum number of elements in the target <code class="highlighter-rouge">array</code>.
</div>
<div class="mb-2"><code>array#offset(n:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an <code class="highlighter-rouge">array</code> instance as a result that has extracted elements of the target <code class="highlighter-rouge">array</code> after skipping its first <code class="highlighter-rouge">n</code> elements.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#paste(offset:number, src:array):map</code></div>
<div class="mb-2 ml-4">
<p>
Pastes elements of <code class="highlighter-rouge">src</code> into the target <code class="highlighter-rouge">array</code> instance.
</p>
<p>
The argument <code class="highlighter-rouge">offset</code> specifies the posision where elements are pasted in
</p>

</div>
<div class="mb-2"><code>array#reshape(dims[]:number:nil) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an <code class="highlighter-rouge">array</code> instance as a result that has reshaped the target <code class="highlighter-rouge">array</code> according to a list of dimension size specified by <code class="highlighter-rouge">dims</code>.
</p>
<p>
Below are examples:
</p>
<pre class="highlight"><code>x = array(1..24)
a = x.reshape([6, 4])    // a is an array of 6x4.
b = x.reshape([2, 3, 4]) // b is an array of 2x3x4.
</code></pre>
<p>
A value of <code class="highlighter-rouge">nil</code> in the list of dimension means it would be calculated from the whole size and other dimension sizes. Only one <code class="highlighter-rouge">nil</code> is allowed to exist.
</p>
<pre class="highlight"><code>x = array(1..24)
b = x.reshape([2, nil, 4]) // b is an array of 2x3x4.
</code></pre>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#roundoff(threshold?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an <code class="highlighter-rouge">array</code> instance as a result that has rounded off elements less than <code class="highlighter-rouge">threshold</code> to zero in the target <code class="highlighter-rouge">array</code>. The default value for <code class="highlighter-rouge">threshold</code> is <code class="highlighter-rouge">1.0e-6</code> when omitted.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#std(axis?:number):map:[p] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Calculates a standard deviation value of elements in the target <code class="highlighter-rouge">array</code>.
</p>
<p>
In default, it calculates an unbiased estimation of standard deviation in which the summation of squared deviations is divided by <code class="highlighter-rouge">(n - 1)</code>. Specifying <code class="highlighter-rouge">:p</code> attributes will calculate a population variance that divides that summation by <code class="highlighter-rouge">n</code>.
</p>

</div>
<div class="mb-2"><code>array#sum(axis?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
Calculates a summation value of elements in the target <code class="highlighter-rouge">array</code>.
</div>
<div class="mb-2"><code>array#tail(n:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an <code class="highlighter-rouge">array</code> instance as a result that has extracted <code class="highlighter-rouge">n</code> elements from the bottom of the target <code class="highlighter-rouge">array</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#transpose(axes[]?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an array instance that transposes axes of the original array according to the specified argument <code class="highlighter-rouge">axes</code>.
</p>
<p>
If the argument is not specified, two axes at the lowest rank, which correspond to row and column for a matrix, would be transposed.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|array:array|</code>, where <code class="highlighter-rouge">array</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>array#var(axis?:number):map:[p] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Calculates a variation value of elements in the target <code class="highlighter-rouge">array</code>.
</p>
<p>
In default, it calculates an unbiased estimation of standard deviation in which the summation of squared deviations is divided by <code class="highlighter-rouge">(n - 1)</code>. Specifying <code class="highlighter-rouge">:p</code> attributes will calculate a population variance that divides that summation by <code class="highlighter-rouge">n</code>.
</p>

</div>
<h2><span class="caption-index-2">5.3</span><a name="anchor-5-3"></a>audio Class</h2>
<h3><span class="caption-index-3">5.3.1</span><a name="anchor-5-3-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">audio</code> class provides measures to work on audio data.
</p>
<h3><span class="caption-index-3">5.3.2</span><a name="anchor-5-3-2"></a>Method</h3>
<div class="mb-2"><code>audio#each(channel:number, offset?:number):map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>audio#get(channel:number, offset:number):map</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>audio#put(channel:number, offset:number, data:number):map:reduce</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>audio#sinewave(channel:number, freq:number, len:number, amplitude?:number):map:reduce</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>audio#store(channel:number, offset:number, data:iterator):reduce</code></div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.4</span><a name="anchor-5-4"></a>binary Class</h2>
<h3><span class="caption-index-3">5.4.1</span><a name="anchor-5-4-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">binary</code> class provides measures to work on binary data that is a byte sequence without any format.
</p>
<p>
You can create a <code class="highlighter-rouge">binary</code> instance by calling <code class="highlighter-rouge">binary()</code> function.
</p>
<p>
You can also create the instance by specifying <code class="highlighter-rouge">b</code> prefix before a string literal. For example, the code below creates a <code class="highlighter-rouge">binary</code> instance that contains a sequence <code class="highlighter-rouge">0x41, 0x42, 0xfe, 0x03, 0x43, 0x44</code>.
</p>
<pre class="highlight"><code>b'AB\xfe\x03CD'
</code></pre>
<h3><span class="caption-index-3">5.4.2</span><a name="anchor-5-4-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">binary</code> instance has the following properties:
</p>
<div class="mb-2"><code>binary#p</code> &hellip; <code>pointer</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns a <code class="highlighter-rouge">pointer</code> instance that accesses the binary. This result is equivalent to that of calling the method <code class="highlighter-rouge">binary#pointer()</code>
</div>
<div class="mb-2"><code>binary#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the binary size in bytes.
</div>
<div class="mb-2"><code>binary#writable</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
Indicates if the content of the binary object is writable.
</div>
<h3><span class="caption-index-3">5.4.3</span><a name="anchor-5-4-3"></a>Constructor</h3>
<div class="mb-2"><code>binary(buff*) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">binary</code> instance after combining <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">binary</code> specified by the arguments <code class="highlighter-rouge">buff</code>. If no argument is specified for <code class="highlighter-rouge">buff</code>, an empty <code class="highlighter-rouge">binary</code> instance would be created.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|bin:binary|</code>, where <code class="highlighter-rouge">bin</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.4.4</span><a name="anchor-5-4-4"></a>Method</h3>
<div class="mb-2"><code>binary.alloc(bytes:number, data?:number):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">binary</code> instance that has the specified size of buffer. If the argument <code class="highlighter-rouge">data</code>, which should have a number between 0 and 255, is specified, the buffer would be initialized with the value.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|bin:binary|</code>, where <code class="highlighter-rouge">bin</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>binary#dump(stream?:stream:w):void:[upper]</code></div>
<div class="mb-2 ml-4">
<p>
Prints a hexadecimal dump from the content of the <code class="highlighter-rouge">binary</code> to the standard output. If the argument <code class="highlighter-rouge">stream</code> is specified, the result would be output to the stream.
</p>
<p>
In default, hexadecimal digit are printed with lower-case characters. Specifying an attribute <code class="highlighter-rouge">:upper</code> would output them with upper-case characters instead.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; b'A quick brown fox jumps over the lazy dog.'.dump():upper
41 20 71 75 69 63 6B 20 62 72 6F 77 6E 20 66 6F  A quick brown fo
78 20 6A 75 6D 70 73 20 6F 76 65 72 20 74 68 65  x jumps over the
20 6C 61 7A 79 20 64 6F 67 2E                     lazy dog.
</code></pre>

</div>
<div class="mb-2"><code>binary#pointer(offset?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a <code class="highlighter-rouge">pointer</code> instance that has an initial offset specified by the argument <code class="highlighter-rouge">offset</code>. If the argument is omitted, it would return a <code class="highlighter-rouge">pointer</code> instance that points to the top of the binary.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|p:pointer|</code>, where <code class="highlighter-rouge">p</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>binary#reader() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">stream</code> instance with which you can read data from the binary by <code class="highlighter-rouge">stream#read()</code> method. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</div>
<div class="mb-2"><code>binary#writer() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">stream</code> instance with which you can append data to the binary by <code class="highlighter-rouge">stream#write()</code> method. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</div>
<h2><span class="caption-index-2">5.5</span><a name="anchor-5-5"></a>boolean Class</h2>
<h3><span class="caption-index-3">5.5.1</span><a name="anchor-5-5-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">boolean</code> class represents a boolean data type that is used in logical operations including NOT, AND, OR and XOR.
</p>
<p>
The <code class="highlighter-rouge">boolean</code> type provides two values: <code class="highlighter-rouge">true</code> and <code class="highlighter-rouge">false</code>. The other types of values can also be calculated in logical operations according to the following general rule:
</p>
<ul>
<li>The <code class="highlighter-rouge">nil</code> value is evaluated as <code class="highlighter-rouge">false</code> value.</li>
<li>Other values are evaluated as <code class="highlighter-rouge">true</code>.</li>
</ul>
<p>
Note that the number <code class="highlighter-rouge">0</code> is treated as <code class="highlighter-rouge">true</code> in logical operations. 
</p>
<h2><span class="caption-index-2">5.6</span><a name="anchor-5-6"></a>codec Class</h2>
<h3><span class="caption-index-3">5.6.1</span><a name="anchor-5-6-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">codec</code> class has features to decoding/encoding character codes stored in <code class="highlighter-rouge">string</code> and <code class="highlighter-rouge">binary</code>. Following measures are provided:
</p>
<ul>
<li>Decode .. Converts specific character codes stored in <code class="highlighter-rouge">binary</code> into UTF-8 code and generages <code class="highlighter-rouge">string</code> containing the result. It can also delete a CR code (<code class="highlighter-rouge">0x0d</code>) before a LF code (<code class="highlighter-rouge">0x0d</code>) at each end of line so that lines in the result are joined with LF code.</li>
<li>Encode .. Converts UTF-8 character codes stored in <code class="highlighter-rouge">string</code> into specific codes and generates <code class="highlighter-rouge">binary</code> containing the result. It can also add a CR code (<code class="highlighter-rouge">0x0d</code>) before a LF code (<code class="highlighter-rouge">0x0a</code>) at each end of line so that lines in the result are joined with CR-LF sequence.</li>
</ul>
<p>
You can utilize these functions using <code class="highlighter-rouge">codec</code> class's methods <code class="highlighter-rouge">codec#decode()</code> and <code class="highlighter-rouge">codec#encode()</code> as well as using <code class="highlighter-rouge">stream</code> class's method to read/write text by specifying <code class="highlighter-rouge">codec</code> instance when creating its instance.
</p>
<p>
The actual functions for encoding and decoding are provided by sub modules under <code class="highlighter-rouge">codecs</code> module. Each module provides following codecs:
</p>
<ul>
<li><code class="highlighter-rouge">codecs.basic</code> .. <code class="highlighter-rouge">us-ascii</code>, <code class="highlighter-rouge">utf-8</code>, <code class="highlighter-rouge">utf-16</code>, <code class="highlighter-rouge">utf-16le</code>, <code class="highlighter-rouge">utf-16be</code></li>
<li><code class="highlighter-rouge">codecs.iso8859</code>.. <code class="highlighter-rouge">iso-8859-1</code>, <code class="highlighter-rouge">iso-8859-2</code>, <code class="highlighter-rouge">iso-8859-3</code>, <code class="highlighter-rouge">iso-8859-4</code>, <code class="highlighter-rouge">iso-8859-5</code>, <code class="highlighter-rouge">iso-8859-6</code>, <code class="highlighter-rouge">iso-8859-7</code>, <code class="highlighter-rouge">iso-8859-8</code>, <code class="highlighter-rouge">iso-8859-9</code>, <code class="highlighter-rouge">iso-8859-10</code>, <code class="highlighter-rouge">iso-8859-11</code>, <code class="highlighter-rouge">iso-8859-13</code>, <code class="highlighter-rouge">iso-8859-14</code>, <code class="highlighter-rouge">iso-8859-15</code>, <code class="highlighter-rouge">iso-8859-16</code></li>
<li><code class="highlighter-rouge">codecs.korean</code> .. <code class="highlighter-rouge">cp949</code>, <code class="highlighter-rouge">euc-kr</code></li>
<li><code class="highlighter-rouge">codecs.chinese</code> .. <code class="highlighter-rouge">cp936</code>, <code class="highlighter-rouge">gb2312</code>, <code class="highlighter-rouge">gbk</code>, <code class="highlighter-rouge">cp950</code>, <code class="highlighter-rouge">big5</code></li>
<li><code class="highlighter-rouge">codecs.japanese</code> .. <code class="highlighter-rouge">euc-jp</code>, <code class="highlighter-rouge">cp932</code>, <code class="highlighter-rouge">shift_jis</code>, <code class="highlighter-rouge">ms_kanji</code>, <code class="highlighter-rouge">jis</code>, <code class="highlighter-rouge">iso-2022-jp</code></li>
</ul>
<p>
Importing other codec modules would expand available codecs. You can call <code class="highlighter-rouge">codecs.dir()</code> to get a list of codec names currently available.
</p>
<h3><span class="caption-index-3">5.6.2</span><a name="anchor-5-6-2"></a>Predefined Variable</h3>
<table class="table">
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
<h3><span class="caption-index-3">5.6.3</span><a name="anchor-5-6-3"></a>Constructor</h3>
<div class="mb-2"><code>codec(encoding:string) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">codec</code> instance of the specified encoding name. You can call <code class="highlighter-rouge">codecs.dir()</code> to get a list of available encoding names.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|codec:codec|</code>, where <code class="highlighter-rouge">codec</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.6.4</span><a name="anchor-5-6-4"></a>Method</h3>
<div class="mb-2"><code>codec#addcr(flag?:boolean):reduce</code></div>
<div class="mb-2 ml-4">
<p>
The codec's encoder has a feature to add a CR code (<code class="highlighter-rouge">0x0d</code>) before a LF code (<code class="highlighter-rouge">0x0a</code>) so that the lines are joined with CR-LF codes in the encoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">false</code>.</li>
</ul>

</div>
<div class="mb-2"><code>codec#decode(buff:binary):map</code></div>
<div class="mb-2 ml-4">
Decodes a binary <code class="highlighter-rouge">buff</code> and returns the decoded result as <code class="highlighter-rouge">string</code>.
</div>
<div class="mb-2"><code>codec#delcr(flag?:boolean):reduce</code></div>
<div class="mb-2 ml-4">
<p>
The codec's decoder has a feature to delete a CR code (<code class="highlighter-rouge">0x0d</code>) before a LF code (<code class="highlighter-rouge">0x0a</code>) so that the lines are joined with LF code in the decoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">false</code>.</li>
</ul>

</div>
<div class="mb-2"><code>codec#encode(str:string):map</code></div>
<div class="mb-2 ml-4">
Encodes a string <code class="highlighter-rouge">str</code> and returns the encoded result as <code class="highlighter-rouge">binary</code>.
</div>
<h3><span class="caption-index-3">5.6.5</span><a name="anchor-5-6-5"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">codec</code> instance in its argument can also take a value of <code class="highlighter-rouge">string</code> that is recognized as a codec name.
</p>
<p>
With the above casting feature, you can call a function <code class="highlighter-rouge">f(codec:codec)</code> that takes a <code class="highlighter-rouge">codec</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">f(codec('utf-16'))</code> .. The most explicit way.</li>
<li><code class="highlighter-rouge">f('utf-16')</code> .. Implicit casting: from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">codec</code>. </li>
</ul>
<h2><span class="caption-index-2">5.7</span><a name="anchor-5-7"></a>color Class</h2>
<h3><span class="caption-index-3">5.7.1</span><a name="anchor-5-7-1"></a>Overview</h3>
<p>
An instance of the <code class="highlighter-rouge">color</code> class represents a color data that consists of red, green, blue and alpha elements.
</p>
<p>
You can create a <code class="highlighter-rouge">color</code> instance by calling <code class="highlighter-rouge">color()</code> function.
</p>
<p>
There are class variables as shown below:
</p>
<h3><span class="caption-index-3">5.7.2</span><a name="anchor-5-7-2"></a>Predefined Variable</h3>
<table class="table">
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
<h3><span class="caption-index-3">5.7.3</span><a name="anchor-5-7-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">color</code> instance has the following properties:
</p>
<div class="mb-2"><code>color#a</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Value of the alpha element.
</div>
<div class="mb-2"><code>color#b</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Value of the blue element.
</div>
<div class="mb-2"><code>color#g</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Value of the green element.
</div>
<div class="mb-2"><code>color#r</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Value of the red element.
</div>
<h3><span class="caption-index-3">5.7.4</span><a name="anchor-5-7-4"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">color</code> instance in its argument can also take a value of <code class="highlighter-rouge">symbol</code>, <code class="highlighter-rouge">string</code> and <code class="highlighter-rouge">list</code> as below:
</p>
<ul>
<li><code class="highlighter-rouge">symbol</code> .. Recognized as a color name to look up the color table.</li>
<li><code class="highlighter-rouge">string</code> .. Recognized as a color name to look up the color table.</li>
<li><code class="highlighter-rouge">list</code> .. Expected to contain elements in a format <code class="highlighter-rouge">[red, green, blue]</code> or <code class="highlighter-rouge">[red, green, blue, alpha]</code>.</li>
</ul>
<p>
With the above casting feature, you can call a function <code class="highlighter-rouge">f(c:color)</code> that takes a <code class="highlighter-rouge">color</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">f(color(`purple))</code> .. The most explicit way.</li>
<li><code class="highlighter-rouge">f(`purple)</code> .. Implicit casting: from <code class="highlighter-rouge">symbol</code> to <code class="highlighter-rouge">color</code>.</li>
<li><code class="highlighter-rouge">f('purple')</code> .. Implicit casting: from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">color</code>.</li>
<li><code class="highlighter-rouge">f([128, 0, 128])</code> .. Implicit casting: from <code class="highlighter-rouge">list</code> to <code class="highlighter-rouge">color</code>.</li>
</ul>
<h3><span class="caption-index-3">5.7.5</span><a name="anchor-5-7-5"></a>Constructor</h3>
<div class="mb-2"><code>color(args+):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">color</code> instance.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|c:color|</code>, where <code class="highlighter-rouge">c</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
There are two forms to call this function as below:
</p>
<ul>
<li><code class="highlighter-rouge">color(name:string, a?:number)</code> .. Creates an instance from color name and an optional alpha element. Predefined variable <code class="highlighter-rouge">color.names</code> is a list that contains available color names. A string in a format of <code class="highlighter-rouge">'#rrggbb'</code> that is used in HTML documents is also acceptable as a color name.</li>
<li><code class="highlighter-rouge">color(r:number, g?:number, b?:number, a?:number)</code> .. Creates an instance from RGB elements and an optional alpha element.</li>
</ul>

</div>
<h3><span class="caption-index-3">5.7.6</span><a name="anchor-5-7-6"></a>Method</h3>
<div class="mb-2"><code>color#getgray()</code></div>
<div class="mb-2 ml-4">
<p>
Calculates a gray scale from RGB elements in the <code class="highlighter-rouge">color</code> instance.
</p>
<p>
This is computed by a formula: <code class="highlighter-rouge">gray = 0.299 * red + 0.587 * blue + 0.114 * blue</code>.
</p>

</div>
<div class="mb-2"><code>color#html()</code></div>
<div class="mb-2 ml-4">
Returns a color string in a format of <code class="highlighter-rouge">'#rrggbb'</code> that is used in HTML documents.
</div>
<div class="mb-2"><code>color#list():[alpha]</code></div>
<div class="mb-2 ml-4">
<p>
Returns a list of RGB elements in a form <code class="highlighter-rouge">[r, g, b]</code>.
</p>
<p>
Specifying <code class="highlighter-rouge">:alpha</code> attribute would add the alpha element to the list.
</p>

</div>
<h2><span class="caption-index-2">5.8</span><a name="anchor-5-8"></a>complex Class</h2>
<h3><span class="caption-index-3">5.8.1</span><a name="anchor-5-8-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">complex</code> class provides measures to calculate complex numbers.
</p>
<p>
You can create a <code class="highlighter-rouge">complex</code> instance by following ways:
</p>
<ul>
<li>Calls <code class="highlighter-rouge">complex()</code> function with a real and imaginary part of numbers. e.g., <code class="highlighter-rouge">complex(2, 3)</code></li>
<li>Calls <code class="highlighter-rouge">complex.polar()</code> function with an absolute value and an argument in radius. e.g., <code class="highlighter-rouge">complex.polar(5, math.pi / 6)</code></li>
<li>Appending <code class="highlighter-rouge">j</code> suffix after a number literal would create an imaginal part of a complex numbrer. e.g., <code class="highlighter-rouge">2 + 3j</code></li>
</ul>
<h3><span class="caption-index-3">5.8.2</span><a name="anchor-5-8-2"></a>Constructor</h3>
<div class="mb-2"><code>complex(real:number, imag?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">complex</code> instance with a real part <code class="highlighter-rouge">real</code> and an imaginary part <code class="highlighter-rouge">imag</code>.
</p>
<p>
If the argument <code class="highlighter-rouge">imag</code> is omitted, the imaginary part would be set to zero.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:complex|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.8.3</span><a name="anchor-5-8-3"></a>Method</h3>
<div class="mb-2"><code>complex.polar(abs:number, arg:number):static:map:[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">complex</code> instance with an absolute number <code class="highlighter-rouge">abs</code> and an angle <code class="highlighter-rouge">arg</code> in polar coords.
</p>
<p>
The argument <code class="highlighter-rouge">arg</code> is specified in a unit of radian. You can give it a degree value by calling the function with <code class="highlighter-rouge">:deg</code> attribute.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:complex|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>complex.roundoff(threshold:number =&gt; 1e-10) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a complex number with real and imaginary parts being rounded off.
</p>
<p>
The argument <code class="highlighter-rouge">threshold</code> specifies the threshold value for the round-off.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:complex|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h2><span class="caption-index-2">5.9</span><a name="anchor-5-9"></a>datetime Class</h2>
<h3><span class="caption-index-3">5.9.1</span><a name="anchor-5-9-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">datetime</code> class provides measures to handle date and time information.
</p>
<p>
You can create a <code class="highlighter-rouge">datetime</code> instance by calling following functions:
</p>
<ul>
<li><code class="highlighter-rouge">datetime()</code> .. Creates an intance from specified date and time.</li>
<li><code class="highlighter-rouge">datetime.now()</code> .. Creates an instance with its date and time fields set as the current one.</li>
<li><code class="highlighter-rouge">datetime.today()</code> .. Creates an instance with its date field set as the current one. Its time fields, <code class="highlighter-rouge">hour</code>, <code class="highlighter-rouge">min</code>, <code class="highlighter-rouge">sec</code> and <code class="highlighter-rouge">usec</code>, are set to zero.</li>
</ul>
<p>
You can calculate a <code class="highlighter-rouge">datetime</code> with a <code class="highlighter-rouge">timedelta</code> to put its date and time values forward and backward.
</p>
<h3><span class="caption-index-3">5.9.2</span><a name="anchor-5-9-2"></a>Predefined Variable</h3>
<table class="table">
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
<h3><span class="caption-index-3">5.9.3</span><a name="anchor-5-9-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">datetime</code> instance has the following properties:
</p>
<div class="mb-2"><code>datetime#day</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Day value betwen 1 and 31.
</div>
<div class="mb-2"><code>datetime#hour</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Hour value between 0 and 23.
</div>
<div class="mb-2"><code>datetime#min</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Minute value between 0 and 59.
</div>
<div class="mb-2"><code>datetime#month</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Month value between 1 and 12.
</div>
<div class="mb-2"><code>datetime#sec</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Second value between 0 and 59.
</div>
<div class="mb-2"><code>datetime#unixtime</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Unixtime, a time in second since January 1st of 1970.
</div>
<div class="mb-2"><code>datetime#usec</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Milli second value between 0 and 999999.
</div>
<div class="mb-2"><code>datetime#wday</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Week day value between 0 and 6.
</div>
<div class="mb-2"><code>datetime#week</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>datetime#yday</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Day in a year between 1 and 366.
</div>
<div class="mb-2"><code>datetime#year</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Year value between 1 and 9999.
</div>
<h3><span class="caption-index-3">5.9.4</span><a name="anchor-5-9-4"></a>Constructor</h3>
<div class="mb-2"><code>datetime(year:number, month:number, day:number, hour:number =&gt; 0, min:number =&gt; 0, sec:number =&gt; 0, usec:number =&gt; 0, minsoff?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an instance of <code class="highlighter-rouge">datetime</code> class based on the specified arguments.
</p>
<p>
Explanations of the arguments are shown below:
</p>
<ul>
<li><code class="highlighter-rouge">year</code> .. Christian year.</li>
<li><code class="highlighter-rouge">month</code> .. Month starting from 1. Numbers from 1 to 12 correspond to January to December.</li>
<li><code class="highlighter-rouge">day</code> .. Day in a month starting from 1.</li>
<li><code class="highlighter-rouge">hour</code> .. Hour in a day between 0 and 23.</li>
<li><code class="highlighter-rouge">min</code> .. Minute in an hour between 0 and 59.</li>
<li><code class="highlighter-rouge">sec</code> .. Second in a minute between 0 and 59.</li>
<li><code class="highlighter-rouge">usec</code> .. Millisecond in a second between 0 and 999.</li>
<li><code class="highlighter-rouge">minsoff</code> .. Timezone offset in minutes.</li>
</ul>
<p>
In default, the instance has a timezone offset based on the current system settings.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|dt:datetime|</code>, where <code class="highlighter-rouge">dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.9.5</span><a name="anchor-5-9-5"></a>Method</h3>
<div class="mb-2"><code>datetime#clrtzoff():reduce</code></div>
<div class="mb-2 ml-4">
Eliminates timezone offset information from the instance.
</div>
<div class="mb-2"><code>datetime#format(format =&gt; `w3c)</code></div>
<div class="mb-2 ml-4">
<p>
Returns a string of the datetime properties based on the specified format. For the argument <code class="highlighter-rouge">format</code>, you can specify either a string of user-specific format or a symbol of predefined style.
</p>
<p>
A string of user-specific format contains following specifiers:
</p>
<ul>
<li><code class="highlighter-rouge">%d</code> .. day of month</li>
<li><code class="highlighter-rouge">%H</code> .. hour in 24-hour format</li>
<li><code class="highlighter-rouge">%I</code> .. hour in 12-hour format</li>
<li><code class="highlighter-rouge">%m</code> .. month</li>
<li><code class="highlighter-rouge">%M</code> .. minute</li>
<li><code class="highlighter-rouge">%S</code> .. second</li>
<li><code class="highlighter-rouge">%w</code> .. week number starting from 0 for Sunday.</li>
<li><code class="highlighter-rouge">%y</code> .. lower two digits of year</li>
<li><code class="highlighter-rouge">%Y</code> .. four digits of year</li>
</ul>
<p>
Below are the symbols of predefined styles:
</p>
<ul>
<li><code class="highlighter-rouge">`w3c</code> .. W3C style. eg) <code class="highlighter-rouge">'2015-01-01T12:34:56+09:00'</code></li>
<li><code class="highlighter-rouge">`http</code> .. a style used in HTTP protocol. eg) <code class="highlighter-rouge">'Thu, 01 Jan 2015 12:34:56 +0900'</code></li>
<li><code class="highlighter-rouge">`asctime</code> .. a style used by the C function <code class="highlighter-rouge">asctime()</code>. eg) <code class="highlighter-rouge">'Thu Jan  1 12:34:56 +0900 2015'</code></li>
</ul>

</div>
<div class="mb-2"><code>datetime.isleap(year:number):static:map</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the specified year is a leap one.
</div>
<div class="mb-2"><code>datetime.monthdays(year:number, month:number):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a number of days that exists in the specified month.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>datetime.now():static:[utc] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">datetime</code> instance of the current time.
</p>
<p>
In default, the timezone offset is set to one in the system setting. Specifying <code class="highlighter-rouge">:utc</code> attribute would set the offset to 0.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|dt:datetime|</code>, where <code class="highlighter-rouge">dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>datetime.parse(str:string):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Parses a string that describs date and time information and returns the <code class="highlighter-rouge">datetime</code> instance.
</p>
<p>
It is capable of parsing the following style:
</p>
<ul>
<li>RFC1123 style. eg) <code class="highlighter-rouge">'Sat, 06 Nov 2010 08:49:37 GMT'</code></li>
<li>RFC1036 style. eg) <code class="highlighter-rouge">'Saturday, 06-Nov-10 08:49:37 GMT'</code></li>
<li>C's <code class="highlighter-rouge">asctime()</code> style. eg) <code class="highlighter-rouge">'Sat Nov  6 08:49:37 2010'</code>, <code class="highlighter-rouge">'Sat Nov  6 08:49:37 +0000 2010'</code></li>
<li>W3C style. eg) <code class="highlighter-rouge">'2010-11-06T08:49:37Z'</code></li>
</ul>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|dt:datetime|</code>, where <code class="highlighter-rouge">dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>datetime#settzoff(mins:number):reduce</code></div>
<div class="mb-2 ml-4">
Sets timezone offset in minutes.
</div>
<div class="mb-2"><code>datetime.time(hour:number =&gt; 0, minute:number =&gt; 0, sec:number =&gt; 0, usec:number =&gt; 0):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">datetime</code> instance from time information. The date inforomation is set as 1st of January in the Christian year of 0.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|dt:datetime|</code>, where <code class="highlighter-rouge">dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>datetime.today():static:[utc] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">datetime</code> instance of today. All the time information are cleared to 0.
</p>
<p>
In default, the timezone offset is set to one in the system setting. Specifying <code class="highlighter-rouge">:utc</code> attribute would set the offset to 0.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|dt:datetime|</code>, where <code class="highlighter-rouge">dt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>datetime#utc()</code></div>
<div class="mb-2 ml-4">
Calculates UTC time of the target <code class="highlighter-rouge">datetime</code> instance. An error occurs if the instance has no timezone offset
</div>
<div class="mb-2"><code>datetime.weekday(year:number, month:number, day:number):static:map</code></div>
<div class="mb-2 ml-4">
Returns a week number for the specified date, which starts from 0 for Sunday.
</div>
<h2><span class="caption-index-2">5.10</span><a name="anchor-5-10"></a>declaration Class</h2>
<h3><span class="caption-index-3">5.10.1</span><a name="anchor-5-10-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">declaration</code> class provides information about argument's declaration defined in a function. You can get an iterator of <code class="highlighter-rouge">declaration</code> instances with the following measures that the <code class="highlighter-rouge">function</code> class provides:
</p>
<ul>
<li>A property value: <code class="highlighter-rouge">function#decls</code></li>
<li>An instance method: <code class="highlighter-rouge">function.getdecls()</code></li>
</ul>
<p>
Below is an example to print argument names declared in a function.
</p>
<pre class="highlight"><code>f(a, b, c, d) = {}
println(f.decls:*name)
</code></pre>
<h3><span class="caption-index-3">5.10.2</span><a name="anchor-5-10-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">declaration</code> instance has the following properties:
</p>
<div class="mb-2"><code>declaration#default</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
An <code class="highlighter-rouge">expr</code> instance that represents a default value in the declaration if exists. This is <code class="highlighter-rouge">nil</code> when no default value is specified.
</div>
<div class="mb-2"><code>declaration#name</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">string</code> instance that represents the declaration's name.
</div>
<div class="mb-2"><code>declaration#symbol</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">symbol</code> instance that represents the declaration's name.
</div>
<h3><span class="caption-index-3">5.10.3</span><a name="anchor-5-10-3"></a>Method</h3>
<div class="mb-2"><code>declaration#istype(type+:expr):map</code></div>
<div class="mb-2 ml-4">
<p>
Return <code class="highlighter-rouge">true</code> if the declaration is defined as a type that is specified in the arguments.
</p>
<p>
The argument <code class="highlighter-rouge">type</code> has following formats:
</p>
<ul>
<li>a single symbol.</li>
<li>a sequence of symbols joined by a dot.</li>
</ul>
<p>
In the second format, a symbol on the left side indicates a container such as a module and a class.
</p>
<p>
Below is an example to check if the declaration is defined as <code class="highlighter-rouge">number</code> type.
</p>
<pre class="highlight"><code>decl.istype(`number)
</code></pre>
<p>
Below is an example to check if the declaration is defined as <code class="highlighter-rouge">re.match</code> type, which is a type named <code class="highlighter-rouge">match</code> defined in <code class="highlighter-rouge">re</code> module.
</p>
<pre class="highlight"><code>decl.istype(`re.match)
</code></pre>
<p>
You can also specify a type by describing factors in separate arguments like below:
</p>
<pre class="highlight"><code>decl.istype(`re, `match)
</code></pre>

</div>
<h2><span class="caption-index-2">5.11</span><a name="anchor-5-11"></a>dict Class</h2>
<h3><span class="caption-index-3">5.11.1</span><a name="anchor-5-11-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">dict</code> class provides measures to handle dictionary data that can seek values by indexing with their associated keys. You can specify values of <code class="highlighter-rouge">string</code>, <code class="highlighter-rouge">number</code> and <code class="highlighter-rouge">symbol</code> as a dictionary key.
</p>
<p>
You can create a <code class="highlighter-rouge">dict</code> instance by following measures:
</p>
<ul>
<li>Calls <code class="highlighter-rouge">dict()</code> constructor.</li>
<li>Calls a function named <code class="highlighter-rouge">%</code> that is an alias of <code class="highlighter-rouge">dict()</code> constructor.</li>
</ul>
<p>
Below are examples to create a <code class="highlighter-rouge">dict</code> instance:
</p>
<pre class="highlight"><code>dict {'first' =&gt; 1, 'second' =&gt; 2, 'third' =&gt; 3}
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
You can read and write element values in a <code class="highlighter-rouge">dict</code> with an indexer by giving it a key value which type is <code class="highlighter-rouge">string</code>, <code class="highlighter-rouge">number</code> or <code class="highlighter-rouge">symbol</code>. Below is an example:
</p>
<pre class="highlight"><code>x = %{'first' =&gt; 1, 'second' =&gt; 2, 'third' =&gt; 3}

println(x['second']) // prints `2`
x['third'] = 33      // replaces `3` with `33`
</code></pre>
<h3><span class="caption-index-3">5.11.3</span><a name="anchor-5-11-3"></a>Constructor</h3>
<div class="mb-2"><code>dict(elems?):[icase] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">dict</code> instance.
</p>
<p>
It takes a list of key-value pairs in an argument as shown below:
</p>
<pre class="highlight"><code>d = dict([['apple', 100], ['grape', 200], ['banana', 80]])
</code></pre>
<p>
Or, you can use a block to describe them like below:
</p>
<pre class="highlight"><code>d = dict {
    ['apple', 100], ['grape', 200], ['banana', 80]
}
</code></pre>
<p>
You can specify values of <code class="highlighter-rouge">number</code>, <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">symbol</code> as dictionary keys.
</p>
<p>
You can also use the operator <code class="highlighter-rouge">=&gt;</code> to create a key-value pair like below:
</p>
<pre class="highlight"><code>d = dict(['apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80])
</code></pre>
<p>
Below is an example using a block:
</p>
<pre class="highlight"><code>d = dict {
    'apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80
}
</code></pre>
<p>
The symbol <code class="highlighter-rouge">%</code> is an alias of the function <code class="highlighter-rouge">dict()</code>.
</p>
<pre class="highlight"><code>d = %{
    'apple' =&gt; 100, 'grape' =&gt; 200, 'banana' =&gt; 80
}
</code></pre>
<p>
In default, if keys contain alphabet characters, different cases are distinguished. Appending the attribute <code class="highlighter-rouge">:icase</code> would ignore cases in them.
</p>

</div>
<h3><span class="caption-index-3">5.11.4</span><a name="anchor-5-11-4"></a>Method</h3>
<div class="mb-2"><code>dict#append(elems?):reduce:[overwrite,strict,timid] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Adds multiple key-value pairs. It takes a list of key-value pairs in an argument or in a block that has the same format with one for the function <code class="highlighter-rouge">dict()</code>.
</p>
<p>
If the specified key already exists in the dictionary, it would be overwritten. This behavior can be customized with the following attributes:
</p>
<ul>
<li><code class="highlighter-rouge">:overwrite</code> .. overwrite the existing one (default)</li>
<li><code class="highlighter-rouge">:strict</code> .. raises an error</li>
<li><code class="highlighter-rouge">:timid</code> .. keep the existing one</li>
</ul>

</div>
<div class="mb-2"><code>dict#clear()</code></div>
<div class="mb-2 ml-4">
Clears all the key-value pairs in the dictionary.
</div>
<div class="mb-2"><code>dict#erase(key):map</code></div>
<div class="mb-2 ml-4">
<p>
Erases a key-value pair that mathces the provided <code class="highlighter-rouge">key</code>.
</p>
<p>
The <code class="highlighter-rouge">key</code> is either <code class="highlighter-rouge">number</code>, <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">symbol</code>.
</p>

</div>
<div class="mb-2"><code>dict#get(key, default?):map:[raise]</code></div>
<div class="mb-2 ml-4">
<p>
Seeks a value that is associated with the specified <code class="highlighter-rouge">key</code>.
</p>
<p>
The method would return <code class="highlighter-rouge">nil</code> as its default value when the specified key doesn't exist in the dictionary. It would use different value if the argument <code class="highlighter-rouge">default</code> is specified.
</p>
<p>
Since the <code class="highlighter-rouge">default</code> value is also processed with implicit mapping, you have to apply <code class="highlighter-rouge">object#nomap()</code> method to it if you want to specify a list or an iterator as a default value.
</p>
<p>
When the attribute <code class="highlighter-rouge">:raise</code> is specified, an error occurs in the case of the key's absence.
</p>
<p>
Another measure to get a value associated with a key is to use an index operator. The following two codes have the same effect.
</p>
<ul>
<li><code class="highlighter-rouge">v = d['foo']</code></li>
<li><code class="highlighter-rouge">v = d.get('foo'):raise</code></li>
</ul>

</div>
<div class="mb-2"><code>dict#haskey(key):map</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the specified <code class="highlighter-rouge">key</code> exists in the dictionary.
</div>
<div class="mb-2"><code>dict#items() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an iterator of key-value pairs in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>dict#keys() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an iterator of keys in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>dict#len()</code></div>
<div class="mb-2 ml-4">
Returns the number of key-value pairs in the dictionary.
</div>
<div class="mb-2"><code>dict#put(key, value):map:reduce:[overwrite,strict,timid]</code></div>
<div class="mb-2 ml-4">
<p>
Adds a new key-value pair.
</p>
<p>
If the specified key already exists in the dictionary, it would be overwritten. This behavior can be customized with the following attributes:
</p>
<ul>
<li><code class="highlighter-rouge">:overwrite</code> .. overwrite the existing one (default)</li>
<li><code class="highlighter-rouge">:strict</code> .. raises an error</li>
<li><code class="highlighter-rouge">:timid</code> .. keep the existing one</li>
</ul>
<p>
Another measure to add a key-value pair is to use an index operator. The following two codes have the same effect.
</p>
<ul>
<li><code class="highlighter-rouge">d['foo'] = 3</code></li>
<li><code class="highlighter-rouge">d.put('foo', 3)</code></li>
</ul>

</div>
<div class="mb-2"><code>dict#values() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an iterator of values in the dictionary.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h2><span class="caption-index-2">5.12</span><a name="anchor-5-12"></a>directory Class</h2>
<h3><span class="caption-index-3">5.12.1</span><a name="anchor-5-12-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">directory</code> class handles information necessary to seek directory structure in a path. Its instance usually works with functions in <code class="highlighter-rouge">path</code> module: <code class="highlighter-rouge">path.dir()</code> and <code class="highlighter-rouge">path.walk()</code>.
</p>
<p>
Though the instance can be created by <code class="highlighter-rouge">directory()</code> function, you don't have to use it in many cases because a casting from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">directory</code> instance works implicitly in a function call.
</p>
<h3><span class="caption-index-3">5.12.2</span><a name="anchor-5-12-2"></a>Constructor</h3>
<div class="mb-2"><code>directory(pathname:string):map {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">directory</code> instance from the specified path name.
</div>
<h2><span class="caption-index-2">5.13</span><a name="anchor-5-13"></a>environment Class</h2>
<h3><span class="caption-index-3">5.13.1</span><a name="anchor-5-13-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">environment</code> class provides measures to operate variables in an environment, which is a fundamental mechanism to store variables.
</p>
<h3><span class="caption-index-3">5.13.2</span><a name="anchor-5-13-2"></a>Method</h3>
<div class="mb-2"><code>environment#getprop!(symbol:symbol):map</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>environment#lookup(symbol:symbol, escalate:boolean =&gt; true):map</code></div>
<div class="mb-2 ml-4">
Looks up a specified symbol in the environment and returns the associated value. In default, if the symbol is not defined in the environment, it will be searched in environments outside of the current one. Set escalate flag to false in order to disable such an escalation behaviour. Returns false when the symbol could not be found.
</div>
<div class="mb-2"><code>environment#setprop!(symbol:symbol, value):map</code></div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.14</span><a name="anchor-5-14"></a>error Class</h2>
<h3><span class="caption-index-3">5.14.1</span><a name="anchor-5-14-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">error</code> class provides measures to access error information.
</p>
<p>
There is no measures to create an <code class="highlighter-rouge">error</code> instance. They're instantiated and passed to a block of <code class="highlighter-rouge">catch()</code> function when an error occurs within a <code class="highlighter-rouge">try</code> block in a <code class="highlighter-rouge">try-catch</code> sequence.
</p>
<p>
In the following code, <code class="highlighter-rouge">e</code> is an instance that contains information about an error that has occured in the <code class="highlighter-rouge">try</code> block.
</p>
<pre class="highlight"><code>try {
    // any jobs
} catch {|e:error|
    // ...
}
</code></pre>
<h3><span class="caption-index-3">5.14.2</span><a name="anchor-5-14-2"></a>Predefined Variable</h3>
<table class="table">
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
<h3><span class="caption-index-3">5.14.3</span><a name="anchor-5-14-3"></a>Property</h3>
<p>
An <code class="highlighter-rouge">error</code> instance has the following properties:
</p>
<div class="mb-2"><code>error#lineno</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
The number of line where the expression that causes this error starts.
</div>
<div class="mb-2"><code>error#linenobtm</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
The number of line where the expression that causes this error ends.
</div>
<div class="mb-2"><code>error#postext</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A text that consists of a source name and a line number.
</div>
<div class="mb-2"><code>error#source</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
The name of the file that causes this error.
</div>
<div class="mb-2"><code>error#text</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
An error message. If an attribute <code class="highlighter-rouge">:lineno</code> is specified, it would contain a line number.
</div>
<div class="mb-2"><code>error#trace</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator that generates <code class="highlighter-rouge">expr</code> instances that indicate stack trace.
</div>
<h2><span class="caption-index-2">5.15</span><a name="anchor-5-15"></a>expr Class</h2>
<h3><span class="caption-index-3">5.15.1</span><a name="anchor-5-15-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">expr</code> class provides inromation about the language's syntax expression.
</p>
<h3><span class="caption-index-3">5.15.2</span><a name="anchor-5-15-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">expr</code> instance has the following properties:
</p>
<div class="mb-2"><code>expr#attrfront</code> &hellip; <code>list</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "identifier" and "caller".
</div>
<div class="mb-2"><code>expr#attrs</code> &hellip; <code>list</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "identifier" and "caller".
</div>
<div class="mb-2"><code>expr#attrsopt</code> &hellip; <code>list</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "identifier" and "caller".
</div>
<div class="mb-2"><code>expr#block</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "caller".
</div>
<div class="mb-2"><code>expr#blockparam</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "block".
</div>
<div class="mb-2"><code>expr#body</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "suffixed".
</div>
<div class="mb-2"><code>expr#car</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "compound".
</div>
<div class="mb-2"><code>expr#cdr</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "compound".
</div>
<div class="mb-2"><code>expr#child</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "unary".
</div>
<div class="mb-2"><code>expr#children</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "collector".
</div>
<div class="mb-2"><code>expr#left</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "binary".
</div>
<div class="mb-2"><code>expr#lineno</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>expr#linenobtm</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>expr#operator</code> &hellip; <code>operator</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "unaryop", "binaryop" and "assign".
</div>
<div class="mb-2"><code>expr#postext</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>expr#right</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "binary".
</div>
<div class="mb-2"><code>expr#source</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>expr#suffix</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "suffixed".
</div>
<div class="mb-2"><code>expr#symbol</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "identifier".
</div>
<div class="mb-2"><code>expr#trailer</code> &hellip; <code>expr</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "caller".
</div>
<div class="mb-2"><code>expr#typename</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>expr#typesym</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>expr#value</code> &hellip; <code>any</code> [read-only]</div>
<div class="mb-2 ml-4">
Exists in "value".
</div>
<h3><span class="caption-index-3">5.15.3</span><a name="anchor-5-15-3"></a>Constructor</h3>
<div class="mb-2"><code>expr(src:stream:r):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Parses a Gura script from the stream <code class="highlighter-rouge">src</code> and creates an <code class="highlighter-rouge">expr</code> instance.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|expr:expr|</code>, where <code class="highlighter-rouge">expr</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.15.4</span><a name="anchor-5-15-4"></a>Method</h3>
<div class="mb-2"><code>expr#eval(env?:environment) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Evaluates the <code class="highlighter-rouge">expr</code> instance.
</p>
<p>
If the argument <code class="highlighter-rouge">env</code> is specified, that environment is used for evaluation. If omitted, the current scope is used.
</p>

</div>
<div class="mb-2"><code>expr.parse(script:string):static:map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Parses a Gura script in the string <code class="highlighter-rouge">script</code> and creates an <code class="highlighter-rouge">expr</code> instance.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it will be evaluated with block parameter in a format of <code class="highlighter-rouge">|expr:expr|</code> where <code class="highlighter-rouge">expr</code> is the created instance.
</p>

</div>
<div class="mb-2"><code>expr#textize(style?:symbol, indent?:string)</code></div>
<div class="mb-2 ml-4">
<p>
Composes a script text from a content of <code class="highlighter-rouge">expr</code>.
</p>
<p>
Argument <code class="highlighter-rouge">style</code> specifies the text style output, which takes the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`crammed</code> .. Puts all the text in one line and removes volatile spaces.</li>
<li><code class="highlighter-rouge">`oneline</code> .. Puts all the text in one line.</li>
<li><code class="highlighter-rouge">`brief</code> .. Omits content of blocks and long strings with "<code class="highlighter-rouge">..</code>".</li>
<li><code class="highlighter-rouge">`fancy</code> .. Prints in the most readable style. This is the default.</li>
</ul>
<p>
The argument <code class="highlighter-rouge">indent</code> specifies a string used for indentation. Its default is a sequence of four spaces.
</p>

</div>
<div class="mb-2"><code>expr#tofunction(`args*)</code></div>
<div class="mb-2 ml-4">
<p>
Converts the <code class="highlighter-rouge">expr</code> into a function.
</p>
<p>
If the <code class="highlighter-rouge">expr</code> is a block that has a block parameter, that would be used as an argument list of the created function. Otherwise, the argument <code class="highlighter-rouge">args</code> declares the argument list.
</p>
<p>
It would be an error if <code class="highlighter-rouge">args</code> is specified and a block parameter exists as well.
</p>

</div>
<div class="mb-2"><code>expr#unquote()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">expr</code> instance that has removed quote operator from the original <code class="highlighter-rouge">expr</code>.
</div>
<div class="mb-2"><code>expr#write(dst:stream:w, style?:symbol, indent?:string)</code></div>
<div class="mb-2 ml-4">
<p>
Outputs a script that describes the expression to the specified <code class="highlighter-rouge">stream</code>.
</p>
<p>
Argument <code class="highlighter-rouge">style</code> specifies the text style output, which takes the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`crammed</code> .. Puts all the text in one line and removes volatile spaces.</li>
<li><code class="highlighter-rouge">`oneline</code> .. Puts all the text in one line.</li>
<li><code class="highlighter-rouge">`brief</code> .. Omits content of blocks and long strings with "<code class="highlighter-rouge">..</code>".</li>
<li><code class="highlighter-rouge">`fancy</code> .. Prints in the most readable style. This is the default.</li>
</ul>
<p>
The argument <code class="highlighter-rouge">indent</code> specifies a string used for indentation. Its default is a sequence of four spaces.
</p>

</div>
<div class="mb-2"><code>expr#isunary()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of unary.
</div>
<div class="mb-2"><code>expr#isunaryop()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of unaryop.
</div>
<div class="mb-2"><code>expr#isquote()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of quote.
</div>
<div class="mb-2"><code>expr#isbinary()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of binary.
</div>
<div class="mb-2"><code>expr#isbinaryop()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of binaryop.
</div>
<div class="mb-2"><code>expr#isassign()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of assign.
</div>
<div class="mb-2"><code>expr#ismember()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of member.
</div>
<div class="mb-2"><code>expr#iscollector()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of collector.
</div>
<div class="mb-2"><code>expr#isroot()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of root.
</div>
<div class="mb-2"><code>expr#isblock()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of block.
</div>
<div class="mb-2"><code>expr#islister()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of lister.
</div>
<div class="mb-2"><code>expr#isiterer()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of iterer.
</div>
<div class="mb-2"><code>expr#iscompound()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of compound.
</div>
<div class="mb-2"><code>expr#isindexer()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of indexer.
</div>
<div class="mb-2"><code>expr#iscaller()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of caller.
</div>
<div class="mb-2"><code>expr#isvalue()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of value.
</div>
<div class="mb-2"><code>expr#isidentifier()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of identifier.
</div>
<div class="mb-2"><code>expr#issuffixed()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if expr is an expression of suffixed.
</div>
<h2><span class="caption-index-2">5.16</span><a name="anchor-5-16"></a>formatter Class</h2>
<h3><span class="caption-index-3">5.16.1</span><a name="anchor-5-16-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">formatter</code> class provides information about a format specifier.
</p>
<p>
The function <code class="highlighter-rouge">printf()</code> has the following declaration:
</p>
<pre class="highlight"><code>printf('name: %s, age: %d\n', name, age)
</code></pre>
<p>
The first argument is a string containing format specifiers like <code class="highlighter-rouge">%s</code> and <code class="highlighter-rouge">%d</code> that determine the manner on how the correspoding values <code class="highlighter-rouge">name</code> and <code class="highlighter-rouge">age</code> should be formatted. In the formatting mechanism, when the specifiers <code class="highlighter-rouge">%s</code> and <code class="highlighter-rouge">%d</code> appear, it would call methods <code class="highlighter-rouge">name.__format_s__()</code> and <code class="highlighter-rouge">age.__format_s__()</code> respectively which are format handlers responsible of formatting these values. In general, a format handler has a format like <code class="highlighter-rouge">__format_X__(fmt:formatter)</code> where <code class="highlighter-rouge">X</code> is the symbol of the specifier and <code class="highlighter-rouge">fmt</code> is a <code class="highlighter-rouge">formatter</code> instance that carries information about the associated specifier such as minimum width and a padding character. The handler must return a <code class="highlighter-rouge">string</code> as its result.
</p>
<p>
The table below summarizes associations between specifiers and the method name of their format handlers:
</p>
<table class="table">
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
<p>
This feature is supposed to be used when you want your original class's instance properly formatted in <code class="highlighter-rouge">printf</code>. Below is an example to implement a format handler for the specifier <code class="highlighter-rouge">%d</code>:
</p>
<pre class="highlight"><code>A = class {

    // any implementations

    __format_d__(fmt:format) = {
        // returns a string for %d specifier.
    }
}

a = A()
printf('%d', a) // a.__format_d__() is called
</code></pre>
<h3><span class="caption-index-3">5.16.2</span><a name="anchor-5-16-2"></a>Method</h3>
<div class="mb-2"><code>formatter#getminwidth()</code></div>
<div class="mb-2 ml-4">
<p>
Returns an expected minimum width for the field.
</p>
<p>
For example, with <code class="highlighter-rouge">'%3d'</code>, this method would return <code class="highlighter-rouge">3</code>.
</p>

</div>
<div class="mb-2"><code>formatter#getpadding()</code></div>
<div class="mb-2 ml-4">
<p>
Returns a string containing a padding character, a space or <code class="highlighter-rouge">'0'</code>.
</p>
<p>
In default, a space is used for padding. For example, with <code class="highlighter-rouge">'%3d'</code>, this method would return <code class="highlighter-rouge">' '</code>.
</p>
<p>
When a character <code class="highlighter-rouge">'0'</code> appears after <code class="highlighter-rouge">'%'</code>, that becomes the padding character. For example, with <code class="highlighter-rouge">'%03d'</code>, this method would return <code class="highlighter-rouge">'0'</code>.
</p>

</div>
<div class="mb-2"><code>formatter#getplusmode()</code></div>
<div class="mb-2 ml-4">
<p>
Returns a symbol that indicates an expected action when a positive number appears.
</p>
<ul>
<li><code class="highlighter-rouge">`none</code> .. No character ahead of the number.</li>
<li><code class="highlighter-rouge">`space</code> .. A space should be inserted.</li>
<li><code class="highlighter-rouge">`plus</code> .. A plus character should be inserted.</li>
</ul>

</div>
<div class="mb-2"><code>formatter#getprecision()</code></div>
<div class="mb-2 ml-4">
<p>
Returns an expected precision for the field.
</p>
<p>
For example, with <code class="highlighter-rouge">'%.3d'</code>, this method would return <code class="highlighter-rouge">3</code>.
</p>

</div>
<div class="mb-2"><code>formatter#isleftalign()</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the field is expected to be aligned on left.
</p>
<p>
For example, with <code class="highlighter-rouge">'%-3d'</code>, this method would return <code class="highlighter-rouge">true</code>.
</p>

</div>
<div class="mb-2"><code>formatter#issharp()</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the specifier sequence includes <code class="highlighter-rouge">'#'</code> flag, which means some literal prefixes such as <code class="highlighter-rouge">0x</code> are expected to be appended at the top.
</p>
<p>
For example, with <code class="highlighter-rouge">'%#x'</code>, this method would return <code class="highlighter-rouge">true</code>.
</p>

</div>
<div class="mb-2"><code>formatter#isuppercase()</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if alphabet characters are expected to be shown in upper case.
</p>
<p>
Upper case characters are requested when a specifier such as <code class="highlighter-rouge">'%X'</code>, <code class="highlighter-rouge">'%E'</code> and <code class="highlighter-rouge">'%G'</code> is specified.
</p>

</div>
<h2><span class="caption-index-2">5.17</span><a name="anchor-5-17"></a>function Class</h2>
<h3><span class="caption-index-3">5.17.1</span><a name="anchor-5-17-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">function</code> class provides measure to inspect information about the instance.
</p>
<p>
All the functions are instances of <code class="highlighter-rouge">function</code> class, so an implementation of a function means a realization of a <code class="highlighter-rouge">function</code> instance. You can also create the instance using <code class="highlighter-rouge">function()</code> constructor. The following two codes have the same result:
</p>
<pre class="highlight"><code>f(a:number, b:number, c:number) = {
    (a + b + c) / 3
}

f = function(a:number, b:number, c:number) {
    (a + b + c) / 3
}
</code></pre>
<p>
Using <code class="highlighter-rouge">function()</code>, you can use variables prefixed by a dollar character so that they are automatically added to the argument list. In such a case, the variables are added to the argument list in the same order as they appear in the function body. The code below creates a function with a declaration <code class="highlighter-rouge">f($a, $b, $c)</code>.
</p>
<pre class="highlight"><code>f = function {
    ($a + $b + $c) / 3
}
</code></pre>
<p>
You can use <code class="highlighter-rouge">&amp;</code> as an alias of <code class="highlighter-rouge">function()</code> as shown below:
</p>
<pre class="highlight"><code>f = &amp;{
    ($a + $b + $c) / 3
}
</code></pre>
<h3><span class="caption-index-3">5.17.2</span><a name="anchor-5-17-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">function</code> instance has the following properties:
</p>
<div class="mb-2"><code>function#decls</code> &hellip; <code>iterator</code> [read-only]</div>
<div class="mb-2 ml-4">
An iterator of <code class="highlighter-rouge">declaration</code> instances that provide information about argument declaration the function defines.
</div>
<div class="mb-2"><code>function#expr</code> &hellip; <code>expr</code> [read/write]</div>
<div class="mb-2 ml-4">
An expression of the function.
</div>
<div class="mb-2"><code>function#format</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A string showing a declared format of the function.
</div>
<div class="mb-2"><code>function#fullname</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A full name of the function that is prefixed by a name of the module or the class it belongs to.
</div>
<div class="mb-2"><code>function#name</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">string</code> instance that represents the function's name.
</div>
<div class="mb-2"><code>function#symbol</code> &hellip; <code>symbol</code> [read/write]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">symbol</code> instance that represents the function's name.
</div>
<h3><span class="caption-index-3">5.17.3</span><a name="anchor-5-17-3"></a>Operator</h3>
<p>
You can print a function's help from the interactive prompt using the unary operator "<code class="highlighter-rouge">~</code>". Below is an example to print the help of <code class="highlighter-rouge">printf()</code> function:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; ~printf
</code></pre>
<h3><span class="caption-index-3">5.17.4</span><a name="anchor-5-17-4"></a>Constructor</h3>
<div class="mb-2"><code>function(`args*) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">function</code> instance with an argument list of <code class="highlighter-rouge">args</code> and a procedure body provided by <code class="highlighter-rouge">block</code>.
</p>
<p>
Following two codes have the same effect with each other.
</p>
<ul>
<li><code class="highlighter-rouge">f = function(a, b, c) { /* any job */ }</code></li>
<li><code class="highlighter-rouge">f(a, b, c) = { /* any job */ }</code></li>
</ul>

</div>
<h3><span class="caption-index-3">5.17.5</span><a name="anchor-5-17-5"></a>Method</h3>
<div class="mb-2"><code>function.getdecls(func:function):static:map</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator of <code class="highlighter-rouge">declaration</code> instances that provide information about argument declaration that the function instance <code class="highlighter-rouge">func</code> defines.
</p>
<p>
This class method returns the same information as the property <code class="highlighter-rouge">function#decls</code>.
</p>

</div>
<div class="mb-2"><code>function.getexpr(func:function):static:map</code></div>
<div class="mb-2 ml-4">
<p>
Returns an expression of the function instance <code class="highlighter-rouge">func</code>.
</p>
<p>
It would return <code class="highlighter-rouge">nil</code> if the function is implemented with binary programs, not scripts.
</p>
<p>
This class method returns the same information as the property <code class="highlighter-rouge">function#expr</code>.
</p>

</div>
<div class="mb-2"><code>function.getformat(func:function):static:map</code></div>
<div class="mb-2 ml-4">
<p>
Returns a string showing a declared format of the function instance <code class="highlighter-rouge">func</code>.
</p>
<p>
This class method returns the same information as the property <code class="highlighter-rouge">function#format</code>.
</p>

</div>
<div class="mb-2"><code>function.getfullname(func:function):static:map</code></div>
<div class="mb-2 ml-4">
<p>
Returns a full name of the function instance <code class="highlighter-rouge">func</code>, which is prefixed by a name of the module or the class the instance belongs to.
</p>
<p>
This class method returns the same information as the property <code class="highlighter-rouge">function#fullname</code>.
</p>

</div>
<div class="mb-2"><code>function.getname(func:function):static:map</code></div>
<div class="mb-2 ml-4">
<p>
Returns a name of the function instance <code class="highlighter-rouge">func</code> in <code class="highlighter-rouge">string</code> type.
</p>
<p>
This class method returns the same information as the property <code class="highlighter-rouge">function#name</code>.
</p>

</div>
<div class="mb-2"><code>function.getsymbol(func:function):static:map</code></div>
<div class="mb-2 ml-4">
<p>
Returns a name of the function instance <code class="highlighter-rouge">func</code> in <code class="highlighter-rouge">symbol</code> type.
</p>
<p>
This class method returns the same information as the property <code class="highlighter-rouge">function#symbol</code>.
</p>

</div>
<div class="mb-2"><code>function#mathdiff(var?:symbol):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Returns a <code class="highlighter-rouge">function</code> instance that computes derivation of the target function, which is expected to contain only mathematical procedures. An error occurs if the target function has any elements that have nothing to do with mathematics.
</p>
<p>
In default, it differentiates the target function with respect to its first argument. Below is an example:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; f(x) = math.sin(x)
&gt;&gt;&gt; g = f.mathdiff()    // g is a function to compute math.cos(x)
</code></pre>
<p>
Specify a symbol to argument <code class="highlighter-rouge">var</code> when you want to differentiate with respect to another variable.
</p>
<p>
You can check the result of derivation by seeing property <code class="highlighter-rouge">function#expr</code> like below:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; g.expr
`math.cos(x)
</code></pre>

</div>
<h2><span class="caption-index-2">5.18</span><a name="anchor-5-18"></a>gear@averagepool1d Class</h2>
<h3><span class="caption-index-3">5.18.1</span><a name="anchor-5-18-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.18.2</span><a name="anchor-5-18-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@averagepool1d(size:number, strides?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">gear@averagepool1d</code> instance.
</p>
<p>
The <code class="highlighter-rouge">size</code> is a gear size.
</p>
<p>
The <code class="highlighter-rouge">strides</code> is a strides of sliding window. Default is one.
</p>
<p>
The <code class="highlighter-rouge">padding</code> is a padding style <code class="highlighter-rouge">`valid</code> or <code class="highlighter-rouge">`same</code>. Default is <code class="highlighter-rouge">`same</code>.
</p>
<p>
The <code class="highlighter-rouge">channel_pos</code> specifies where channel dimension is positioned and takes <code class="highlighter-rouge">`first</code> or <code class="highlighter-rouge">`last</code>. Default is <code class="highlighter-rouge">`last</code>.
</p>

</div>
<h3><span class="caption-index-3">5.18.3</span><a name="anchor-5-18-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@averagepool1d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@averagepool1d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@averagepool1d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@averagepool1d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@averagepool1d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.19</span><a name="anchor-5-19"></a>gear@averagepool2d Class</h2>
<h3><span class="caption-index-3">5.19.1</span><a name="anchor-5-19-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.19.2</span><a name="anchor-5-19-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@averagepool2d(size[]:number, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@averagepool2d</code> instance.
</div>
<h3><span class="caption-index-3">5.19.3</span><a name="anchor-5-19-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@averagepool2d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@averagepool2d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@averagepool2d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@averagepool2d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@averagepool2d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.20</span><a name="anchor-5-20"></a>gear@averagepool3d Class</h2>
<h3><span class="caption-index-3">5.20.1</span><a name="anchor-5-20-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.20.2</span><a name="anchor-5-20-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@averagepool3d(size[]:number, strides[]?:number, padding?:symbol, format?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@averagepool3d</code> instance.
</div>
<h3><span class="caption-index-3">5.20.3</span><a name="anchor-5-20-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@averagepool3d</code> instance has the following properties:
</p>
<h2><span class="caption-index-2">5.21</span><a name="anchor-5-21"></a>gear@conv1d Class</h2>
<h3><span class="caption-index-3">5.21.1</span><a name="anchor-5-21-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.21.2</span><a name="anchor-5-21-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@conv1d(array:array, strides?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">gear@conv1d</code> instance.
</p>
<p>
The <code class="highlighter-rouge">array</code> is an <code class="highlighter-rouge">array</code> instance that has one of the following shapes:
</p>
<ul>
<li><code class="highlighter-rouge">[size]</code> .. 1-dimension</li>
<li><code class="highlighter-rouge">[size, channel_num]</code> .. 2-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`last</code></li>
<li><code class="highlighter-rouge">[channel_num, size]</code> .. 2-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`first</code></li>
<li><code class="highlighter-rouge">[filter_num, size]</code> .. 2-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`none</code></li>
<li><code class="highlighter-rouge">[filter_num, size, channel_num]</code> .. 3-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`last</code></li>
<li><code class="highlighter-rouge">[filter_num, channel_num, size]</code> .. 3-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`first</code></li>
</ul>
<p>
where <code class="highlighter-rouge">size</code> is the size of the filter's kernel, <code class="highlighter-rouge">channel_num</code> is the number of channels and <code class="highlighter-rouge">filter_num</code> is the number of filters.
</p>
<p>
The <code class="highlighter-rouge">strides</code> is a strides for a sliding window. Default is one.
</p>
<p>
The <code class="highlighter-rouge">padding</code> is a padding style and takes <code class="highlighter-rouge">`valid</code> or <code class="highlighter-rouge">`same</code>. Default is <code class="highlighter-rouge">`same</code>. When <code class="highlighter-rouge">valid</code> is specified, there is no padding. When <code class="highlighter-rouge">same</code> is specified, zero values are padded so that the result array has the size of the division of the original size by <code class="highlighter-rouge">strides</code>.
</p>
<p>
The <code class="highlighter-rouge">channel_pos</code> is a channel position and takes <code class="highlighter-rouge">`none</code>, <code class="highlighter-rouge">`first</code> or <code class="highlighter-rouge">`last</code>. If not specified, <code class="highlighter-rouge">`none` for an array without channel dimension</code>and <code class="highlighter-rouge">`last</code> for others are to be set.
</p>

</div>
<h3><span class="caption-index-3">5.21.3</span><a name="anchor-5-21-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@conv1d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@conv1d#array</code> &hellip; <code>array</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv1d#channel_num</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv1d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv1d#filter_num</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv1d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv1d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv1d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.22</span><a name="anchor-5-22"></a>gear@conv2d Class</h2>
<h3><span class="caption-index-3">5.22.1</span><a name="anchor-5-22-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.22.2</span><a name="anchor-5-22-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@conv2d(array:array, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">gear@conv2d</code> instance.
</p>
<p>
The given <code class="highlighter-rouge">array</code> instance shoud have one of the following shapes:
</p>
<ul>
<li><code class="highlighter-rouge">[row_size, col_size]</code> .. 2-dimensions</li>
<li><code class="highlighter-rouge">[row_size, col_size, channel_num]</code> .. 3-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`last</code></li>
<li><code class="highlighter-rouge">[channel_num, row_size, col_size]</code> .. 3-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`first</code></li>
<li><code class="highlighter-rouge">[filter_num, row_size, col_size]</code> .. 3-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`none</code></li>
<li><code class="highlighter-rouge">[filter_num, row_size, col_size, channel_num]</code> .. 4-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`last</code></li>
<li><code class="highlighter-rouge">[filter_num, channel_num, row_size, col_size]</code> .. 4-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`first</code></li>
</ul>
<p>
where <code class="highlighter-rouge">row_size</code> and <code class="highlighter-rouge">col_size</code> are the size of the filter's kernel, <code class="highlighter-rouge">channel_num</code> is the number of channels and <code class="highlighter-rouge">filter_num</code> is the number of filters.
</p>
<p>
The <code class="highlighter-rouge">strides</code> is a list of strides for a sliding window in row and column. Default is <code class="highlighter-rouge">[1, 1]</code>.
</p>
<p>
The <code class="highlighter-rouge">padding</code> is a padding style and takes <code class="highlighter-rouge">`valid</code> or <code class="highlighter-rouge">`same</code>. Default is <code class="highlighter-rouge">`same</code>. When <code class="highlighter-rouge">valid</code> is specified, there is no padding. When <code class="highlighter-rouge">same</code> is specified, zero values are padded so that the result array has the size of the division of the original size by <code class="highlighter-rouge">strides</code>.
</p>
<p>
The <code class="highlighter-rouge">channel_pos</code> is a channel position and takes <code class="highlighter-rouge">`none</code>, <code class="highlighter-rouge">`first</code> or <code class="highlighter-rouge">`last</code>. If not specified, <code class="highlighter-rouge">`none` for an array without channel dimension</code>and <code class="highlighter-rouge">`last</code> for others are to be set.
</p>

</div>
<h3><span class="caption-index-3">5.22.3</span><a name="anchor-5-22-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@conv2d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@conv2d#array</code> &hellip; <code>array</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv2d#channel_num</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv2d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv2d#filter_num</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv2d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv2d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv2d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.23</span><a name="anchor-5-23"></a>gear@conv3d Class</h2>
<h3><span class="caption-index-3">5.23.1</span><a name="anchor-5-23-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.23.2</span><a name="anchor-5-23-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@conv3d(array:array, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">gear@conv3d</code> instance.
</p>
<p>
The given <code class="highlighter-rouge">array</code> instance shoud have one of the following shapes:
</p>
<ul>
<li><code class="highlighter-rouge">[plane_size, row_size, col_size]</code> .. 3-dimensions</li>
<li><code class="highlighter-rouge">[plane_size, row_size, col_size, channel_num]</code> .. 4-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`last</code></li>
<li><code class="highlighter-rouge">[channel_num, plane_size, row_size, col_size]</code> .. 4-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`first</code></li>
<li><code class="highlighter-rouge">[filter_num, plane_size, row_size, col_size]</code> .. 4-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`none</code></li>
<li><code class="highlighter-rouge">[filter_num, plane_size, row_size, col_size, channel_num]</code> .. 5-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`last</code></li>
<li><code class="highlighter-rouge">[filter_num, channel_num, plane_size, row_size, col_size]</code> .. 5-dimensions and <code class="highlighter-rouge">channel_pos</code> is <code class="highlighter-rouge">`first</code></li>
</ul>
<p>
where <code class="highlighter-rouge">plane_size</code>, <code class="highlighter-rouge">row_size</code> and <code class="highlighter-rouge">col_size</code> are the size of the filter's kernel, <code class="highlighter-rouge">channel_num</code> is the number of channels and <code class="highlighter-rouge">filter_num</code> is the number of filters.
</p>
<p>
The <code class="highlighter-rouge">strides</code> is a list of strides for a sliding window in plane, row and column. Default is <code class="highlighter-rouge">[1, 1, 1]</code>.
</p>
<p>
The <code class="highlighter-rouge">padding</code> is a padding style and takes <code class="highlighter-rouge">`valid</code> or <code class="highlighter-rouge">`same</code>. Default is <code class="highlighter-rouge">`same</code>. When <code class="highlighter-rouge">valid</code> is specified, there is no padding. When <code class="highlighter-rouge">same</code> is specified, zero values are padded so that the result array has the size of the division of the original size by <code class="highlighter-rouge">strides</code>.
</p>
<p>
The <code class="highlighter-rouge">channel_pos</code> is a channel position and takes <code class="highlighter-rouge">`none</code>, <code class="highlighter-rouge">`first</code> or <code class="highlighter-rouge">`last</code>. If not specified, <code class="highlighter-rouge">`none` for an array without channel dimension</code>and <code class="highlighter-rouge">`last</code> for others are to be set.
</p>

</div>
<h3><span class="caption-index-3">5.23.3</span><a name="anchor-5-23-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@conv3d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@conv3d#array</code> &hellip; <code>array</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv3d#channel_num</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv3d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv3d#filter_num</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv3d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv3d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@conv3d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.24</span><a name="anchor-5-24"></a>gear@maxpool1d Class</h2>
<h3><span class="caption-index-3">5.24.1</span><a name="anchor-5-24-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.24.2</span><a name="anchor-5-24-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@maxpool1d(size:number, strides?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">gear@maxpool1d</code> instance.
</p>
<p>
The <code class="highlighter-rouge">size</code> is a gear size.
</p>
<p>
The <code class="highlighter-rouge">strides</code> is a strides of sliding window. Default is one.
</p>
<p>
The <code class="highlighter-rouge">padding</code> is a padding style <code class="highlighter-rouge">`valid</code> or <code class="highlighter-rouge">`same</code>. Default is <code class="highlighter-rouge">`same</code>.
</p>
<p>
The <code class="highlighter-rouge">channel_pos</code> specifies where channel dimension is positioned and takes <code class="highlighter-rouge">`first</code> or <code class="highlighter-rouge">`last</code>. Default is <code class="highlighter-rouge">`last</code>.
</p>

</div>
<h3><span class="caption-index-3">5.24.3</span><a name="anchor-5-24-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@maxpool1d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@maxpool1d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@maxpool1d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@maxpool1d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@maxpool1d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.25</span><a name="anchor-5-25"></a>gear@maxpool2d Class</h2>
<h3><span class="caption-index-3">5.25.1</span><a name="anchor-5-25-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.25.2</span><a name="anchor-5-25-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@maxpool2d(size[]:number, strides[]?:number, padding?:symbol, channel_pos?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@maxpool2d</code> instance.
</div>
<h3><span class="caption-index-3">5.25.3</span><a name="anchor-5-25-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@maxpool2d</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@maxpool2d#channel_pos</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@maxpool2d#padding</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@maxpool2d#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gear@maxpool2d#strides</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.26</span><a name="anchor-5-26"></a>gear@maxpool3d Class</h2>
<h3><span class="caption-index-3">5.26.1</span><a name="anchor-5-26-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.26.2</span><a name="anchor-5-26-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@maxpool3d(size[]:number, strides[]?:number, padding?:symbol, format?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@maxpool3d</code> instance.
</div>
<h3><span class="caption-index-3">5.26.3</span><a name="anchor-5-26-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@maxpool3d</code> instance has the following properties:
</p>
<h2><span class="caption-index-2">5.27</span><a name="anchor-5-27"></a>gear@relu Class</h2>
<h3><span class="caption-index-3">5.27.1</span><a name="anchor-5-27-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.27.2</span><a name="anchor-5-27-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@relu() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@relu</code> instance.
</div>
<h2><span class="caption-index-2">5.28</span><a name="anchor-5-28"></a>gear@sigmoid Class</h2>
<h3><span class="caption-index-3">5.28.1</span><a name="anchor-5-28-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.28.2</span><a name="anchor-5-28-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@sigmoid() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@sigmoid</code> instance.
</div>
<h2><span class="caption-index-2">5.29</span><a name="anchor-5-29"></a>gear@softmax Class</h2>
<h3><span class="caption-index-3">5.29.1</span><a name="anchor-5-29-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.29.2</span><a name="anchor-5-29-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@softmax(axis?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@softmax</code> instance.
</div>
<h3><span class="caption-index-3">5.29.3</span><a name="anchor-5-29-3"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gear@softmax</code> instance has the following properties:
</p>
<div class="mb-2"><code>gear@softmax#axis</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.30</span><a name="anchor-5-30"></a>gear@tanh Class</h2>
<h3><span class="caption-index-3">5.30.1</span><a name="anchor-5-30-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.30.2</span><a name="anchor-5-30-2"></a>Constructor</h3>
<div class="mb-2"><code>gear@tanh() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">gear@tanh</code> instance.
</div>
<h2><span class="caption-index-2">5.31</span><a name="anchor-5-31"></a>help Class</h2>
<h3><span class="caption-index-3">5.31.1</span><a name="anchor-5-31-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">help</code> class provides measures to access help information associated with a <code class="highlighter-rouge">function</code> instance.
</p>
<p>
You can get a <code class="highlighter-rouge">help</code> instance from a <code class="highlighter-rouge">function</code> instance or a <code class="highlighter-rouge">class</code> by calling <code class="highlighter-rouge">help@function()</code> or <code class="highlighter-rouge">help@class()</code> respectively.
</p>
<h3><span class="caption-index-3">5.31.2</span><a name="anchor-5-31-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">help</code> instance has the following properties:
</p>
<div class="mb-2"><code>help#doc</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
The help text.
</div>
<div class="mb-2"><code>help#format</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A name of the syntax format in which the help text is described such as <code class="highlighter-rouge">'markdown'</code>.
</div>
<div class="mb-2"><code>help#lang</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
A symbol of the natural language in which the help text is written. For example, <code class="highlighter-rouge">`en</code> for English and <code class="highlighter-rouge">`ja</code> for Japanese.
</div>
<div class="mb-2"><code>help#title</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
The title of the help.
</div>
<h3><span class="caption-index-3">5.31.3</span><a name="anchor-5-31-3"></a>Method</h3>
<div class="mb-2"><code>help.text@iterator(lang:symbol):static {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a help text for functions that return an iterator.
</p>
<p>
The argument <code class="highlighter-rouge">lang</code> is a symbol that specifies the language in which the text is written, e.g. <code class="highlighter-rouge">`en</code> for English and <code class="highlighter-rouge">`ja</code> for Japanese.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>help.text@block(lang:symbol, varname:string, typename:string):static {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a help text that for functions that take a block .
</p>
<p>
The argument <code class="highlighter-rouge">lang</code> is a symbol that specifies the language in which the text is written, e.g. <code class="highlighter-rouge">`en</code> for English and <code class="highlighter-rouge">`ja</code> for Japanese.
</p>
<p>
In the text, variable names would be replaced by <code class="highlighter-rouge">varname</code> and type names by <code class="highlighter-rouge">typename</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>help.presenter(format:string):static:void {block}</code></div>
<div class="mb-2 ml-4">
<p>
Registers a presentation procedure with a name specified by the argument <code class="highlighter-rouge">format</code>.
</p>
<p>
The procedure is written in the block that takes block parameters: <code class="highlighter-rouge">|help:help|</code>.
</p>

</div>
<h2><span class="caption-index-2">5.32</span><a name="anchor-5-32"></a>image Class</h2>
<h3><span class="caption-index-3">5.32.1</span><a name="anchor-5-32-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">image</code> class provides following measures to handle graphic image data:
</p>
<ul>
<li>Reads image data from a file.</li>
<li>Writes image data to a file.</li>
<li>Apply some modifications on image data including rotation, resize and color conversion.</li>
</ul>
<p>
Acceptable image data formats can be extended by importing modules. Below is a table to show image formats and name of modules that handle them. The string listed in "imagetype" column shows a name that is used by functions <code class="highlighter-rouge">image()</code>, <code class="highlighter-rouge">image#read()</code> and <code class="highlighter-rouge">image#write()</code> to explicitly specify the image data format in a process of reading and writing files.
</p>
<table class="table">
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
<h3><span class="caption-index-3">5.32.2</span><a name="anchor-5-32-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">image</code> instance has the following properties:
</p>
<div class="mb-2"><code>image#format</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
<p>
Takes one of the following symbols indicating what elements are stored in the memory:
</p>
<ul>
<li><code class="highlighter-rouge">`rgb</code> .. red, green and blue</li>
<li><code class="highlighter-rouge">`rgba</code> .. red, green, blue and alpha</li>
</ul>

</div>
<div class="mb-2"><code>image#height</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Image height.
</div>
<div class="mb-2"><code>image#palette</code> &hellip; <code>palette</code> [read/write]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">palette</code> instance associated with this image. If there's no palette associated, this property returns <code class="highlighter-rouge">nil</code>.
</div>
<div class="mb-2"><code>image#width</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Image width.
</div>
<h3><span class="caption-index-3">5.32.3</span><a name="anchor-5-32-3"></a>Constructor</h3>
<div class="mb-2"><code>image(args+):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an image instance with specified characteristics. There are three forms to call the function as below:
</p>
<ul>
<li><code class="highlighter-rouge">image(format:symbol)</code> .. Creates an image instance of the specified format without buffer allocated.</li>
<li><code class="highlighter-rouge">image(format:symbol, width:number, height:number, color?:color)</code> .. Allocates an image buffer with the specified size and fills it with the color.</li>
<li><code class="highlighter-rouge">image(stream:stream, format?:symbol, imagetype?:string)</code> .. Reads image data from the stream and allocates necessary buffer in which the read data is stored.</li>
</ul>
<p>
The argument <code class="highlighter-rouge">format</code> specifies what elements are stored in the memory and takes one of the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`rgb</code> .. red, green and blue</li>
<li><code class="highlighter-rouge">`rgba</code> .. red, green, blue and alpha</li>
</ul>
<p>
In the third form, the format of the image data is determined by the byte sequence of the stream data and its file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code class="highlighter-rouge">imagetype</code>.
</p>

</div>
<h3><span class="caption-index-3">5.32.4</span><a name="anchor-5-32-4"></a>Method</h3>
<div class="mb-2"><code>image#allocbuff(width:number, height:number, color?:color):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Allocates a specified size of buffer in the <code class="highlighter-rouge">image</code> instance that is supposed to has no buffer allocated.
</p>
<p>
The allocated buffer will be filled with <code class="highlighter-rouge">color</code>. If omitted, it will be filled with zero value.
</p>
<p>
An error occurs in following cases:
</p>
<ul>
<li>It fails to allocate necessary buffer.</li>
<li>The <code class="highlighter-rouge">image</code> instance already has allocated buffer.</li>
</ul>

</div>
<div class="mb-2"><code>image#blur(radius:number, sigma?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a new image that blurs the original image with the given parameters.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#clear():reduce</code></div>
<div class="mb-2 ml-4">
<p>
Fills the buffer in the <code class="highlighter-rouge">image</code> instance with zero value.
</p>
<p>
This has the same effect with calling <code class="highlighter-rouge">image#fill()</code> with <code class="highlighter-rouge">color.zero</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#crop(x:number, y:number, width?:number, height?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a new image instance of the extracted area of the source image.
</p>
<p>
The extracted area is specified by the following arguments:
</p>
<ul>
<li><code class="highlighter-rouge">x</code> .. The left position.</li>
<li><code class="highlighter-rouge">y</code> .. The top position.</li>
<li><code class="highlighter-rouge">width</code> .. The width. If it's omitted or specified with <code class="highlighter-rouge">nil</code>, the whole area on the right of <code class="highlighter-rouge">x</code> will be extracted.</li>
<li><code class="highlighter-rouge">height</code> .. The height. If it's omitted or specified with <code class="highlighter-rouge">nil</code>, the whole area on the bottom of <code class="highlighter-rouge">y</code> will be extracted.</li>
</ul>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#delpalette():reduce</code></div>
<div class="mb-2 ml-4">
<p>
Deletes a <code class="highlighter-rouge">palette</code> instance that belongs to the <code class="highlighter-rouge">image</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#extract(x:number, y:number, width:number, height:number, element:symbol, dst):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Extracts the element values within the specified area of the image, and store them into a list. The argument <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> specifies the left-top position, and <code class="highlighter-rouge">width</code>, and <code class="highlighter-rouge">height</code> does the size of the area.
</p>
<p>
The argument <code class="highlighter-rouge">element</code> takes the following symbol that specifies which element should be extracted:
</p>
<ul>
<li><code class="highlighter-rouge">`r</code> .. red</li>
<li><code class="highlighter-rouge">`g</code> .. green</li>
<li><code class="highlighter-rouge">`b</code> .. blue</li>
<li><code class="highlighter-rouge">`a</code> .. alpha</li>
</ul>
<p>
The argument <code class="highlighter-rouge">dst</code> specifies the variable into which the extracted data is stored, which must be a list that has enough space to store the data.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#fill(color:color):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Fills the whole image with the specified color.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#fillrect(x:number, y:number, width:number, height:number, color:color):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Fills the specified area with the specified color. The argument <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> specifies the left-top position, and <code class="highlighter-rouge">width</code>, and <code class="highlighter-rouge">height</code> does the size of the area.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#flip(orient:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a new <code class="highlighter-rouge">image</code> instance that flips the source image horizontally or vertically. You can specify the following symbol to the <code class="highlighter-rouge">orient</code> argument.
</p>
<ul>
<li><code class="highlighter-rouge">`horz</code> .. flips horizontally.</li>
<li><code class="highlighter-rouge">`vert</code> .. flips vertically.</li>
<li><code class="highlighter-rouge">`both</code> .. flips both horizontally and vertically. This has the same effect with rotating the image 180 degrees.</li>
</ul>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#getpixel(x:number, y:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a color of a pixel data at the specified position.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|c:color|</code>, where <code class="highlighter-rouge">c</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#grayscale() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a new image instance that converts the source image into gray scale.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#mapcolorlevel(map@r:array@uint8, map@g?:array@uint8, map@b?:array@uint8) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a new image that converts color levels according to the given table.
</p>
<p>
Each of the arguments <code class="highlighter-rouge">map@r</code>, <code class="highlighter-rouge">map@g</code> and <code class="highlighter-rouge">map@b</code> is an instance of array@uchar containing 256 numbers that range between 0 and 255 and corresponds to elements red, green and blue respectively. An element value in the source image becomes an index of the list and the indexed value will be stored as a converted element value.
</p>
<p>
If you want to apply a mapping table to all the elements, call the method with a single argument like <code class="highlighter-rouge">image#mapcolorlevel(map)</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#paste(x:number, y:number, src:image, width?:number, height?:number, xoffset:number =&gt; 0, yoffset:number =&gt; 0, a:number =&gt; 255):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Pastes the source image <code class="highlighter-rouge">src</code> onto the target image instance at the specified position.
</p>
<p>
The argument <code class="highlighter-rouge">width</code>, <code class="highlighter-rouge">height</code>, <code class="highlighter-rouge">xoffset</code> and <code class="highlighter-rouge">yoffset</code> specify the source image's area to be pasted. If they're omitted, the whole image will be pasted.
</p>
<p>
The argument <code class="highlighter-rouge">a</code> specifies the alpha value that is put on the target image.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#putpixel(x:number, y:number, color:color):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Puts a color on the specified position.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#size()</code></div>
<div class="mb-2 ml-4">
Returns the image size as a list <code class="highlighter-rouge">[width, height]</code>.
</div>
<div class="mb-2"><code>image#store(x:number, y:number, width:number, height:number, element:symbol, src):reduce</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>image#read(stream:stream:r, imagetype?:string):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Reads image data from a stream.
</p>
<p>
The format of the image data is determined by the byte sequence of the stream data and its file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code class="highlighter-rouge">imagetype</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#reducecolor(palette?:palette) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an image that reduces colors in the original image with a set of colors in the given palette. The specified palette would be associated with the created image.
</p>
<p>
If no argument is specified, the associated palette would be used. In this case, an error occurs if there's no palette associated.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#replacecolor(colorOrg:color, color:color, tolerance?:number):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Replaces pixels that have a color matching <code class="highlighter-rouge">colorOrg</code> with the <code class="highlighter-rouge">color</code>.
</p>
<p>
The argument <code class="highlighter-rouge">tolerance</code> specifies an acceptable distance for the matching. If omitted, only an exact match is acceptable.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#resize(width?:number, height?:number):map:[box,ratio] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Resizes the image to the size specified by <code class="highlighter-rouge">width</code> and <code class="highlighter-rouge">height</code> and returns the result.
</p>
<ul>
<li>When both <code class="highlighter-rouge">width</code> and <code class="highlighter-rouge">height</code> are specified, the image would be resized to the size.</li>
<li>When <code class="highlighter-rouge">width</code> is specified and <code class="highlighter-rouge">height</code> is omitted or <code class="highlighter-rouge">nil</code>, the resized height would be calculated from the width so that they keep the same ratio as the original.</li>
<li>When <code class="highlighter-rouge">width</code> is <code class="highlighter-rouge">nil</code> and <code class="highlighter-rouge">height</code> is specified, the resized width would be calculated from the height so that they keep the same ratio as the original.</li>
</ul>
<p>
The following attributes are acceptable:
</p>
<ul>
<li><code class="highlighter-rouge">:box</code> .. When only <code class="highlighter-rouge">width</code> is specified, the same value is set to <code class="highlighter-rouge">height</code>.</li>
<li><code class="highlighter-rouge">:ratio</code> .. Treats values of <code class="highlighter-rouge">width</code> and <code class="highlighter-rouge">height</code> as magnifying ration instead of pixel size.</li>
</ul>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#rotate(rotate:number, background?:color):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an image that rotates the original image by the specified angle.
</p>
<p>
The argument <code class="highlighter-rouge">angle</code> specifies the rotation angle in degree unit, and positive numbers for counterclockwise direction and negative for clockwise direction.
</p>
<p>
The created instance has a size that exactly fits the rotated image. The argument <code class="highlighter-rouge">background</code> specifies the color of pixels to fill the empty area that appears after rotation. If omitted, the color that has all elements set to zero is used for filling.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#scan(x?:number, y?:number, width?:number, height?:number, scandir?:symbol) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an iterator that scans pixels in the image.
</p>
<p>
The arguments <code class="highlighter-rouge">x</code>, <code class="highlighter-rouge">y</code>, <code class="highlighter-rouge">width</code> and <code class="highlighter-rouge">height</code> specify the image area to scan. The argument <code class="highlighter-rouge">scandir</code> specifies the scan direction and takes one of the following symbol:
</p>
<table class="table">
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
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>image#setalpha(a:number, color?:color, tolerance?:number):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Replaces the alpha element of all the pixels in the image with the value specified by <code class="highlighter-rouge">a</code>.
</p>
<p>
If the argument <code class="highlighter-rouge">color</code> is specified, alpha element of pixels that match with that color would be replaced. The argument <code class="highlighter-rouge">tolerance</code> specifies the distance within which the color is determined as matched.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#thumbnail(width?:number, height?:number):map:[box] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Resizes the image so that it fits within a rectangular area specified by <code class="highlighter-rouge">width</code> and <code class="highlighter-rouge">height</code> and returns the result.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|img:image|</code>, where <code class="highlighter-rouge">img</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>image#write(stream:stream:w, imagetype?:string):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Writes image data to a stream.
</p>
<p>
The format of the image data is determined by the stream's file name.
</p>
<p>
You can also explicitly specify the image data format by the argument <code class="highlighter-rouge">imagetype</code>.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<h2><span class="caption-index-2">5.33</span><a name="anchor-5-33"></a>iterator/list Class</h2>
<h3><span class="caption-index-3">5.33.1</span><a name="anchor-5-33-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">iterator</code> class provides measures to operate an iterator, which iterates values that come from containers and streams.
</p>
<p>
The <code class="highlighter-rouge">list</code> class provides measures to handle a list structure, which stores values on memory that can be accessed by indexer.
</p>
<h3><span class="caption-index-3">5.33.2</span><a name="anchor-5-33-2"></a>Iterator-specific Features</h3>
<h4><span class="caption-index-4">5.33.2.1</span><a name="anchor-5-33-2-1"></a>Function to Create iterator Instance</h4>
<div class="mb-2"><code>iterator(value+) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that combines iterators given in the argument.
</p>
<p>
If an argument is not an iterator, that would be added as an element.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h4><span class="caption-index-4">5.33.2.2</span><a name="anchor-5-33-2-2"></a>Method Specific to iterator Class</h4>
<div class="mb-2"><code>iterator#delay(delay:number) {block?}</code></div>
<div class="mb-2 ml-4">
Creates an iterator that returns each element with an interval time specified by the argument <code class="highlighter-rouge">delay</code> in seconds.
</div>
<div class="mb-2"><code>iterator#finite():reduce</code></div>
<div class="mb-2 ml-4">
<p>
Marks the iterator as a finite one by clearing its infinite flag.
</p>
<p>
This method returns the target instance itself.
</p>

</div>
<div class="mb-2"><code>iterator#infinite():reduce</code></div>
<div class="mb-2 ml-4">
<p>
Marks the iterator as an infinite one by setting its infinite flag.
</p>
<p>
This method returns the target instance itself.
</p>

</div>
<div class="mb-2"><code>iterator#isinfinite()</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the iterator is infinite one.
</p>
<p>
The trait of iterator's infinity is used to avoid an endless process by evaluating an infinite iterator. An attempt to evaluate an infinite iterator such as creation of a list from it would occur an error.
</p>

</div>
<div class="mb-2"><code>iterator#next()</code></div>
<div class="mb-2 ml-4">
Returns a next element of the iterator. This operation updates the iterator's internal status.
</div>
<div class="mb-2"><code>iterator#repeater()</code></div>
<div class="mb-2 ml-4">
<p>
Makes the iterator behave as a "repeater". This would allow the iterator be evaulated when it appears as an element of another "repeater" iterator.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = repeat(3):iter {
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

</div>
<h3><span class="caption-index-3">5.33.3</span><a name="anchor-5-33-3"></a>List-specific Features</h3>
<h4><span class="caption-index-4">5.33.3.1</span><a name="anchor-5-33-3-1"></a>Creating List</h4>
<p>
There are several ways to create a list.
</p>
<pre class="highlight"><code>[3, 1, 4, 1, 5, 9]
@{3, 1, 4, 1, 5, 9}
</code></pre>
<h4><span class="caption-index-4">5.33.3.2</span><a name="anchor-5-33-3-2"></a>Index Access</h4>
<p>
You can read and write element values in a list with an indexer by giving it an index number starting from zero. Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F]

println(x[2]) // prints `C
x[4] = `e     // replaces `E with `e
</code></pre>
<h4><span class="caption-index-4">5.33.3.3</span><a name="anchor-5-33-3-3"></a>Function to Create list Instance</h4>
<div class="mb-2"><code>list(value+)</code></div>
<div class="mb-2 ml-4">
Creates a new list from given values in its argument list. If a given value is a list or an iteartor, elements it contains are added to the created list.
</div>
<div class="mb-2"><code>xlist(value+)</code></div>
<div class="mb-2 ml-4">
Creates a new list from given values except for <code class="highlighter-rouge">nil</code> in its argument list. If a given value is a list or an iteartor, elements it contains are added to the created list.
</div>
<div class="mb-2"><code>set(iter+:iterator):[and,or,xor]</code></div>
<div class="mb-2 ml-4">
<p>
Creates a new list that contains unique values from given iterators in its argument list.
</p>
<p>
In default, all the elements in each iterators are added to the created list. Specifying the following attributes would apply a filtering condition.
</p>
<ul>
<li><code class="highlighter-rouge">:and</code> .. Elements that exist in all the iterators are added.</li>
<li><code class="highlighter-rouge">:or</code> .. All the elements are added. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xor</code> .. Elements that exist in only one iterator are added.</li>
</ul>

</div>
<div class="mb-2"><code>xset(iter+:iterator):[and,or,xor]</code></div>
<div class="mb-2 ml-4">
<p>
Creates a new list that contains unique values except for <code class="highlighter-rouge">nil</code> from given iterators in its argument list.
</p>
<p>
In default, all the elements in each iterators are added to the created list. Specifying the following attributes would apply a filtering condition.
</p>
<ul>
<li><code class="highlighter-rouge">:and</code> .. Elements that exist in all the iterators are added.</li>
<li><code class="highlighter-rouge">:or</code> .. All the elements are added. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xor</code> .. Elements that exist in only one iterator are added.</li>
</ul>

</div>
<h4><span class="caption-index-4">5.33.3.4</span><a name="anchor-5-33-3-4"></a>Method Specific to list Class</h4>
<div class="mb-2"><code>list#add(elem+):reduce</code></div>
<div class="mb-2 ml-4">
Add specified items to the list.
</div>
<div class="mb-2"><code>list#append(elem+):reduce</code></div>
<div class="mb-2 ml-4">
Adds specified items to the list. If the item is a list or an iterator, each element in such an item is added to the list.
</div>
<div class="mb-2"><code>list#clear():reduce</code></div>
<div class="mb-2 ml-4">
Clear the content of the list.
</div>
<div class="mb-2"><code>list#combination(n:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that generates lists that contain elements picked up from the original list in a combination manner.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>list#erase(idx*:number):reduce</code></div>
<div class="mb-2 ml-4">
Erases elements at the specified indices.
</div>
<div class="mb-2"><code>list#first()</code></div>
<div class="mb-2 ml-4">
Returns a first value in the list. An error occurs when the list is empty.
</div>
<div class="mb-2"><code>list#get(index:number):flat:map</code></div>
<div class="mb-2 ml-4">
Returns a value stored at the specified index in the list. An error occurs when the index is out of range.
</div>
<div class="mb-2"><code>list#insert(idx:number, elem+):reduce</code></div>
<div class="mb-2 ml-4">
Insert specified items to the list from the selected index.
</div>
<div class="mb-2"><code>list#isempty()</code></div>
<div class="mb-2 ml-4">
Return true if the list is empty.
</div>
<div class="mb-2"><code>list#last()</code></div>
<div class="mb-2 ml-4">
Returns a last value in the list. An error occurs when the list is empty.
</div>
<div class="mb-2"><code>list#permutation(n?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that generates lists that contain elements picked up from the original list in a permutation manner.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>list#put(index:number, value:nomap):map:reduce</code></div>
<div class="mb-2 ml-4">
Stores a value at the specified index in the list. An error occurs when the index is out of range.
</div>
<div class="mb-2"><code>list#shift():[raise]</code></div>
<div class="mb-2 ml-4">
Shifts the elements of the list. If the content of the list is [1, 2, 3, 4], it becomes [2, 3, 4] after calling this method. In default, no error occurs even when the list is empty. To raise an error for executing this method on an empty list, specify :raise attribute.
</div>
<div class="mb-2"><code>list#shuffle():reduce</code></div>
<div class="mb-2 ml-4">
Shuffle the order of the list content based on random numbers.
</div>
<div class="mb-2"><code>list.zip(values+):static {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator generating lists that bind given argument values. When the value is a list or an iterator, each item in it would be zipped.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h3><span class="caption-index-3">5.33.4</span><a name="anchor-5-33-4"></a>Method Common to Both list and iterator Classes</h3>
<div class="mb-2"><code>iterable#after(criteria) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that picks up elements that appear at positions after the criteria is evaluated to be <code class="highlighter-rouge">true</code>.
</p>
<p>
You can specify a function, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#align(n:number, value?) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns the specified number of elements in the source iterator. If the number is larger than the length of the source iterator, the lacking part is filled with <code class="highlighter-rouge">value</code>. If the argument <code class="highlighter-rouge">value</code> is omitted, <code class="highlighter-rouge">nil</code> is used for the filling.
</p>
<p>
Below is an example to specify a number less than the source length:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F].align(3)
// x generates `A, `B, `C.
</code></pre>
<p>
Below is an example to specify a number that exceeds the source length:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F].align(8)
// x generates `A, `B, `C, `D, `E, `F, nil, nil.
</code></pre>

</div>
<div class="mb-2"><code>iterable#and()</code></div>
<div class="mb-2 ml-4">
Calculates a logical AND result of all the values in the iterable.
</div>
<div class="mb-2"><code>iterable#argmax():[indices,last_index]</code></div>
<div class="mb-2 ml-4">
<p>
Returns a position index where the maximum value is found at first.
</p>
<p>
The following attributes modify the behavior:
</p>
<ul>
<li><code class="highlighter-rouge">:last_index</code> .. returns an index where the maximum value is found at last.</li>
<li><code class="highlighter-rouge">:indices</code> .. returns a list of all indices where the maximum value is found.</li>
</ul>
<p>
Calling of methods <code class="highlighter-rouge">iterable#argmas()</code> and <code class="highlighter-rouge">iteraboe#max()</code> have the same effect when attributes are specified as follows:
</p>
<ul>
<li><code class="highlighter-rouge">iterable.argmax()</code> and <code class="highlighter-rouge">iterable.max():index</code></li>
<li><code class="highlighter-rouge">iterable.argmax():last_index</code> and <code class="highlighter-rouge">iterable.max():last_index</code></li>
<li><code class="highlighter-rouge">iterable.argmax():indices</code> and <code class="highlighter-rouge">iterable.max():indices</code></li>
</ul>

</div>
<div class="mb-2"><code>iterable#argmin():[indices,last_index]</code></div>
<div class="mb-2 ml-4">
<p>
Returns a position index where the minimum value is found at first.
</p>
<p>
The following attributes modify the behavior:
</p>
<ul>
<li><code class="highlighter-rouge">:last_index</code> .. returns an index where the minimum value is found at last.</li>
<li><code class="highlighter-rouge">:indices</code> .. returns a list of all indices where the minimum value is found.</li>
</ul>
<p>
Calling of methods <code class="highlighter-rouge">iterable#argmas()</code> and <code class="highlighter-rouge">iteraboe#max()</code> have the same effect when attributes are specified as follows:
</p>
<ul>
<li><code class="highlighter-rouge">iterable.argmax()</code> and <code class="highlighter-rouge">iterable.max():index</code></li>
<li><code class="highlighter-rouge">iterable.argmax():last_index</code> and <code class="highlighter-rouge">iterable.max():last_index</code></li>
<li><code class="highlighter-rouge">iterable.argmax():indices</code> and <code class="highlighter-rouge">iterable.max():indices</code></li>
</ul>

</div>
<div class="mb-2"><code>iterable#before(criteria) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts elements in the iterable before criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#contains(value)</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the specified value appears in the iterable.
</div>
<div class="mb-2"><code>iterable#count(criteria?)</code></div>
<div class="mb-2 ml-4">
<p>
Returns a number of elements that matches the given criteria which is a single-argument function or a value.
</p>
<p>
When a function is applied, it counts the number of true after evaluating element value with the function. If a value is applied, it counts the number of elements that are equal to the value.
</p>

</div>
<div class="mb-2"><code>iterable#cycle(n?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that iterates elements in the source iterator cyclically.
</p>
<p>
The argument <code class="highlighter-rouge">n</code> specifies the number of elements the created iterator returns. If omitted, it would iterates elements infinitely.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E].cycle()
// x generates `A, `B, `C, `D, `E, `A, `B, `C, `D, `E, `A, `B, ..
</code></pre>

</div>
<div class="mb-2"><code>iterable#each() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that iterates each element in the list.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#filter(criteria?) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterable that filters values in the source iterable by a criteria.
</p>
<p>
A criteria can be an iterable or a function instance.
</p>
<ul>
<li>When the criteria is an iterable, the created iterator would scan the source and the criteria iterable simultaneously and would return a value of the source when the corresponding criteria value is evaluated as <code class="highlighter-rouge">true</code>.</li>
<li>When the criteria is a function instance, the created iterator would give it a value of the source as an argument and would return the value when the function has returned <code class="highlighter-rouge">true</code>.</li>
</ul>
<p>
Below is an example to use an iterable as its criteria:
</p>
<pre class="highlight"><code>x = [3, 1, 4, 1, 5, 9]
y = filter(x &gt; 3)
// (x &gt; 3) makes a list [false, false, true, false, true, true]
// y generates 4, 5, 9
</code></pre>
<p>
Below is an example to use a function as its criteria:
</p>
<pre class="highlight"><code>x = [3, 1, 4, 1, 5, 9]
y = filter(&amp;{$x &gt; 3})
// y generates 4, 5, 9
</code></pre>

</div>
<div class="mb-2"><code>iterable#find(criteria?):[index]</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>iterable#flatten():[bfs,dfs] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that searches items recursively if they are lists or iterators.
</p>
<p>
Specifying an attribute could customize searching order as below:
</p>
<ul>
<li><code class="highlighter-rouge">:dfs</code> .. Searches in depth-first order. This is the default behavior.</li>
<li><code class="highlighter-rouge">:bfs</code> .. Searches in breadth-first order.</li>
</ul>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [[`A, `B, `C], [`D, `E, [`F, `G, `H], `I, `J], `K, `L]

y = x.flattten():dfs
// y generates `A, `B, `C, `D, `E, `F, `G, `H, `I, `J, `K, `L

y = x.flatten():bfs
// y generates `K, `L, `A, `B, `C, `D, `E, `I, `J, `F, `G, `H
</code></pre>

</div>
<div class="mb-2"><code>iterable#fold(n:number, nstep?:number):map:[iteritem,neat] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that packs <code class="highlighter-rouge">n</code> elements of the source iterator into a list and returns it as its element.
</p>
<p>
The argument <code class="highlighter-rouge">nstep</code> specifies the shift amount to the next packing.If omitted, the next packing is shifted by <code class="highlighter-rouge">n</code> elements.
</p>
<p>
Specifying the attribute <code class="highlighter-rouge">:iteritem</code> returns an iterator as its element instead of a list
</p>
<p>
If the last packing doesn't satisfy <code class="highlighter-rouge">n</code> elements, its list would be shorter than <code class="highlighter-rouge">n</code>. When specifying the attribute <code class="highlighter-rouge">:neat</code>, such an immature list would be eliminated.
</p>
<p>
Following is an example to fold elements by 3:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].fold(3)
// x generates [`A, `B, `C], [`D, `E, `F], [`G, `H].
</code></pre>
<p>
Following is an example to fold elements by 3 with a step of 2:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].fold(3, 2)
// x generates [`A, `B, `C], [`C, `D, `E], [`E, `F, `G], [`G, `H].
</code></pre>

</div>
<div class="mb-2"><code>iterable#format(format:string):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that converts element values in the source iterable into strings depending on formatter specifier in <code class="highlighter-rouge">format</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#head(n:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that takes the first <code class="highlighter-rouge">n</code> elements from the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#join(sep?:string):map</code></div>
<div class="mb-2 ml-4">
<p>
Joins all the elements in the iterable as strings while inserting the specified separator <code class="highlighter-rouge">sep</code> and returns the result.
</p>
<p>
If an element is not a <code class="highlighter-rouge">string</code> value, it would be converted to a <code class="highlighter-rouge">string</code> before being joined.
</p>

</div>
<div class="mb-2"><code>iterable#joinb()</code></div>
<div class="mb-2 ml-4">
Joins all the <code class="highlighter-rouge">binary</code> values in the iterable and returns the result.
</div>
<div class="mb-2"><code>iterable#len()</code></div>
<div class="mb-2 ml-4">
Returns the length of the iterable.
</div>
<div class="mb-2"><code>iterable#map(func:function) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that generates element values after applying the specfied function on them. The function must take one argument.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#max():[index,indices,last_index]</code></div>
<div class="mb-2 ml-4">
<p>
Returns the maximum value in the iterable.
</p>
<p>
It would return a position index where the maximum value is found when one of the following attributes is specified:
</p>
<ul>
<li><code class="highlighter-rouge">:index</code> .. an index of the maximum value.</li>
<li><code class="highlighter-rouge">:last_index</code> .. an index where the maximum value is found at last.</li>
<li><code class="highlighter-rouge">:indices</code> .. a list of all indices where the maximum value is found.</li>
</ul>

</div>
<div class="mb-2"><code>iterable#mean()</code></div>
<div class="mb-2 ml-4">
<p>
Calculates an average of elements in the iterable.
</p>
<p>
It can work on an iterable with elements of type that supports addition and division operators. Below is a list of acceptable value types:
</p>
<ul>
<li><code class="highlighter-rouge">number</code></li>
<li><code class="highlighter-rouge">complex</code></li>
<li><code class="highlighter-rouge">rational</code></li>
</ul>

</div>
<div class="mb-2"><code>iterable#min():[index,indices,last_index]</code></div>
<div class="mb-2 ml-4">
<p>
Returns the minimum value in the iterable.
</p>
<p>
It would return a position index where the minimum value is found when one of the following attributes is specified:
</p>
<ul>
<li><code class="highlighter-rouge">:index</code> .. an index of the minimum value.</li>
<li><code class="highlighter-rouge">:last_index</code> .. an index where the minimum value is found at last.</li>
<li><code class="highlighter-rouge">:indices</code> .. a list of all indices where the minimum value is found.</li>
</ul>

</div>
<div class="mb-2"><code>iterable#nilto(replace) {block?}</code></div>
<div class="mb-2 ml-4">
Creates an iterator that converts <code class="highlighter-rouge">nil</code> in the source iterable to the specified value.
</div>
<div class="mb-2"><code>iterable#offset(n:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns skips the first <code class="highlighter-rouge">n</code> elements in the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].offset(3)
// x generates `D, `E, `F, `G, `H
</code></pre>

</div>
<div class="mb-2"><code>iterable#or()</code></div>
<div class="mb-2 ml-4">
Calculates a logical OR result of all the values in the iterable.
</div>
<div class="mb-2"><code>iterable#pack(format:string) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">binary</code> instance that has packed elements in the iterable according to specifiers in the <code class="highlighter-rouge">format</code>.
</p>
<p>
A specifier has a format of "<code class="highlighter-rouge">nX</code>" where <code class="highlighter-rouge">X</code> is a format character that represents a packing format and <code class="highlighter-rouge">n</code> is a number of packing size. The number can be omitted, and it would be treated as <code class="highlighter-rouge">1</code> in that case.
</p>
<p>
Following format characters would take a <code class="highlighter-rouge">number</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code class="highlighter-rouge">b</code> .. A one-byte signed number.</li>
<li><code class="highlighter-rouge">B</code> .. A one-byte unsigned number.</li>
<li><code class="highlighter-rouge">h</code> .. A two-byte signed number.</li>
<li><code class="highlighter-rouge">H</code> .. A two-byte unsigned number.</li>
<li><code class="highlighter-rouge">i</code> .. A four-byte signed number.</li>
<li><code class="highlighter-rouge">I</code> .. A four-byte unsigned number.</li>
<li><code class="highlighter-rouge">l</code> .. A four-byte signed number.</li>
<li><code class="highlighter-rouge">L</code> .. A four-byte unsigned number.</li>
<li><code class="highlighter-rouge">q</code> .. A eight-byte signed number.</li>
<li><code class="highlighter-rouge">Q</code> .. A eight-byte unsigned number.</li>
<li><code class="highlighter-rouge">f</code> .. A float-typed number occupying four bytes.</li>
<li><code class="highlighter-rouge">d</code> .. A double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code class="highlighter-rouge">n</code> means the number of values to be packed.
</p>
<p>
Following format characters would take a <code class="highlighter-rouge">string</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code class="highlighter-rouge">s</code> .. Packs a sequence of UTF-8 codes in the string. The packing size <code class="highlighter-rouge">n</code> means the size of the room in bytes where the character codes are to be packed. Only the sequence within the allocated room would be packed. If the string length is smaller than the room, the lacking part would be filled with zero.</li>
<li><code class="highlighter-rouge">c</code> .. Picks the first byte of the string and packs it as a one-byte unsigned number. The packing size <code class="highlighter-rouge">n</code> means the number of values to be packed.</li>
</ul>
<p>
Following format character would take no value from the argument list.
</p>
<ul>
<li><code class="highlighter-rouge">x</code> .. Fills the binary with zero. The packing size <code class="highlighter-rouge">n</code> means the size of the room in bytes to be filled with zero.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code class="highlighter-rouge">@</code> .. System-dependent order.</li>
<li><code class="highlighter-rouge">=</code> .. System-dependent order.</li>
<li><code class="highlighter-rouge">&lt;</code> .. Little endian</li>
<li><code class="highlighter-rouge">&gt;</code> .. Big endian</li>
<li><code class="highlighter-rouge">!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code class="highlighter-rouge">*</code>" for the number of packing size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code class="highlighter-rouge">{</code>" and "<code class="highlighter-rouge">}</code>" in the format to change coding character set while packing a string with format character "<code class="highlighter-rouge">s</code>" from UTF-8.
</p>

</div>
<div class="mb-2"><code>iterable#pingpong(n?:number):[sticky,sticky@top,sticky@btm] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that iterates elements in the source iterator from top to bottom, and then from bottom to top repeatedly.
</p>
<p>
The argument <code class="highlighter-rouge">n</code> specifies the number of elements the created iterator returns. If omitted, it would iterates elements infinitely.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E].pingpong()
// x generates `A, `B, `C, `D, `E, `D, `C, `B, `A, `B, ..
</code></pre>
<p>
The following attributes specify whether the elements on top and bottom are duplicated:
</p>
<ul>
<li><code class="highlighter-rouge">:sticky</code> .. Duplicate the top and bottom elements.</li>
<li><code class="highlighter-rouge">:sticky@top</code> .. Duplicate the top element.</li>
<li><code class="highlighter-rouge">:sticky@btm</code> .. Duplicate the bottom element.</li>
</ul>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E].pingpong():sticky
// x generates `A, `B, `C, `D, `E, `E, `D, `C, `B, `A, `A, `B, ..
</code></pre>

</div>
<div class="mb-2"><code>iterable#print(stream?:stream:w):void</code></div>
<div class="mb-2 ml-4">
<p>
Prints elements to the specified <code class="highlighter-rouge">stream</code>.
</p>
<p>
If omitted, they are printed to the standard output.
</p>

</div>
<div class="mb-2"><code>iterable#printf(format:string, stream?:stream:w):void</code></div>
<div class="mb-2 ml-4">
Prints items in the iterable by using the format.
</div>
<div class="mb-2"><code>iterable#println(stream?:stream:w):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>iterable#rank(directive?) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterable of rank numbers for elements after sorting them.
</p>
<p>
In default, they are sorted in an ascending order. This means that, if two elements <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> has the relationship of <code class="highlighter-rouge">x &lt; y</code>, <code class="highlighter-rouge">x</code> would be placed before <code class="highlighter-rouge">y</code>. You can change the order by specifying the argument <code class="highlighter-rouge">directive</code> with the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`ascend</code> .. Sorts in an ascending order. This is the default.</li>
<li><code class="highlighter-rouge">`descend</code> .. Sorts in a descending order.</li>
</ul>
<p>
You can also put a function to the argument <code class="highlighter-rouge">directive</code> that takes two arguments <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> and is expected to return numbers below:
</p>
<ul>
<li><code class="highlighter-rouge">x == y</code> .. Zero.</li>
<li><code class="highlighter-rouge">x &lt; y</code> .. A number less than zero.</li>
<li><code class="highlighter-rouge">x &gt; y</code> .. A number greater than zero.</li>
</ul>
<p>
When an attribute :stable is specified, the original order shall be kept for elements that are determined as the same.
</p>

</div>
<div class="mb-2"><code>iterable#reduce(accum) {block}</code></div>
<div class="mb-2 ml-4">
<p>
Evaluates a block with a parameter format <code class="highlighter-rouge">|value, accum|</code> and leaves the result as the next <code class="highlighter-rouge">accum</code> value.
</p>
<p>
It returns the final <code class="highlighter-rouge">accum</code> value as its result.
</p>
<p>
Below is an example to calculate summation of the elements:
</p>
<pre class="highlight"><code>x = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
n = x.reduce(0) {|value, accum| value + accum}
// n is 55
</code></pre>

</div>
<div class="mb-2"><code>iterable#replace(value, replace) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that replaces the <code class="highlighter-rouge">value</code> in the original iterablewith the value of <code class="highlighter-rouge">replace</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#reverse() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that iterates elements in the source iterable from tail to top.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#roundoff(threshold:number =&gt; 1e-10) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that replaces a number with zero if it is less than the specified <code class="highlighter-rouge">threshold</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#runlength() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that counts the number of consecutive same value and generates elements in a form of <code class="highlighter-rouge">[cnt, value]</code> where <code class="highlighter-rouge">cnt</code> indicates how many <code class="highlighter-rouge">value</code> appears in a row.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `A, `B, `C, `C, `C, `D, `D].runlength()
// x generates [2, `A], [1, `B], [3, `C], [2, `D]
</code></pre>

</div>
<div class="mb-2"><code>iterable#since(criteria) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that picks up each element in the iterable since criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#skip(n:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that skips <code class="highlighter-rouge">n</code> elements before picking up next element.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, `B, `C, `D, `E, `F, `G, `H].skip(2)
// x generates `A, `D, `G
</code></pre>

</div>
<div class="mb-2"><code>iterable#skipnil() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that skips <code class="highlighter-rouge">nil</code> in the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
Below is an example:
</p>
<pre class="highlight"><code>x = [`A, nil, `C, nil, nil, `F, nil, `H].skipnil()
// x generates `A, `C, `F, `H
</code></pre>

</div>
<div class="mb-2"><code>iterable#sort(directive?, keys[]?):[stable] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator of elements after sorting them.
</p>
<p>
In default, they are sorted in an ascending order. This means that, if two elements <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> has the relationship of <code class="highlighter-rouge">x &lt; y</code>, <code class="highlighter-rouge">x</code> would be placed before <code class="highlighter-rouge">y</code>. You can change the order by specifying the argument <code class="highlighter-rouge">directive</code> with the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`ascend</code> .. Sorts in an ascending order. This is the default.</li>
<li><code class="highlighter-rouge">`descend</code> .. Sorts in a descending order.</li>
</ul>
<p>
You can also put a function to the argument <code class="highlighter-rouge">directive</code> that takes two arguments <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> and is expected to return numbers below:
</p>
<ul>
<li><code class="highlighter-rouge">x == y</code> .. Zero.</li>
<li><code class="highlighter-rouge">x &lt; y</code> .. A number less than zero.</li>
<li><code class="highlighter-rouge">x &gt; y</code> .. A number greater than zero.</li>
</ul>
<p>
When an attribute :stable is specified, the original order shall be kept for elements that are determined as the same. If the argument <code class="highlighter-rouge">keys</code> is specified, it would be used as a key instead of element values.
</p>

</div>
<div class="mb-2"><code>iterable#std():[p]</code></div>
<div class="mb-2 ml-4">
Calculates a standard deviation of elements in the iterable.
</div>
<div class="mb-2"><code>iterable#sum()</code></div>
<div class="mb-2 ml-4">
<p>
Calculates a summation of elements in the iterable.
</p>
<p>
It can work on an iterable with elements of a value type that supports addition operator. Below is a list of acceptable value types:
</p>
<ul>
<li><code class="highlighter-rouge">number</code></li>
<li><code class="highlighter-rouge">complex</code></li>
<li><code class="highlighter-rouge">string</code></li>
<li><code class="highlighter-rouge">rational</code></li>
<li><code class="highlighter-rouge">timedelta</code></li>
</ul>

</div>
<div class="mb-2"><code>iterable#tail(n:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that takes the last <code class="highlighter-rouge">n</code> elements from the source iterable.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#until(criteria) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that picks up each element in the list until criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>iterable#var():[p]</code></div>
<div class="mb-2 ml-4">
Calculates a variance of elements in the iterable.
</div>
<div class="mb-2"><code>iterable#while (criteria) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that picks up each element in the list while criteria is evaluated as true. You can specify a function object, a list or an iterator as the criteria.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h2><span class="caption-index-2">5.34</span><a name="anchor-5-34"></a>memory Class</h2>
<h3><span class="caption-index-3">5.34.1</span><a name="anchor-5-34-1"></a>Overview</h3>
<p>
An instance of the <code class="highlighter-rouge">memory</code> class represents a memory that is stored in <code class="highlighter-rouge">array</code> instances.
</p>
<h3><span class="caption-index-3">5.34.2</span><a name="anchor-5-34-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">memory</code> instance has the following properties:
</p>
<div class="mb-2"><code>memory#p</code> &hellip; <code>pointer</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns a <code>pointer</code> instance that accesses the memory. This result is equivalent to that of calling the method <code class="highlighter-rouge">memory#pointer()</code>.
</div>
<div class="mb-2"><code>memory#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the memory size in bytes.
</div>
<h3><span class="caption-index-3">5.34.3</span><a name="anchor-5-34-3"></a>Constructor</h3>
<div class="mb-2"><code>memory(bytes:number):map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<h3><span class="caption-index-3">5.34.4</span><a name="anchor-5-34-4"></a>Method</h3>
<div class="mb-2"><code>memory#array@int8():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@int8</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@uint8():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@uint8</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@int16():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@int16</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@uint16():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@uint16</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@int32():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@int32</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@uint32():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@uint32</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@int64():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@int64</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@uint64():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@uint64</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@float():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@float</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#array@double():map {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">array@double</code> instance that accesses the content of the target <code class="highlighter-rouge">memory</code> instance.
</div>
<div class="mb-2"><code>memory#dump(stream?:stream:w):void:[upper]</code></div>
<div class="mb-2 ml-4">
<p>
Prints a hexadecimal dump from the content of the <code class="highlighter-rouge">memory</code> to the standard output. If the argument <code class="highlighter-rouge">stream</code> is specified, the result would be output to the stream.
</p>
<p>
In default, hexadecimal digit are printed with lower-case characters. Specifying an attribute <code class="highlighter-rouge">:upper</code> would output them with upper-case characters instead.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; b'A quick brown fox jumps over the lazy dog.'.dump():upper
41 20 71 75 69 63 6B 20 62 72 6F 77 6E 20 66 6F  A quick brown fo
78 20 6A 75 6D 70 73 20 6F 76 65 72 20 74 68 65  x jumps over the
20 6C 61 7A 79 20 64 6F 67 2E                     lazy dog.
</code></pre>

</div>
<div class="mb-2"><code>memory#pointer(offset?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a <code class="highlighter-rouge">pointer</code> instance that has an initial offset specified by the argument <code class="highlighter-rouge">offset</code>. If the argument is omitted, it would return a <code class="highlighter-rouge">pointer</code> instance that points to the top of the memory.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|p:pointer|</code>, where <code class="highlighter-rouge">p</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h2><span class="caption-index-2">5.35</span><a name="anchor-5-35"></a>nil Class</h2>
<h3><span class="caption-index-3">5.35.1</span><a name="anchor-5-35-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">nil</code> class is the class of <code class="highlighter-rouge">nil</code> value that is usually used as an invalid value. In a logical operation, the <code class="highlighter-rouge">nil</code> value is recognized as <code class="highlighter-rouge">false</code>. 
</p>
<h2><span class="caption-index-2">5.36</span><a name="anchor-5-36"></a>number Class</h2>
<h3><span class="caption-index-3">5.36.1</span><a name="anchor-5-36-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">number</code> class is a type of number values. A number literal would create a <code class="highlighter-rouge">number</code> instance.
</p>
<h3><span class="caption-index-3">5.36.2</span><a name="anchor-5-36-2"></a>Method</h3>
<div class="mb-2"><code>number.roundoff(threshold:number =&gt; 1e-10)</code></div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">5.37</span><a name="anchor-5-37"></a>operator Class</h2>
<h3><span class="caption-index-3">5.37.1</span><a name="anchor-5-37-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">operator</code> class provides measures to assign operators with a user-defined procedure.
</p>
<h3><span class="caption-index-3">5.37.2</span><a name="anchor-5-37-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">operator</code> instance has the following properties:
</p>
<div class="mb-2"><code>operator#symbol</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">symbol</code> instance that represents the operator's type.
</div>
<h3><span class="caption-index-3">5.37.3</span><a name="anchor-5-37-3"></a>Constructor</h3>
<div class="mb-2"><code>operator(symbol:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">operator</code> instance that is associated with the specified symbol.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|op:operator|</code>, where <code class="highlighter-rouge">op</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Below is an example to create an <code class="highlighter-rouge">operator</code> instance that is associated with the plus symbol.
</p>
<pre class="highlight"><code>op = operator(`+)
</code></pre>

</div>
<h3><span class="caption-index-3">5.37.4</span><a name="anchor-5-37-4"></a>Method</h3>
<div class="mb-2"><code>operator#assign(type_l:expr, type_r?:expr):map:void {block}</code></div>
<div class="mb-2 ml-4">
<p>
Associates the <code class="highlighter-rouge">operator</code> instance with a procedure described in <code class="highlighter-rouge">block</code> that takes values as a block parameter and returns its operation result.
</p>
<p>
Some <code class="highlighter-rouge">operator</code> instances have two forms of expression: unary and binary. This method assignes the procedure to one of them according to how it takes its arguments as below:
</p>
<ul>
<li><code class="highlighter-rouge">operator#assign(type:expr)</code> .. Assigns procedure to the unary form.</li>
<li><code class="highlighter-rouge">operator#assign(type_l:expr, type_r:expr)</code> .. Assignes procedure to the binary form.</li>
</ul>
<p>
They take different format of block parameters as below:
</p>
<ul>
<li><code class="highlighter-rouge">|value|</code> .. For unary form.</li>
<li><code class="highlighter-rouge">|value_l, value_r|</code> .. For binary form.</li>
</ul>
<p>
Below is an example to assign a procedure to a unary form of operator <code class="highlighter-rouge">-</code>.
</p>
<pre class="highlight"><code>operator(`-).assign(`string) = {|value|
    // any job
}
</code></pre>
<p>
Below is an example to assign a procedure to a binary form of operator <code class="highlighter-rouge">-</code>.
</p>
<pre class="highlight"><code>operator(`-).assign(`string, `number) = {|value_l, value_r|
    // any job
}
</code></pre>

</div>
<div class="mb-2"><code>operator#entries(type?:symbol)</code></div>
<div class="mb-2 ml-4">
<p>
Returns a list that contains type expressions that the operator can accept as its arguments.
</p>
<p>
The argument <code class="highlighter-rouge">type</code> takes a symbol <code class="highlighter-rouge">`binary</code> or <code class="highlighter-rouge">`unary</code>.
</p>
<ul>
<li>If it's omitted or specified with <code class="highlighter-rouge">`binary</code>, the method would return a list of pairs of type expressions for its left element and right one.</li>
<li>If it's specified with <code class="highlighter-rouge">`unary</code>, the method would return a list of type expressions for its single element.</li>
</ul>

</div>
<h2><span class="caption-index-2">5.38</span><a name="anchor-5-38"></a>optimizer Class</h2>
<h3><span class="caption-index-3">5.38.1</span><a name="anchor-5-38-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.38.2</span><a name="anchor-5-38-2"></a>Constructor</h3>
<p>
An <code class="highlighter-rouge">optimizer</code> instance is constructed by following functions:
</p>
<div class="mb-2"><code>optimizer@adagrad(learning_rate:number, epsilon?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">optimizer</code> instance that uses AdaGrad approach for optimization.
</p>
<p>
The argument <code class="highlighter-rouge">learning_rate</code> indicates the learning rate per one training session.
</p>
<p>
The argumnent <code class="highlighter-rouge">epsilon</code> is a value that is added to the denominator in a divination to avoid zero-divided error. The default is <code class="highlighter-rouge">1e-7</code>.
</p>

</div>
<div class="mb-2"><code>optimizer@adam():map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>optimizer@gradient_descent(learning_rate:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">optimizer</code> instance that uses gradient descent approach for optimization.
</p>
<p>
The argument <code class="highlighter-rouge">learning_rate</code> indicates the learning rate per one training session.
</p>

</div>
<div class="mb-2"><code>optimizer@momentum(learning_rate:number, momentum?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an <code class="highlighter-rouge">optimizer</code> instance that uses AdaGrad approach for optimization.
</p>
<p>
The argument <code class="highlighter-rouge">learning_rate</code> indicates the learning rate per one training session.
</p>
<p>
The argumnent <code class="highlighter-rouge">momentum</code> is a momentum parameter and has a default value of <code class="highlighter-rouge">0.9</code>.
</p>

</div>
<div class="mb-2"><code>optimizer@nesterov():map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>optimizer@none():map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>optimizer@rmsprop():map {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<h3><span class="caption-index-3">5.38.3</span><a name="anchor-5-38-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">optimizer</code> class has following methods:
</p>
<div class="mb-2"><code>optimizer#reset():void</code></div>
<div class="mb-2 ml-4">
Resets the status of the optimizer, if exists.
</div>
<div class="mb-2"><code>optimizer#update(array:array, array_grad:array):void</code></div>
<div class="mb-2 ml-4">
Updates <code class="highlighter-rouge">array</code>'s value by the optimizer calculation using the gradient information in <code class="highlighter-rouge">array_grad</code>.
</div>
<h2><span class="caption-index-2">5.39</span><a name="anchor-5-39"></a>palette Class</h2>
<h3><span class="caption-index-3">5.39.1</span><a name="anchor-5-39-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">palette</code> instance has a set of <code class="highlighter-rouge">color</code> instance.
</p>
<h3><span class="caption-index-3">5.39.2</span><a name="anchor-5-39-2"></a>Constructor</h3>
<div class="mb-2"><code>palette(type) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">palette</code> instance.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|plt:palette|</code>, where <code class="highlighter-rouge">plt</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
This function can be called in the following two forms:
</p>
<ul>
<li><code class="highlighter-rouge">palette(n:number)</code> .. Creates an instance with the specified number of entries. All the entries are initialized with a color of black.</li>
<li><code class="highlighter-rouge">palette(type:symbol)</code> .. Creates an instance initialized with a pre-defined set of entries associated with the specified symbol.</li>
</ul>
<p>
In the second form, it can take one of the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`basic</code> .. A palette with 16 basic colors that are: <code class="highlighter-rouge">color.black</code>, <code class="highlighter-rouge">color.maroon</code>, <code class="highlighter-rouge">color.green</code>, <code class="highlighter-rouge">color.olive</code>, <code class="highlighter-rouge">color.navy</code>, <code class="highlighter-rouge">color.purple</code>, <code class="highlighter-rouge">color.teal</code>, <code class="highlighter-rouge">color.gray</code>, <code class="highlighter-rouge">color.silver</code>, <code class="highlighter-rouge">color.red</code>, <code class="highlighter-rouge">color.lime</code>, <code class="highlighter-rouge">color.yellow</code>,  <code class="highlighter-rouge">color.blue</code>, <code class="highlighter-rouge">color.fuchsia</code>, <code class="highlighter-rouge">color.aqua</code> and <code class="highlighter-rouge">color.white</code>.</li>
<li><code class="highlighter-rouge">`win256</code> .. A palette with 256 colors defined by Windows.</li>
<li><code class="highlighter-rouge">`websafe</code> .. A palette with 216 colors that assure to be displayed correctly in any Web environments. It actually has 256 entries though the last 40 entries are initialized with black.</li>
</ul>

</div>
<h3><span class="caption-index-3">5.39.3</span><a name="anchor-5-39-3"></a>Method</h3>
<div class="mb-2"><code>palette#each() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that iterates each element in the palette.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>palette#nearest(color:color):map:[index]</code></div>
<div class="mb-2 ml-4">
<p>
Returns a <code class="highlighter-rouge">color</code> instance in the palette that is the nearest with the specified color.
</p>
<p>
If the attribute <code class="highlighter-rouge">:index</code> is specified, it would return an index of the nearst entry instead of its <code class="highlighter-rouge">color</code> instance.
</p>

</div>
<div class="mb-2"><code>palette#shrink():reduce:[align]</code></div>
<div class="mb-2 ml-4">
Shrinks the size of the palette to a number powered by two that is enough to contain unique entries. The ordef of existing entries will be kept intact.
</div>
<div class="mb-2"><code>palette#updateby(image_or_palette):reduce:[align,shrink]</code></div>
<div class="mb-2 ml-4">
<p>
Updates palette entries according to color data in an image or a palette.
</p>
<p>
The order of existing entries will be kept intact. If attribute shrink is specified, the whole size will be shrinked to a number powered by two that is enough to contain unique entries.
</p>

</div>
<h2><span class="caption-index-2">5.40</span><a name="anchor-5-40"></a>pointer Class</h2>
<h3><span class="caption-index-3">5.40.1</span><a name="anchor-5-40-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">pointer</code> class provides measures to read and write content in a <code class="highlighter-rouge">binary</code> and <code class="highlighter-rouge">memory</code> instance.
</p>
<h3><span class="caption-index-3">5.40.2</span><a name="anchor-5-40-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">pointer</code> instance has following properties:
</p>
<div class="mb-2"><code>pointer#offset</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
The current offset.
</div>
<div class="mb-2"><code>pointer#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the size of data accessible from the current offset.
</div>
<div class="mb-2"><code>pointer#size@all</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the entire size of the target binary or memory. This equals to <code class="highlighter-rouge">p.offset + p.size</code> where <code class="highlighter-rouge">p</code> is a <code class="highlighter-rouge">pointer</code> instance.
</div>
<div class="mb-2"><code>pointer#target</code> &hellip; <code>any</code> [read-only]</div>
<div class="mb-2 ml-4">
An instance that is associated with the pointer. Currently, this can be an instance of <code class="highlighter-rouge">binary</code> or <code class="highlighter-rouge">memory</code>.
</div>
<h3><span class="caption-index-3">5.40.3</span><a name="anchor-5-40-3"></a>Constructor</h3>
<p>
A <code class="highlighter-rouge">pointer</code> instance is constructed by the following function:
</p>
<div class="mb-2"><code>pointer(org:pointer):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">pointer</code> instance that is cloned from the given instance <code class="highlighter-rouge">org</code>. You can use this to cast a <code class="highlighter-rouge">binary</code> and <code class="highlighter-rouge">memory</code> instance to the <code class="highlighter-rouge">pointer</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|ptr:pointer|</code>, where <code class="highlighter-rouge">ptr</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.40.4</span><a name="anchor-5-40-4"></a>Method</h3>
<p>
The <code class="highlighter-rouge">pointer</code> class has following methods:
</p>
<div class="mb-2"><code>pointer#copyfrom(src:pointer, bytes?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Copies data from <code class="highlighter-rouge">src</code> to the target pointer.
</p>
<p>
If the argument <code class="highlighter-rouge">bytes</code> is specified, it would limit the size of data to be copied. Otherwise, all the data pointerd by <code class="highlighter-rouge">src</code> is to be copied.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#copyto(dst:pointer, bytes?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Copies data from the target pointer to <code class="highlighter-rouge">dst</code>.
</p>
<p>
If the argument <code class="highlighter-rouge">bytes</code> is specified, it would limit the size of data to be copied. Otherwise, all the data pointerd by the target instance is to be copied.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#decode(codec:codec, bytes?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Decodes the content of the <code class="highlighter-rouge">pointer</code> as a sequence of string characters using <code class="highlighter-rouge">codec</code> and returns the result in <code class="highlighter-rouge">string</code>.
</p>
<p>
If the argument <code class="highlighter-rouge">bytes</code> is specified, it would limit the size of data to be decoded. Otherwise, all the data pointerd by the target instance is to be decoded.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#dump(stream?:stream:w, bytes?:number):reduce:[upper]</code></div>
<div class="mb-2 ml-4">
<p>
Prints a hexadecimal dump from the content of the <code class="highlighter-rouge">pointer</code> to the standard output. If the argument <code class="highlighter-rouge">stream</code> is specified, the result would be output to the stream.
</p>
<p>
If the argument <code class="highlighter-rouge">bytes</code> is specified, it would limit the size of data to be dumped. Otherwise, all the data pointerd by the target instance is to be dumped.
</p>
<p>
In default, hexadecimal digit are printed with lower-case characters. Specifying an attribute <code class="highlighter-rouge">:upper</code> would output them with upper-case characters instead.
</p>
<p>
Example:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; b'A quick brown fox jumps over the lazy dog.'.p.dump():upper
41 20 71 75 69 63 6B 20 62 72 6F 77 6E 20 66 6F  A quick brown fo
78 20 6A 75 6D 70 73 20 6F 76 65 72 20 74 68 65  x jumps over the
20 6C 61 7A 79 20 64 6F 67 2E                     lazy dog.
</code></pre>

</div>
<div class="mb-2"><code>pointer#encodeuri(bytes?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a string in which non-URIC characters are converted to percent-encoded string.
</p>
<p>
For example, <code class="highlighter-rouge">b'"Hello"'.p.encodeuri()</code> would return <code class="highlighter-rouge">'%22Hello%22'</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#each@int8():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of int8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@uint8():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of uint8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@int16():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of int16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@uint16():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of uint16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@int32():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of int32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@uint32():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of uint32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@int64():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of int64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@uint64():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of uint64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@float():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of float from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#each@double():[be] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that extracts numbers in size of double from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>pointer#forward(distance:number):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Put the pointer offset forward by <code class="highlighter-rouge">distance</code>. If a negative number is specified for the argument, the offset would be put backward.
</p>
<p>
An error would occur when the pointer's offset becomes a negative value while it would be no error when the offset exceeds the target maximum range.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#get@int8():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of int8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@uint8():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of uint8 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@int16():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of int16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@uint16():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of uint16 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@int32():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of int32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@uint32():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of uint32 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@int64():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of int64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@uint64():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of uint64 from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@float():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of float from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#get@double():[be,nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an extracted number in size of double from the current pointer position.
</p>
<p>
In default, it assumes the byte seqeuces are ordered in little-endian. You can specify <code class="highlighter-rouge">:be</code> attribute to extract them in big-endian order.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|n:number|</code>, where <code class="highlighter-rouge">n</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#head():reduce</code></div>
<div class="mb-2 ml-4">
<p>
Moves the pointer position to the beginning.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#hex(bytes?:number):[carray,cstr,upper] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Converts the binary data into a hexadecimal string.
</p>
<p>
In default, the result string is a sequence of joined hexadecimal values without any space. You can specify the following attribute to change the format:
</p>
<ul>
<li><code class="highlighter-rouge">:cstr</code> .. Format of C string.</li>
<li><code class="highlighter-rouge">:carray</code> .. Format of C array.</li>
</ul>
<p>
Alphabet characters are described in lower characters unless the attribute <code class="highlighter-rouge">:upper</code> is specified.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|str:string|</code>, where <code class="highlighter-rouge">str</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
Example:
</p>
<table class="table">
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

</div>
<div class="mb-2"><code>pointer#pack(format:string, values+):reduce:[stay]</code></div>
<div class="mb-2 ml-4">
<p>
Packs <code class="highlighter-rouge">values</code> in the argument list according to specifiers in the <code class="highlighter-rouge">format</code> into a binary and adds it to where the pointer points. The pointer offset is automatically incremented by the added length unless <code class="highlighter-rouge">:stay</code> attribute is specified.
</p>
<p>
This method returns a reference to the target instance itself.
</p>
<p>
A specifier has a format of "<code class="highlighter-rouge">nX</code>" where <code class="highlighter-rouge">X</code> is a format character that represents a packing format and <code class="highlighter-rouge">n</code> is a number of packing size. The number can be omitted, and it would be treated as <code class="highlighter-rouge">1</code> in that case.
</p>
<p>
Following format characters would take a <code class="highlighter-rouge">number</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code class="highlighter-rouge">b</code> .. One-byte signed number.</li>
<li><code class="highlighter-rouge">B</code> .. One-byte unsigned number.</li>
<li><code class="highlighter-rouge">h</code> .. Two-byte signed number.</li>
<li><code class="highlighter-rouge">H</code> .. Two-byte unsigned number.</li>
<li><code class="highlighter-rouge">i</code> .. Four-byte signed number.</li>
<li><code class="highlighter-rouge">I</code> .. Four-byte unsigned number.</li>
<li><code class="highlighter-rouge">l</code> .. Four-byte signed number.</li>
<li><code class="highlighter-rouge">L</code> .. Four-byte unsigned number.</li>
<li><code class="highlighter-rouge">q</code> .. Eight-byte signed number.</li>
<li><code class="highlighter-rouge">Q</code> .. Eight-byte unsigned number.</li>
<li><code class="highlighter-rouge">f</code> .. Float-typed number occupying four bytes.</li>
<li><code class="highlighter-rouge">d</code> .. Double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code class="highlighter-rouge">n</code> means the number of values to be packed.
</p>
<p>
Following format characters would take a <code class="highlighter-rouge">string</code> value from the argument list and pack them into a binary sequence.
</p>
<ul>
<li><code class="highlighter-rouge">s</code> .. Packs a sequence of UTF-8 codes in the string. The packing size <code class="highlighter-rouge">n</code> means the size of the room in bytes where the character codes are to be packed. Only the sequence within the allocated room would be packed. If the string length is smaller than the room, the lacking part would be filled with zero.</li>
<li><code class="highlighter-rouge">c</code> .. Picks the first byte of the string and packs it as a one-byte unsigned number. The packing size <code class="highlighter-rouge">n</code> means the number of values to be packed.</li>
</ul>
<p>
Following format character would take no value from the argument list.
</p>
<ul>
<li><code class="highlighter-rouge">x</code> .. Fills the binary with zero. The packing size <code class="highlighter-rouge">n</code> means the size of the room in bytes to be filled with zero.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code class="highlighter-rouge">@</code> .. System-dependent order.</li>
<li><code class="highlighter-rouge">=</code> .. System-dependent order.</li>
<li><code class="highlighter-rouge">&lt;</code> .. Little endian</li>
<li><code class="highlighter-rouge">&gt;</code> .. Big endian</li>
<li><code class="highlighter-rouge">!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code class="highlighter-rouge">*</code>" for the number of packing size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code class="highlighter-rouge">{</code>" and "<code class="highlighter-rouge">}</code>" in the format to change coding character set from UTF-8 while packing a string with format character "<code class="highlighter-rouge">s</code>".
</p>

</div>
<div class="mb-2"><code>pointer#put@int8(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of int8.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@uint8(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of uint8.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@int16(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of int16.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@uint16(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of uint16.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@int32(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of int32.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@uint32(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of uint32.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@int64(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of int64.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@uint64(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of uint64.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@float(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of float.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#put@double(n:number):map:reduce:[be,stay]</code></div>
<div class="mb-2 ml-4">
<p>
Stores the specified number to the current pointer position in size of double.
</p>
<p>
In default, it stores the byte sequences in the order of little-endian. You can specify <code class="highlighter-rouge">:be</code> sttribute to store them in big-endian order.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#reader() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">stream</code> instance with which you can read data from the memory pointerd by the pointer. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</div>
<div class="mb-2"><code>pointer#seek(offset:number):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Moves the pointer position to the specified <code class="highlighter-rouge">offset</code>.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#tail():reduce</code></div>
<div class="mb-2 ml-4">
<p>
Moves the pointer position to the end.
</p>
<p>
This method returns a reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>pointer#unpack(format:string, values*:number):[nil,stay] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Extracts values from data sequence pointed by the <code class="highlighter-rouge">pointer</code> instance according to specifiers in the <code class="highlighter-rouge">format</code> and returns a list containing the values.
</p>
<p>
A specifier has a format of "<code class="highlighter-rouge">nX</code>" where <code class="highlighter-rouge">X</code> is a format character that represents a packing format and <code class="highlighter-rouge">n</code> is a number of packing size. The number can be omitted, and it would be treated as <code class="highlighter-rouge">1</code> in that case.
</p>
<p>
Following format characters would extract an integer or float value of specified size from the binary and returns a <code class="highlighter-rouge">number</code> value.
</p>
<ul>
<li><code class="highlighter-rouge">b</code> .. One-byte signed number.</li>
<li><code class="highlighter-rouge">B</code> .. One-byte unsigned number.</li>
<li><code class="highlighter-rouge">h</code> .. Two-byte signed number.</li>
<li><code class="highlighter-rouge">H</code> .. Two-byte unsigned number.</li>
<li><code class="highlighter-rouge">i</code> .. Four-byte signed number.</li>
<li><code class="highlighter-rouge">I</code> .. Four-byte unsigned number.</li>
<li><code class="highlighter-rouge">l</code> .. Four-byte signed number.</li>
<li><code class="highlighter-rouge">L</code> .. Four-byte unsigned number.</li>
<li><code class="highlighter-rouge">q</code> .. Eight-byte signed number.</li>
<li><code class="highlighter-rouge">Q</code> .. Eight-byte unsigned number.</li>
<li><code class="highlighter-rouge">f</code> .. Float-typed number occupying four bytes.</li>
<li><code class="highlighter-rouge">d</code> .. Double-typed number occupying eight bytes.</li>
</ul>
<p>
As for them, the packing size <code class="highlighter-rouge">n</code> means the number of values to be extracted.
</p>
<p>
Following format characters would extract a string sequence from the binary and returns a <code class="highlighter-rouge">string</code> value.
</p>
<ul>
<li><code class="highlighter-rouge">s</code> .. Extracts a sequence of UTF-8 codes and returns <code class="highlighter-rouge">string</code> instance containing it. The unpacking size <code class="highlighter-rouge">n</code> means the size of the room in bytes where the character codes are to be unpacked.</li>
<li><code class="highlighter-rouge">c</code> .. Extracts a one-byte unsigned number and returns a <code class="highlighter-rouge">string</code> instance containing it. The unpacking size <code class="highlighter-rouge">n</code> means the number of values to be extracted.</li>
</ul>
<p>
Following format character would not return any value.
</p>
<ul>
<li><code class="highlighter-rouge">x</code> .. Advances the address by one byte. If the unpacking size <code class="highlighter-rouge">n</code> is specifies, it would advance the address by <code class="highlighter-rouge">n</code> bytes.</li>
</ul>
<p>
The default byte-order for numbers of two-byte, four-byte and eight-byte depends on the system the interpreter is currently running. You can change it by the following specifiers:
</p>
<ul>
<li><code class="highlighter-rouge">@</code> .. System-dependent order.</li>
<li><code class="highlighter-rouge">=</code> .. System-dependent order.</li>
<li><code class="highlighter-rouge">&lt;</code> .. Little endian</li>
<li><code class="highlighter-rouge">&gt;</code> .. Big endian</li>
<li><code class="highlighter-rouge">!</code> .. Big endian</li>
</ul>
<p>
You can specify an asterisk character "<code class="highlighter-rouge">*</code>" for the number of unpacking size that picks that number from the argument list.
</p>
<p>
You can specify encoding name embraced with "<code class="highlighter-rouge">{</code>" and "<code class="highlighter-rouge">}</code>" in the format to change coding character set from UTF-8 while extracting a string with format character "<code class="highlighter-rouge">s</code>".
</p>
<p>
An error occurs if the binary size is smaller than the format reqeusts. If the attribute <code class="highlighter-rouge">:nil</code> is specified, <code class="highlighter-rouge">nil</code> value would be returned for such a case.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|list:list|</code>, where <code class="highlighter-rouge">list</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#unpacks(format:string, values*:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns an iterator that extracts values from data pointed by the <code class="highlighter-rouge">pointer</code> instance according to specifiers in <code class="highlighter-rouge">format</code>.
</p>
<p>
For detailed information about specifiers, see the help of <code class="highlighter-rouge">pointer#unpack()</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|iter:iterator|</code>, where <code class="highlighter-rouge">iter</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>pointer#writer() {block?}</code></div>
<div class="mb-2 ml-4">
Creates a <code class="highlighter-rouge">stream</code> instance with which you can append data to the memory pointed by the pointer. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</div>
<h3><span class="caption-index-3">5.40.5</span><a name="anchor-5-40-5"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">pointer</code> instance in its argument can also take a value of <code class="highlighter-rouge">binary</code> and <code class="highlighter-rouge">memory</code>.
</p>
<p>
With the above casting feature, you can call a function <code class="highlighter-rouge">f(p:pointer)</code> that takes a <code class="highlighter-rouge">pointer</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">b = b'\x01\x23\x45\x67\x89\xab', f(b)</code></li>
<li><code class="highlighter-rouge">m = memory(32), f(m)</code> </li>
</ul>
<h2><span class="caption-index-2">5.41</span><a name="anchor-5-41"></a>propdeclaration Class</h2>
<h3><span class="caption-index-3">5.41.1</span><a name="anchor-5-41-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">propdeclaration</code> class provides information such as the name and the read/write attribute of property that is stored in various objects.
</p>
<p>
You can get an <code class="highlighter-rouge">iterator</code> of <code class="highlighter-rouge">propdeclaration</code> by calling <code class="highlighter-rouge">object#__propdecls__()</code>.
</p>
<h3><span class="caption-index-3">5.41.2</span><a name="anchor-5-41-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">propdeclaration</code> instance has the following properties:
</p>
<div class="mb-2"><code>propdeclaration#dispname</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Display name. If the property is a list, a pair of square brackets are appended.
</div>
<div class="mb-2"><code>propdeclaration#fullname</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
A full name of the property that is prefixed by a name of the class it belongs to.
</div>
<div class="mb-2"><code>propdeclaration#name</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
The property's name.
</div>
<div class="mb-2"><code>propdeclaration#readable</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if it is readable, <code class="highlighter-rouge">false</code> otherwise.
</div>
<div class="mb-2"><code>propdeclaration#symbol</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
The property's name as a <code class="highlighter-rouge">symbol</code> instance.
</div>
<div class="mb-2"><code>propdeclaration#type</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
The value type of the property.
</div>
<div class="mb-2"><code>propdeclaration#writable</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if it is readable, <code class="highlighter-rouge">false</code> otherwise.
</div>
<h3><span class="caption-index-3">5.41.3</span><a name="anchor-5-41-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">propdeclaration</code> class provides the following methods:
</p>
<div class="mb-2"><code>propdeclaration#gethelp(lang?:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Get a <code class="highlighter-rouge">help</code> instance assosicated with the property.
</p>
<p>
The argument <code class="highlighter-rouge">lang</code> specifies the language of the document, such as <code class="highlighter-rouge">en</code> and <code class="highlighter-rouge">ja</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|help:help|</code>, where <code class="highlighter-rouge">help</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h2><span class="caption-index-2">5.42</span><a name="anchor-5-42"></a>rational Class</h2>
<h3><span class="caption-index-3">5.42.1</span><a name="anchor-5-42-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">rational</code> class provides measures to handle rational numbers.
</p>
<p>
You can create a <code class="highlighter-rouge">rational</code> instance with following ways:
</p>
<ul>
<li>Use <code class="highlighter-rouge">rational()</code> function.</li>
<li>Append <code class="highlighter-rouge">r</code> suffix after a number literal.</li>
</ul>
<p>
Below are examples to realize a common fraction two-thirds:
</p>
<pre class="highlight"><code>rational(2, 3)
2r / 3
2 / 3r
</code></pre>
<h3><span class="caption-index-3">5.42.2</span><a name="anchor-5-42-2"></a>Constructor</h3>
<div class="mb-2"><code>rational(numer:number, denom?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a rational value from given numerator <code class="highlighter-rouge">numer</code> and denominator <code class="highlighter-rouge">denom</code>.
</p>
<p>
If the argument <code class="highlighter-rouge">denom</code> is omitted, one is set as its denominator.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|r:rational|</code>, where <code class="highlighter-rouge">r</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.42.3</span><a name="anchor-5-42-3"></a>Method</h3>
<div class="mb-2"><code>rational.reduce()</code></div>
<div class="mb-2 ml-4">
Reduces the rational number by dividing its numerator and denominator by their GCD.
</div>
<h2><span class="caption-index-2">5.43</span><a name="anchor-5-43"></a>semaphore Class</h2>
<h3><span class="caption-index-3">5.43.1</span><a name="anchor-5-43-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.43.2</span><a name="anchor-5-43-2"></a>Constructor</h3>
<div class="mb-2"><code>semaphore()</code></div>
<div class="mb-2 ml-4">

</div>
<h3><span class="caption-index-3">5.43.3</span><a name="anchor-5-43-3"></a>Method</h3>
<div class="mb-2"><code>semaphore#release()</code></div>
<div class="mb-2 ml-4">
Releases the owership of the semaphore that is grabbed by semaphore#wait().
</div>
<div class="mb-2"><code>semaphore#session() {block}</code></div>
<div class="mb-2 ml-4">
Forms a critical session by grabbing the semaphore's ownership, executing the block and releasing that ownership. It internally proccesses the same job as semaphore#wait() and semaphore#release() before and after the block execution
</div>
<div class="mb-2"><code>semaphore#wait()</code></div>
<div class="mb-2 ml-4">
Watis for the semaphore being released by other threads, and ghen grabs that ownership.
</div>
<h2><span class="caption-index-2">5.44</span><a name="anchor-5-44"></a>stream Class</h2>
<h3><span class="caption-index-3">5.44.1</span><a name="anchor-5-44-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">stream</code> class provides methods to read and write data through a stream, an abstract structure to handle a byte sequence. It also provides information of the stream such as the pathname and the creation date and time.
</p>
<p>
You can specify a proper <code class="highlighter-rouge">codec</code> when creating the <code class="highlighter-rouge">stream</code> instance, which is used to decode/encode character codes that appear in the stream. Features of <code class="highlighter-rouge">codec</code> would affect on functions and methods that handle text data like follows:
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
<li>operator <code class="highlighter-rouge">&lt;&lt;</code></li>
<li>stream#print()</li>
<li>stream#printf()</li>
<li>stream#println()</li>
</ul>
</li>
</ul>
<h3><span class="caption-index-3">5.44.2</span><a name="anchor-5-44-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">stream</code> instance has the following properties:
</p>
<div class="mb-2"><code>stream#codec</code> &hellip; <code>codec</code> [read-only]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">codec</code> instance associated with the stream.
</div>
<div class="mb-2"><code>stream#identifier</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Identifier of the stream.
</div>
<div class="mb-2"><code>stream#name</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Name of the stream.
</div>
<div class="mb-2"><code>stream#readable</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
Indicates whether the stream is readable.
</div>
<div class="mb-2"><code>stream#stat</code> &hellip; <code>any</code> [read-only]</div>
<div class="mb-2 ml-4">
Status of the stream.
</div>
<div class="mb-2"><code>stream#writable</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
Indicates whether the stream is writable.
</div>
<h3><span class="caption-index-3">5.44.3</span><a name="anchor-5-44-3"></a>Operator</h3>
<p>
You can use the operator "<code class="highlighter-rouge">&lt;&lt;</code>" to output a content of a value to a <code class="highlighter-rouge">stream</code>. It comes like "<code class="highlighter-rouge">stream &lt;&lt; obj</code>" where <code class="highlighter-rouge">obj</code> is converted to a string before output to the stream.
</p>
<pre class="highlight"><code>sys.stdout &lt;&lt; 'Hello World.'
</code></pre>
<p>
Since the operator returns the <code class="highlighter-rouge">stream</code> instance specified on the left as its result, you can chain multiple operations as below:
</p>
<pre class="highlight"><code>sys.stdout &lt;&lt; 'First' &lt;&lt; 'Second'
</code></pre>
<h3><span class="caption-index-3">5.44.4</span><a name="anchor-5-44-4"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">stream</code> instance in its argument can also take a value of <code class="highlighter-rouge">string</code> and <code class="highlighter-rouge">binary</code> as below:
</p>
<ul>
<li><code class="highlighter-rouge">string</code> .. Recognized the <code class="highlighter-rouge">string</code> as a path name from which <code class="highlighter-rouge">stream</code> instance is created.</li>
<li><code class="highlighter-rouge">binary</code> .. Creates a <code class="highlighter-rouge">stream</code> instance that reads or modifies the content of the specified <code class="highlighter-rouge">binary</code> data. If the <code class="highlighter-rouge">binary</code> data is a constant one, which might be created from a binary literal such as <code class="highlighter-rouge">b'\x00\x12\x34\x56'</code>, the stream is created with read-only attribute.</li>
</ul>
<p>
Using the above casting feature, you can call a function <code class="highlighter-rouge">f(stream:stream)</code> that takes a <code class="highlighter-rouge">stream</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">f(stream('foo.txt'))</code> .. The most explicit way.</li>
<li><code class="highlighter-rouge">f('foo.txt')</code> .. Implicit casting from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">stream</code>.</li>
<li><code class="highlighter-rouge">f(b'\x00\x12\x34\x56')</code> .. Implicit casting from <code class="highlighter-rouge">binary</code> to <code class="highlighter-rouge">stream</code> that reads the content.</li>
</ul>
<h3><span class="caption-index-3">5.44.5</span><a name="anchor-5-44-5"></a>Constructor</h3>
<div class="mb-2"><code>stream(pathname:string, mode?:string, codec?:codec):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">stream</code> instance from the specified <code class="highlighter-rouge">pathname</code>.
</p>
<p>
The argument <code class="highlighter-rouge">mode</code> takes one of the strings that specifies what access should be allowed with the stream. If omitted, the stream would be opened with read mode.
</p>
<ul>
<li><code class="highlighter-rouge">'r'</code> .. read</li>
<li><code class="highlighter-rouge">'w'</code> .. write</li>
<li><code class="highlighter-rouge">'a'</code> .. append</li>
</ul>
<p>
The argument <code class="highlighter-rouge">codec</code> specifies a name of the character codec that converts between the stream's character code and UTF-8, which is a code used in the iterpreter's internal process.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<p>
You can also call <code class="highlighter-rouge">open()</code> function that is just an alias of <code class="highlighter-rouge">stream()</code> to create a <code class="highlighter-rouge">stream</code> instance.
</p>
<h3><span class="caption-index-3">5.44.6</span><a name="anchor-5-44-6"></a>Utility Function</h3>
<div class="mb-2"><code>readlines(stream?:stream:r):[chop] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that reads text from the specified stream line by line.
</p>
<p>
If attribute <code class="highlighter-rouge">:chop</code> is specified, it eliminates an end-of-line character that appears at the end of each line.
</p>
<p>
This function decodes character codes in the stream using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h3><span class="caption-index-3">5.44.7</span><a name="anchor-5-44-7"></a>Method</h3>
<div class="mb-2"><code>stream#addcr(flag?:boolean):reduce</code></div>
<div class="mb-2 ml-4">
<p>
The codec's encoder in the stream has a feature to add a CR code (<code class="highlighter-rouge">0x0d</code>) before a LF code (<code class="highlighter-rouge">0x0a</code>) so that the lines are joined with CR-LF codes in the encoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">false</code>.</li>
</ul>

</div>
<div class="mb-2"><code>stream#close():void</code></div>
<div class="mb-2 ml-4">
Closes the stream.
</div>
<div class="mb-2"><code>stream#compare(stream:stream:r):map</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if there's no difference between the binary sequences of the target stream instance and that of <code class="highlighter-rouge">stream</code> in the argument.
</div>
<div class="mb-2"><code>stream.copy(src:stream:r, dst:stream:w, bytesunit:number =&gt; 65536):static:map:void:[finalize] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Copies the content in <code class="highlighter-rouge">src</code> to the stream <code class="highlighter-rouge">dst</code>.
</p>
<p>
The copy process is done by the following steps:
</p>
<ol>
<li>Reads data from stream <code class="highlighter-rouge">src</code> into a buffer with the size specified by <code class="highlighter-rouge">bytesunit</code>.</li>
<li>(1) If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|buff:binary|</code> where <code class="highlighter-rouge">buff</code> contains the read data. When the block's result is a <code class="highlighter-rouge">binary</code> instance, the content would be written to the stream <code class="highlighter-rouge">dst</code>. Otherwise, the read data would be written to stream <code class="highlighter-rouge">dst</code>. (2) If <code class="highlighter-rouge">block</code> is not specified, the read data would be written to stream <code class="highlighter-rouge">dst</code>.</li>
<li>Continues from step 1 to 2 until data from <code class="highlighter-rouge">src</code> runs out.</li>
</ol>
<p>
If the attribute <code class="highlighter-rouge">:finalize</code> is specified, some finalizing process such as copying the time stamp and attributes will be applied at the end.
</p>
<p>
This works the same way as <code class="highlighter-rouge">stream#copyfrom()</code> and <code class="highlighter-rouge">stream#copyto()</code>.
</p>

</div>
<div class="mb-2"><code>stream#copyfrom(src:stream:r, bytesunit:number =&gt; 65536):map:reduce:[finalize] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Copies the content in <code class="highlighter-rouge">src</code> to target stream instance.
</p>
<p>
The copy process is done by the following steps:
</p>
<ol>
<li>Reads data from stream <code class="highlighter-rouge">src</code> into a buffer with the size specified by <code class="highlighter-rouge">bytesunit</code>.</li>
<li>(1) If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|buff:binary|</code> where <code class="highlighter-rouge">buff</code> contains the read data. When the block's result is a <code class="highlighter-rouge">binary</code> instance, the content would be written to the target stream. Otherwise, the read data would be written to the target stream. (2) If <code class="highlighter-rouge">block</code> is not specified, the read data would be written to the target stream.</li>
<li>Continues from step 1 to 2 until data from <code class="highlighter-rouge">src</code> runs out.</li>
</ol>
<p>
If the attribute <code class="highlighter-rouge">:finalize</code> is specified, some finalizing process such as copying the time stamp and attributes will be applied at the end.
</p>
<p>
This works the same way as <code class="highlighter-rouge">stream.copy()</code> and <code class="highlighter-rouge">stream#copyto()</code>.
</p>

</div>
<div class="mb-2"><code>stream#copyto(dst:stream:w, bytesunit:number =&gt; 65536):map:reduce:[finalize] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Copies the content in the target stream to the stream <code class="highlighter-rouge">dst</code>.
</p>
<p>
The copy process is done by the following steps:
</p>
<ol>
<li>Reads data from the target stream into a buffer with the size specified by <code class="highlighter-rouge">bytesunit</code>.</li>
<li>(1) If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|buff:binary|</code> where <code class="highlighter-rouge">buff</code> contains the read data. When the block's result is a <code class="highlighter-rouge">binary</code> instance, the content would be written to the stream <code class="highlighter-rouge">dst</code>. Otherwise, the read data would be written to stream <code class="highlighter-rouge">dst</code>. (2) If <code class="highlighter-rouge">block</code> is not specified, the read data would be written to stream <code class="highlighter-rouge">dst</code>.</li>
<li>Continues from step 1 to 2 until data from the target stream runs out.</li>
</ol>
<p>
If the attribute <code class="highlighter-rouge">:finalize</code> is specified, some finalizing process such as copying the time stamp and attributes will be applied at the end.
</p>
<p>
This works the same way as <code class="highlighter-rouge">stream.copy()</code> and <code class="highlighter-rouge">stream#copyfrom()</code>.
</p>

</div>
<div class="mb-2"><code>stream#delcr(flag?:boolean):reduce</code></div>
<div class="mb-2 ml-4">
<p>
The codec's decoder in the stream has a feature to delete a CR code (<code class="highlighter-rouge">0x0d</code>) before a LF code (<code class="highlighter-rouge">0x0a</code>) so that the lines are joined with LF code in the decoded result. This method enables or disables the feature.
</p>
<ul>
<li>To enable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">true</code> or without any argument.</li>
<li>To disable it, call the method with the argument <code class="highlighter-rouge">flag</code> set to <code class="highlighter-rouge">false</code>.</li>
</ul>

</div>
<div class="mb-2"><code>stream#deserialize()</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>stream#flush():void</code></div>
<div class="mb-2 ml-4">
Flushes cached data to the stream.
</div>
<div class="mb-2"><code>stream#peek(bytes?:number)</code></div>
<div class="mb-2 ml-4">
Reads specified length of data from the stream and returns a <code class="highlighter-rouge">binary</code> instance that contains it. This doesn't move the stream's current file position.
</div>
<div class="mb-2"><code>stream#print(values*):map:void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out <code class="highlighter-rouge">values</code> to the <code class="highlighter-rouge">stream</code> instance after converting them to strings.
</p>
<p>
This function encodes character codes in the string using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>

</div>
<div class="mb-2"><code>stream#printf(format:string, values*):map:void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out <code class="highlighter-rouge">values</code> to the <code class="highlighter-rouge">stream</code> instance according to formatter specifiers in <code class="highlighter-rouge">format</code>.
</p>
<p>
Refer to the help of <code class="highlighter-rouge">printf()</code> function to see information about formatter specifiers.
</p>
<p>
This function encodes character codes in the string using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>

</div>
<div class="mb-2"><code>stream#println(values*):map:void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out <code class="highlighter-rouge">values</code> and an end-of-line character to the <code class="highlighter-rouge">stream</code> instanceafter converting them to strings.
</p>
<p>
This function encodes character codes in the string using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>

</div>
<div class="mb-2"><code>stream#read(bytes?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Reads specified length of data from the stream and returns a <code class="highlighter-rouge">binary</code> instance that contains it. If the argument <code class="highlighter-rouge">bytes</code> is omitted, all the data available from the stream would be read.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|buff:binary|</code>, where <code class="highlighter-rouge">buff</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>stream#readchar() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Reads one character from the stream and returns a <code class="highlighter-rouge">string</code> instance that contains it.
</p>
<p>
This method decodes character codes in the stream using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|ch:string|</code>, where <code class="highlighter-rouge">ch</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>stream#readline():[chop] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Reads one line from the stream and returns a <code class="highlighter-rouge">string</code> instance that contains it.
</p>
<p>
If the attribute <code class="highlighter-rouge">:chop</code> is specified, it would remove the last new line character from the result. This method decodes character codes in the stream using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|line:string|</code>, where <code class="highlighter-rouge">line</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>stream#readlines(nlines?:number):[chop] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that reads text from the specified stream line by line.
</p>
<p>
The argument <code class="highlighter-rouge">nlines</code> specifies how many lines should be read from the stream. If omitted, it would read all the lines.
</p>
<p>
If attribute <code class="highlighter-rouge">:chop</code> is specified, it eliminates an end-of-line character that appears at the end of each line.
</p>
<p>
This method decodes character codes in the stream using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>stream#readtext() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Reads the whole data in the stream as a text sequence and returns a <code class="highlighter-rouge">string</code> instance that contains it. This method decodes character codes in the stream using <code class="highlighter-rouge">codec</code> instance that is specified when the <code class="highlighter-rouge">stream</code> instance is created.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|text:string|</code>, where <code class="highlighter-rouge">text</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>stream#seek(offset:number, origin?:symbol):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Seeks the current file position to the offset specified by the argument <code class="highlighter-rouge">offset</code>.
</p>
<p>
The argument <code class="highlighter-rouge">origin</code> specifies the meaning of <code class="highlighter-rouge">offset</code> value as follows:
</p>
<ul>
<li><code class="highlighter-rouge">set` ... `offset` is an absolute offset from the begining of the stream.</code></li>
<li><code class="highlighter-rouge">cur` ... `offset` is a relative offset from the current position.</code></li>
</ul>
<p>
This method returns the target stream instance itself.
</p>

</div>
<div class="mb-2"><code>stream#serialize(value):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>stream#setcodec(codec:codec:nil):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Sets <code class="highlighter-rouge">codec</code> instance to the target stream. If <code class="highlighter-rouge">nil</code> is specified for the argument, the current <code class="highlighter-rouge">codec</code> instance would be removed.
</p>
<p>
This method returns the target stream instance itself.
</p>

</div>
<div class="mb-2"><code>stream#tell()</code></div>
<div class="mb-2 ml-4">
Returns the current file position at which read/write operation works.
</div>
<div class="mb-2"><code>stream#write(ptr:pointer, bytes?:number):reduce</code></div>
<div class="mb-2 ml-4">
Writes binary data pointer by <code class="highlighter-rouge">ptr</code> to the stream. The argument <code class="highlighter-rouge">bytes</code> limits the number of data that is to be written to the stream.
</div>
<h2><span class="caption-index-2">5.45</span><a name="anchor-5-45"></a>string Class</h2>
<h3><span class="caption-index-3">5.45.1</span><a name="anchor-5-45-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">string</code> class provides measures to operate on strings.
</p>
<p>
You can create a <code class="highlighter-rouge">string</code> instance by embracing a sequence of characters with a pair of single- or double-quotes.
</p>
<pre class="highlight"><code>'Hello World'

"Hello World"
</code></pre>
<p>
If you need to declare a string that contains multiple lines, embrace it with a pair of sequences of three single- or double-quotes.
</p>
<pre class="highlight"><code>R"""
first line
second line
third line
"""
</code></pre>
<h3><span class="caption-index-3">5.45.2</span><a name="anchor-5-45-2"></a>Suffix Management</h3>
<p>
When an string literal is suffixed by a character <code class="highlighter-rouge">$</code>, a handler registered by <code class="highlighter-rouge">string.translate()</code> function that is supposed to translate the string into other natural languages would be evaluated.
</p>
<h3><span class="caption-index-3">5.45.3</span><a name="anchor-5-45-3"></a>Method</h3>
<div class="mb-2"><code>string#align(width:number, padding:string =&gt; ' '):map:[center,left,right] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Align the string to the left, right or center within the specified <code class="highlighter-rouge">width</code> and returns the result.
</p>
<p>
The following attributes specify the alignment position:
</p>
<ul>
<li><code class="highlighter-rouge">:center</code> .. Aligns to the center. This is the default.</li>
<li><code class="highlighter-rouge">:left</code> .. Aligns to the left</li>
<li><code class="highlighter-rouge">:right</code> .. Aligns to the right</li>
</ul>
<p>
If the string width is narrower than the specified <code class="highlighter-rouge">width</code>, nothing would be done.
</p>
<p>
It uses a string specified by the argument <code class="highlighter-rouge">padding</code> to fill lacking spaces. If omitted, a white space is used for padding.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. A kanji-character occupies two characters in width.
</p>

</div>
<div class="mb-2"><code>string.binary() {block?}</code></div>
<div class="mb-2 ml-4">
Converts the string into <code class="highlighter-rouge">binary</code> instance.
</div>
<div class="mb-2"><code>string#capitalize() {block?}</code></div>
<div class="mb-2 ml-4">
Returns a string that capitalizes the first character.
</div>
<div class="mb-2"><code>string#chop(suffix*:string):[eol,icase] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a string that removes a last character.
</p>
<p>
If an attribute <code class="highlighter-rouge">:eol</code> is specified, only the end-of-line character shall be removed. In this case, if the end-of-line has a sequence of CR-LF, CR code shall be removed as well.
</p>

</div>
<div class="mb-2"><code>string#decodeuri() {block?}</code></div>
<div class="mb-2 ml-4">
Returns a string in which percent-encoded characters are decoded.
</div>
<div class="mb-2"><code>string#each():map:[utf32,utf8] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator generating strings of each character in the original one.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>string#eachline(nlines?:number):[chop] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator generating strings of each line in the original one.
</p>
<p>
In default, end-of-line characters are involved in the result. You can eliminates them by specifying <code class="highlighter-rouge">:chop</code> attribute.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>string#embed(dst?:stream:w):[lasteol,noindent]</code></div>
<div class="mb-2 ml-4">
<p>
Evaluates a string that contains embedded scripts and renders the result to the specified stream.
</p>
<p>
If the stream is omitted, the function returns the rendered result as a string.
</p>
<p>
Calling this method is equivalent to calling a method <code class="highlighter-rouge">string#template()</code> to create a <code class="highlighter-rouge">template</code> instance on which a method <code class="highlighter-rouge">template#render()</code> is applied afterward.
</p>

</div>
<div class="mb-2"><code>string.encode(codec:codec) {block?}</code></div>
<div class="mb-2 ml-4">
Encodes the string with the given <code class="highlighter-rouge">codec</code> and return the result as a <code class="highlighter-rouge">binary</code>.
</div>
<div class="mb-2"><code>string#encodeuri() {block?}</code></div>
<div class="mb-2 ml-4">
Returns a string in which non-URIC characters are percent-encoded.
</div>
<div class="mb-2"><code>string#endswith(suffix:string, endpos?:number):map:[icase,rest]</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the string ends with suffix.
</p>
<p>
If attribute <code class="highlighter-rouge">:rest</code> is specified, it returns the rest part if the string ends with suffix, or <code class="highlighter-rouge">nil</code> otherewise. You can specify a bottom position for the matching by an argument <code class="highlighter-rouge">endpos</code>.
</p>
<p>
With an attribute <code class="highlighter-rouge">:icase</code>, character cases are ignored while matching.
</p>

</div>
<div class="mb-2"><code>string#escapehtml():[quote] {block?}</code></div>
<div class="mb-2 ml-4">
Converts some characters into HTML entity symbols. If attribute <code class="highlighter-rouge">:quote</code> is specified, a double-quotation character would be converted to an entity symbol "&quot;".
</div>
<div class="mb-2"><code>string#find(sub:string, pos:number =&gt; 0):map:[icase,rev]</code></div>
<div class="mb-2 ml-4">
<p>
Finds a sub string from the string and returns its position.
</p>
<p>
Number of position starts from zero. You can specify a position to start finding by an argument pos. It returns nil if finding fails.
</p>
<p>
With an attribute <code class="highlighter-rouge">:icase</code>, case of characters are ignored while finding.
</p>
<p>
When an attribute <code class="highlighter-rouge">:rev</code>, finding starts from tail of the string
</p>

</div>
<div class="mb-2"><code>string#fold(len:number, step?:number):[neat] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that folds the source string by the specified length.
</p>
<p>
The argument <code class="highlighter-rouge">step</code> specifies the length of advancement for the next folding point. If omitted, it would be the same amount as <code class="highlighter-rouge">len</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>string#foldw(width:number):[padding] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that folds the source string by the specified width.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>string#format(values*):map</code></div>
<div class="mb-2 ml-4">
Taking the string instance as a printf-styled formatter string, it converts <code class="highlighter-rouge">values</code> into a string depending on formatter specifiers in it.
</div>
<div class="mb-2"><code>string#isempty()</code></div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> if the string is empty.
</div>
<div class="mb-2"><code>string#left(len?:number):map</code></div>
<div class="mb-2 ml-4">
<p>
Extracts the specified length of string from left of the source string.
</p>
<p>
If the argument is omitted, it would return whole the source string.
</p>

</div>
<div class="mb-2"><code>string#len()</code></div>
<div class="mb-2 ml-4">
Returns the length of the string in characters.
</div>
<div class="mb-2"><code>string#lower()</code></div>
<div class="mb-2 ml-4">
Converts upper-case to lower-case characters.
</div>
<div class="mb-2"><code>string#mid(pos:number, len?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Extracts the specified length of string from the position <code class="highlighter-rouge">pos</code> and returns the result.
</p>
<p>
If the argument <code class="highlighter-rouge">len</code> is omitted, it returns a string from <code class="highlighter-rouge">pos</code> to the end. The number of an argument <code class="highlighter-rouge">pos</code> starts from zero.
</p>
<p>
Below are examples:
</p>
<pre class="highlight"><code>'Hello world'.mid(3, 2) // 'lo'
'Hello world'.mid(5)    // 'world'
</code></pre>

</div>
<div class="mb-2"><code>string.print(stream?:stream:w):void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out the string to the specified <code class="highlighter-rouge">stream</code>.
</p>
<p>
If the argument is omitted, it would print to the standard output.
</p>

</div>
<div class="mb-2"><code>string.println(stream?:stream:w):void</code></div>
<div class="mb-2 ml-4">
<p>
Prints out the string and a line-break to the specified <code class="highlighter-rouge">stream</code>.
</p>
<p>
If the argument is omitted, it would print to the standard output.
</p>

</div>
<div class="mb-2"><code>string#reader() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a <code class="highlighter-rouge">stream</code> instance that reads the string content as a binary sequence.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>string#replace(match:string, sub:string, count?:number):map:[icase] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Replaces sub strings that matches the string <code class="highlighter-rouge">match</code> with a string specified by <code class="highlighter-rouge">sub</code> and returns the result.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> limits the maximum number of substitution. If omitted, there's no limit of the work.
</p>
<p>
With an attribute <code class="highlighter-rouge">:icase</code>, character cases are ignored while matching strings.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|result:string, replaced:boolean|</code>, where <code class="highlighter-rouge">result</code> is the result string and <code class="highlighter-rouge">replaced</code> indicates if there is any change between the result and its original string. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>string#replaces(map[]:string, count?:number):map:[icase] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Replaces string parts according to a list of pairs of a matching and a substituting string and returns the result.
</p>
<p>
The argument <code class="highlighter-rouge">map</code> is a <code class="highlighter-rouge">list</code> of match-substitution paris like <code class="highlighter-rouge">[match1, sub1, match2, sub2, ..]</code> with which a sub string that matches <code class="highlighter-rouge">match</code><em>n</em> would be replaced with <code class="highlighter-rouge">sub</code><em>n</em>.
</p>
<p>
The argument <code class="highlighter-rouge">count</code> limits the maximum number of substitution. If omitted, there's no limit of the work.
</p>
<p>
With an attribute <code class="highlighter-rouge">:icase</code>, character cases are ignored while matching strings.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|result:string, replaced:boolean|</code>, where <code class="highlighter-rouge">result</code> is the result string and <code class="highlighter-rouge">replaced</code> indicates if there is any change between the result and its original string. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>string#right(len?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Extracts the specified length of string from right of the source string.
</p>
<p>
If the argument is omitted, it would return whole the source string.
</p>

</div>
<div class="mb-2"><code>string#split(sep?:string, count?:number):[icase] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator generating sub strings extracted from the original one separated by a specified string <code class="highlighter-rouge">sep</code>. With an attribute <code class="highlighter-rouge">:icase</code>, character cases are ignored while finding the separator.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<div class="mb-2"><code>string#startswith(prefix:string, pos:number =&gt; 0):map:[icase,rest]</code></div>
<div class="mb-2 ml-4">
<p>
Returns <code class="highlighter-rouge">true</code> if the string starts with <code class="highlighter-rouge">prefix</code>.
</p>
<p>
If attribute <code class="highlighter-rouge">:rest</code> is specified, it returns the rest part if the string starts with prefix, or <code class="highlighter-rouge">nil</code> otherewise. You can specify a top position for the matching by an argument <code class="highlighter-rouge">pos</code>.
</p>
<p>
With an attribute <code class="highlighter-rouge">:icase</code>, character cases are ignored while matching.
</p>

</div>
<div class="mb-2"><code>string#strip():[both,left,right] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns a string that removes space characters on the left, the right or the both sides of the original string.
</p>
<p>
The following attributes would specify which side of spaces should be removed:
</p>
<ul>
<li><code class="highlighter-rouge">:both</code> .. Removes spaces on both sides. This is the default.</li>
<li><code class="highlighter-rouge">:left</code> .. Removes spaces on the left side.</li>
<li><code class="highlighter-rouge">:right</code> .. Removes spaces on the right side.</li>
</ul>

</div>
<div class="mb-2"><code>string#template():[lasteol,noindent] {block?}</code></div>
<div class="mb-2 ml-4">
Parses the content of the string as a text containing embedded scripts and returns a <code class="highlighter-rouge">template</code> instance.
</div>
<div class="mb-2"><code>string#tosymbol() {block?}</code></div>
<div class="mb-2 ml-4">
Convers the string into a symbol.
</div>
<div class="mb-2"><code>string.translator():static:void {block}</code></div>
<div class="mb-2 ml-4">
<p>
Register a procedure evaluated when a string literal appears with a suffix symbol "<code class="highlighter-rouge">$</code>", which is meant to translate the string into another language.
</p>
<p>
The procedure is described in <code class="highlighter-rouge">block</code> takes a block parameter <code class="highlighter-rouge">|str:string|</code> where <code class="highlighter-rouge">str</code> is the original string, and is expected to return a string translated from the original.
</p>

</div>
<div class="mb-2"><code>string#unescapehtml() {block?}</code></div>
<div class="mb-2 ml-4">
Converts escape sequences into readable characters.
</div>
<div class="mb-2"><code>string#upper() {block?}</code></div>
<div class="mb-2 ml-4">
Converts lower-case to upper-case characters.
</div>
<div class="mb-2"><code>string#width()</code></div>
<div class="mb-2 ml-4">
<p>
Returns the width of the string.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. For example, a kanji-character of Japanese occupies two characters in width.
</p>

</div>
<div class="mb-2"><code>string#zentohan() {block?}</code></div>
<div class="mb-2 ml-4">
Converts zenkaku to hankaku characters.
</div>
<h2><span class="caption-index-2">5.46</span><a name="anchor-5-46"></a>suffixmgr Class</h2>
<h3><span class="caption-index-3">5.46.1</span><a name="anchor-5-46-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">suffixmgr</code> class provides measures to access suffix managers that are responsible to handle suffix symbols appended to number or string literals.
</p>
<p>
Below is an example to register a suffix <code class="highlighter-rouge">X</code> that converts a string into upper case after being appended to a string literal:
</p>
<pre class="highlight"><code>suffixmgr(`string).assign(`X) {|body| body.upper()}
</code></pre>
<p>
You can use that suffix like below:
</p>
<pre class="highlight"><code>'hello world'X
</code></pre>
<h3><span class="caption-index-3">5.46.2</span><a name="anchor-5-46-2"></a>Constructor</h3>
<div class="mb-2"><code>suffixmgr(type:symbol) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a reference to one of two suffix managers, number and string.
</p>
<ul>
<li>The number suffix manager works with number literals.</li>
<li>The string suffix manager works with string literals.</li>
</ul>
<p>
Specify the argument <code class="highlighter-rouge">type</code> with a symbol <code class="highlighter-rouge">`number</code> for a number suffix manager and <code class="highlighter-rouge">`string</code> for a string suffix manager.
</p>

</div>
<h3><span class="caption-index-3">5.46.3</span><a name="anchor-5-46-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">suffixmgr</code> class has following methods:
</p>
<div class="mb-2"><code>suffixmgr#assign(suffix:symbol):void:[overwrite] {block}</code></div>
<div class="mb-2 ml-4">
<p>
Assigns a procedure to a specified symbol in the suffix manager. The procedure is provided by the <code class="highlighter-rouge">block</code> that takes a block parameter <code class="highlighter-rouge">|value|</code> where <code class="highlighter-rouge">value</code> comes from the preceded literal.
</p>
<p>
An error occurs if the same suffix symbol has already been assigned. Specifying <code class="highlighter-rouge">:overwrite</code> attribute will forcibly overwrite an existing assignment.
</p>

</div>
<h2><span class="caption-index-2">5.47</span><a name="anchor-5-47"></a>symbol Class</h2>
<h3><span class="caption-index-3">5.47.1</span><a name="anchor-5-47-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.47.2</span><a name="anchor-5-47-2"></a>Method</h3>
<p>
The <code class="highlighter-rouge">symbol</code> class has following methods:
</p>
<div class="mb-2"><code>symbol#eval(env?:environment)</code></div>
<div class="mb-2 ml-4">
Evaluate a symbol object.
</div>
<div class="mb-2"><code>symbol#len()</code></div>
<div class="mb-2 ml-4">
Returns the length of the symbol in characters.
</div>
<div class="mb-2"><code>symbol#width()</code></div>
<div class="mb-2 ml-4">
<p>
Returns the width of the symbol.
</p>
<p>
This method takes into account the character width based on the specification of East Asian Width. For example, a kanji-character of Japanese occupies two characters in width.
</p>

</div>
<h2><span class="caption-index-2">5.48</span><a name="anchor-5-48"></a>template Class</h2>
<h3><span class="caption-index-3">5.48.1</span><a name="anchor-5-48-1"></a>Overview</h3>
<h3><span class="caption-index-3">5.48.2</span><a name="anchor-5-48-2"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">template</code> instance in its argument can also take a value of <code class="highlighter-rouge">stream</code> as below:
</p>
<ul>
<li><code class="highlighter-rouge">stream</code> .. Creates a <code class="highlighter-rouge">template</code> instance by parsing the content of the stream.</li>
</ul>
<p>
As a <code class="highlighter-rouge">stream</code> is capable of being casted from <code class="highlighter-rouge">string</code> and <code class="highlighter-rouge">binary</code>, such values can also be passed to the argument that expects <code class="highlighter-rouge">template</code>.
</p>
<p>
Using the above casting feature, you can call a function <code class="highlighter-rouge">f(tmpl:template)</code> that takes a <code class="highlighter-rouge">template</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">f(template(stream('foo.txt')))</code> .. The most explicit way.</li>
<li><code class="highlighter-rouge">f(stream('foo.txt'))</code> .. Implicit casting: from <code class="highlighter-rouge">stream</code> to <code class="highlighter-rouge">template</code>.</li>
<li><code class="highlighter-rouge">f(template('foo.txt'))</code> .. Implicit casting: from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">stream</code>.</li>
<li><code class="highlighter-rouge">f('foo.txt')</code> .. Implicit casting: from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">stream</code>, then from <code class="highlighter-rouge">stream</code> to <code class="highlighter-rouge">template</code>.</li>
</ul>
<h3><span class="caption-index-3">5.48.3</span><a name="anchor-5-48-3"></a>Constructor</h3>
<div class="mb-2"><code>template(src?:stream:r):map:[lasteol,noindent] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">template</code> instance.
</p>
<p>
If the stream <code class="highlighter-rouge">src</code> is specified, the instance would be initialized with the parsed result of the script-embedded text from the stream.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code class="highlighter-rouge">:lasteol</code></li>
<li><code class="highlighter-rouge">:noindent</code></li>
</ul>

</div>
<h3><span class="caption-index-3">5.48.4</span><a name="anchor-5-48-4"></a>Method</h3>
<div class="mb-2"><code>template#parse(str:string):void:[lasteol,noindent]</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">template</code> instance by parsing a script-embedded text in a string.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code class="highlighter-rouge">:lasteol</code></li>
<li><code class="highlighter-rouge">:noindent</code></li>
</ul>

</div>
<div class="mb-2"><code>template#read(src:stream:r):void:[lasteol,noindent]</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">template</code> instance by parsing a script-embedded text from a stream.
</p>
<p>
Following attributes would customize the parser's behavior:
</p>
<ul>
<li><code class="highlighter-rouge">:lasteol</code></li>
<li><code class="highlighter-rouge">:noindent</code></li>
</ul>

</div>
<div class="mb-2"><code>template#render(dst?:stream:w)</code></div>
<div class="mb-2 ml-4">
<p>
Renders stored content to the specified stream.
</p>
<p>
If the stream is omitted, the function returns the rendered result as a string.
</p>

</div>
<h3><span class="caption-index-3">5.48.5</span><a name="anchor-5-48-5"></a>Method Called by Template Directive</h3>
<div class="mb-2"><code>template#block(symbol:symbol):void</code></div>
<div class="mb-2 ml-4">
<p>
Creates a template block which content is supposed to be replaced by a derived template.
</p>
<p>
This method is called by template directive <code class="highlighter-rouge">${=block()}</code> during both the initialization and presentation phase of a template process.
</p>
<ul>
<li><strong>Initialization:</strong> Creates a template block from the specified block that is then registered in the current template with the specified symbol.</li>
<li><strong>Presentation:</strong> Evaluates a template block registered with the specified symbol.</li>
</ul>
<p>
Consider an example. Assume that a block associated with symbol <code class="highlighter-rouge">`foo</code> is declared in a template file named <code class="highlighter-rouge">base.tmpl</code> as below:
</p>
<p>
<code class="highlighter-rouge">[base.tmpl]</code>
</p>
<pre class="highlight"><code>Block begins here.
${=block(`foo)}
Content of base.
${end}
Block ends here.
</code></pre>
<p>
This template renders the following result:
</p>
<pre class="highlight"><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
Below is another template named <code class="highlighter-rouge">derived.tmpl</code> that devies from <code class="highlighter-rouge">base.tmpl</code> and overrides the block <code class="highlighter-rouge">`foo</code>.
</p>
<p>
<code class="highlighter-rouge">[derived.tmpl]</code>
</p>
<pre class="highlight"><code>${=extends('base.tmpl')}

${=block(`foo)}
Content of derived.
${end}
</code></pre>
<p>
This template renders the following result:
</p>
<pre class="highlight"><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>

</div>
<div class="mb-2"><code>template#call(symbol:symbol, args*)</code></div>
<div class="mb-2 ml-4">
<p>
Calls a template macro that has been created by directive <code class="highlighter-rouge">${=define}</code>.
</p>
<p>
This method is called by template directive <code class="highlighter-rouge">${=call()}</code> during the presentation phase of a template process.
</p>
<p>
Below is an exemple to call a template macro:
</p>
<pre class="highlight"><code>${=call(`show_person, 'Harry', 24)}
</code></pre>
<p>
This method would return <code class="highlighter-rouge">nil</code> if a line-break character is rendered at last and would return a null string otherwise.
</p>

</div>
<div class="mb-2"><code>template#define(symbol:symbol, `args*):void</code></div>
<div class="mb-2 ml-4">
<p>
Creates a template macro from the specified block, which is supposed to be called by <code class="highlighter-rouge">${=call}</code> directive, and associates it with the specified symbol.
</p>
<p>
This method is called by template directive <code class="highlighter-rouge">${=define()}</code> during the initialization phase of a template process.
</p>
<p>
Below is an example to create a template macro:
</p>
<pre class="highlight"><code>${=define(`show_person, name:string, age:number)}
${name} is ${age} years old.
${end}
</code></pre>

</div>
<div class="mb-2"><code>template#embed(template:template)</code></div>
<div class="mb-2 ml-4">
<p>
Renders the specified template at the current position.
</p>
<p>
This method is called by template directive <code class="highlighter-rouge">${=embed()}</code> during the presentation phase of a template process.
</p>
<p>
Below is an example to embed a template file named <code class="highlighter-rouge">foo.tmpl</code>.
</p>
<pre class="highlight"><code>${=embed('foo.tmpl')}
</code></pre>
<p>
As the template rendered by this method runs in a different context from the current one, macros and blocks that it defines are not reflected to the current context.
</p>
<p>
This method would return <code class="highlighter-rouge">nil</code> if a line-break character is rendered at last and would return a null string otherwise.
</p>

</div>
<div class="mb-2"><code>template#extends(template:template):void</code></div>
<div class="mb-2 ml-4">
<p>
Declares the current template as a derived one from the specified template.
</p>
<p>
This method is called by template directive <code class="highlighter-rouge">${=extends()}</code> during the initialization phase of a template process.
</p>
<p>
The directive must appear in a template only once. An error occurs if the current template has already derived from another template.
</p>
<p>
Below is an example to declare the current template as one derived from <code class="highlighter-rouge">base.tmpl</code>.
</p>
<pre class="highlight"><code>${=extends('base.tmpl')}
</code></pre>

</div>
<div class="mb-2"><code>template#super(symbol:symbol):void</code></div>
<div class="mb-2 ml-4">
<p>
Evaluates a template block registered with the specified symbol in a template from which the current template has derived.
</p>
<p>
This method is called by template directive <code class="highlighter-rouge">${=super()}</code> during the presentation phase of a template process. The directive is intended to be used within a directive <code class="highlighter-rouge">${=block()}</code>.
</p>
<p>
Consider an example. Assume that a block associated with symbol <code class="highlighter-rouge">`foo</code> is declared in a template named <code class="highlighter-rouge">base.tmpl</code> as below:
</p>
<p>
<code class="highlighter-rouge">[base.tmpl]</code>
</p>
<pre class="highlight"><code>Block begins here.
${=block(`foo)}
Content of base.
${end}
Block ends here.
</code></pre>
<p>
This template renders the following result:
</p>
<pre class="highlight"><code>Block begins here.
Content of derived.
Block ends here.
</code></pre>
<p>
Below is another template named <code class="highlighter-rouge">derived.tmpl</code> that devies from <code class="highlighter-rouge">base.tmpl</code> and overrides the block <code class="highlighter-rouge">`foo</code>.
</p>
<p>
<code class="highlighter-rouge">[derived.tmpl]</code>
</p>
<pre class="highlight"><code>${=extends('base.tmpl')}

${=block(`foo)}
${=super(`foo)}
Content of derived.
${end}
</code></pre>
<p>
This template renders the following result:
</p>
<pre class="highlight"><code>Block begins here.
Content of base.
Content of derived.
Block ends here.
</code></pre>

</div>
<h2><span class="caption-index-2">5.49</span><a name="anchor-5-49"></a>timedelta Class</h2>
<h3><span class="caption-index-3">5.49.1</span><a name="anchor-5-49-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">timedelta</code> instance provides a time delta information that works with <code class="highlighter-rouge">datetime</code> instance. You can shift time information of <code class="highlighter-rouge">datetime</code> by applying addition or subtraction of <code class="highlighter-rouge">timedelta</code> to it.
</p>
<h3><span class="caption-index-3">5.49.2</span><a name="anchor-5-49-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">timedelta</code> instance has the following properties:
</p>
<div class="mb-2"><code>timedelta#days</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Offset of days.
</div>
<div class="mb-2"><code>timedelta#secs</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Offset of seconds.
</div>
<div class="mb-2"><code>timedelta#usecs</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
Offset of micro seconds.
</div>
<h3><span class="caption-index-3">5.49.3</span><a name="anchor-5-49-3"></a>Constructor</h3>
<div class="mb-2"><code>timedelta(days:number =&gt; 0, secs:number =&gt; 0, usecs:number =&gt; 0):map {block?}</code></div>
<div class="mb-2 ml-4">
Returns a timedelta instance with specified values. The instance actually holds properties of days, secs and usecs.
</div>
<h2><span class="caption-index-2">5.50</span><a name="anchor-5-50"></a>uri Class</h2>
<h3><span class="caption-index-3">5.50.1</span><a name="anchor-5-50-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">uri</code> instance analyzes a URI string and returns each part in it such as the scheme and path. A generic URI has the following format:
</p>
<pre class="highlight"><code>scheme:[//[user:password@]host:port]][/]path[?query][#fragment]
</code></pre>
<h3><span class="caption-index-3">5.50.2</span><a name="anchor-5-50-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">uri</code> instance has the following properties:
</p>
<div class="mb-2"><code>uri#host</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
Host part in the URI.
</div>
<div class="mb-2"><code>uri#misc</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
Misc part in the URI.
</div>
<div class="mb-2"><code>uri#password</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
Password part in the URI.
</div>
<div class="mb-2"><code>uri#port</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
Port part in the URI.
</div>
<div class="mb-2"><code>uri#scheme</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
Scheme part in the URI.
</div>
<div class="mb-2"><code>uri#urlpath</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
URL path part in the URI, which contains the path, query and fragment part.
</div>
<div class="mb-2"><code>uri#user</code> &hellip; <code>string</code> [read/write]</div>
<div class="mb-2 ml-4">
User part in the URI.
</div>
<h3><span class="caption-index-3">5.50.3</span><a name="anchor-5-50-3"></a>Constructor</h3>
<div class="mb-2"><code>uri(str?:string):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates <code class="highlighter-rouge">uri</code> instance.
</p>
<p>
If the argument <code class="highlighter-rouge">str</code> is specified, it would be parsed as a URI which is stored in the instance.
</p>
<p>
If omitted, the instance would be initialized as an empty one.
</p>

</div>
<h3><span class="caption-index-3">5.50.4</span><a name="anchor-5-50-4"></a>Method</h3>
<div class="mb-2"><code>uri#getfragment()</code></div>
<div class="mb-2 ml-4">
Returns the fragment part contained in the URI path.
</div>
<div class="mb-2"><code>uri#getpath()</code></div>
<div class="mb-2 ml-4">
Returns the path part contained in the URI path.
</div>
<div class="mb-2"><code>uri#getquery()</code></div>
<div class="mb-2 ml-4">
Returns a <code class="highlighter-rouge">dict</code> instance that is made from the query part in the URI path.
</div>
<div class="mb-2"><code>uri.parsequery(query:string):static:map</code></div>
<div class="mb-2 ml-4">
This is a utility function to parse a query string and return a <code class="highlighter-rouge">dict</code> instance that contains key-value pairs for the query.
</div>
<h3><span class="caption-index-3">5.50.5</span><a name="anchor-5-50-5"></a>Cast Operation</h3>
<p>
A function that expects a <code class="highlighter-rouge">uri</code> instance in its argument can also take a value of <code class="highlighter-rouge">string</code> that is recognized as a URI string.
</p>
<p>
With the above casting feature, you can call a function <code class="highlighter-rouge">f(uri:uri)</code> that takes a <code class="highlighter-rouge">uri</code> instance in its argument as below:
</p>
<ul>
<li><code class="highlighter-rouge">f(uri('http://example.com'))</code> .. The most explicit way.</li>
<li><code class="highlighter-rouge">f('http://example.com')</code> .. Implicit casting: from <code class="highlighter-rouge">string</code> to <code class="highlighter-rouge">uri</code>. </li>
</ul>
<h2><span class="caption-index-2">5.51</span><a name="anchor-5-51"></a>vertex Class</h2>
<h3><span class="caption-index-3">5.51.1</span><a name="anchor-5-51-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">vertex</code> class provides vertex information that consists of x, y, z and w values.
</p>
<h3><span class="caption-index-3">5.51.2</span><a name="anchor-5-51-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">vertex</code> instance has the following properties:
</p>
<div class="mb-2"><code>vertex#x</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
A value of X.
</div>
<div class="mb-2"><code>vertex#y</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
A value of Y.
</div>
<div class="mb-2"><code>vertex#z</code> &hellip; <code>number</code> [read/write]</div>
<div class="mb-2 ml-4">
A value of Z.
</div>
<h3><span class="caption-index-3">5.51.3</span><a name="anchor-5-51-3"></a>Constructor</h3>
<div class="mb-2"><code>vertex(x:number, y:number, z?:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">vertex</code> instance that has the given coordinates <code class="highlighter-rouge">x</code>, <code class="highlighter-rouge">y</code> and <code class="highlighter-rouge">z</code>. The argument <code class="highlighter-rouge">z</code> is optional and set to zero if omitted.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|v:vertex|</code>, where <code class="highlighter-rouge">v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">5.51.4</span><a name="anchor-5-51-4"></a>Method</h3>
<div class="mb-2"><code>vertex.cross (v1:vertex, v2:vertex):static:map {block?}</code></div>
<div class="mb-2 ml-4">
Calculates cross product between <code class="highlighter-rouge">v1</code> and <code class="highlighter-rouge">v2</code> and returns the result as a <code class="highlighter-rouge">vertex</code> instance.
</div>
<div class="mb-2"><code>vertex.dot(v1:vertex, v2:vertex):static:map {block?}</code></div>
<div class="mb-2 ml-4">
Calculates dot product between <code class="highlighter-rouge">v1</code> and <code class="highlighter-rouge">v2</code> and returns the result as a <code class="highlighter-rouge">number</code> instance.
</div>
<div class="mb-2"><code>vertex#list() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">list</code> that contains coordinate values <code class="highlighter-rouge">[x, y, z]</code> of the target <code class="highlighter-rouge">vertex</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|list:list|</code>, where <code class="highlighter-rouge">list</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>vertex.normal(v1:vertex, v2:vertex, v3:vertex):static:map:[unit] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Calculates a normal vector for a face that consists of three vertices given and returns it as a <code class="highlighter-rouge">vertex</code> instance.
</p>
<p>
In default, it returns a vector before being regulated to have a length of one. Specifying the attribute <code class="highlighter-rouge">:unit</code> would apply the calculation.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|v:vertex|</code>, where <code class="highlighter-rouge">v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>vertex#rotate@x(angle:number):[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">vertex</code> that is rotated from the target <code class="highlighter-rouge">vertex</code> around X-axis by the specified <code class="highlighter-rouge">angle</code> in radian. It would be rotated in a direction of tilting Y-axis toward Z-axis.
</p>
<p>
If the attribute <code class="highlighter-rouge">:deg</code> is specified, you can specify the <code class="highlighter-rouge">angle</code> in degree unit.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|v:vertex|</code>, where <code class="highlighter-rouge">v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>vertex#rotate@y(angle:number):[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">vertex</code> that is rotated from the target <code class="highlighter-rouge">vertex</code> around Y-axis by the specified <code class="highlighter-rouge">angle</code> in radian. It would be rotated in a direction of tilting Z-axis toward X-axis.
</p>
<p>
If the attribute <code class="highlighter-rouge">:deg</code> is specified, you can specify the <code class="highlighter-rouge">angle</code> in degree unit.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|v:vertex|</code>, where <code class="highlighter-rouge">v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>vertex#rotate@z(angle:number):[deg] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">vertex</code> that is rotated from the target <code class="highlighter-rouge">vertex</code> around Z-axis by the specified <code class="highlighter-rouge">angle</code> in radian. It would be rotated in a direction of tilting X-axis toward Y-axis.
</p>
<p>
If the attribute <code class="highlighter-rouge">:deg</code> is specified, you can specify the <code class="highlighter-rouge">angle</code> in degree unit.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|v:vertex|</code>, where <code class="highlighter-rouge">v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>vertex#translate(tx:number, ty:number, tz?:number) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">vertex</code> that is translated from the target <code class="highlighter-rouge">vertex</code> by the specified offsets <code class="highlighter-rouge">tx</code>, <code class="highlighter-rouge">ty</code> and <code class="highlighter-rouge">tz</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|v:vertex|</code>, where <code class="highlighter-rouge">v</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
{% endraw %}
