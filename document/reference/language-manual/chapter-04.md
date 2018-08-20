---
layout: doc-widenavi
lang: en
title: Gura Language Manual
prevpage: chapter-03.html#naviitem-selected
nextpage: chapter-05.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">4</span>Data Type</h1>
<h2><span class="caption-index-2">4.1</span><a name="anchor-4-1"></a>Overview</h2>
<p>
A value has a corresponding Data Type that defines its behavior and properties.
</p>
<p>
Each Data Type is bound with a type name, which usually appears in argument list of function call.
</p>
<p>
Name spaces for Data Type are completely isolated from those for variable and function names.
</p>
<p>
As each Data Type has a one-to-one relationship with a corresponding Class, those terms have almost the same meaning within documents in many cases.
</p>
<p>
Data types are categorized into two types: <strong>Primitive Data Type</strong> and <strong>Object Data Type</strong>.
</p>
<p>
A value of Primitive Data Type holds its content in as small memory as possible. It doesn't include any Environment in it and doesn't have any methods with side effects. Among them are <code class="highlighter-rouge">nil</code>, <code class="highlighter-rouge">boolean</code>, <code class="highlighter-rouge">complex</code>, <code class="highlighter-rouge">number</code>, <code class="highlighter-rouge">rational</code>, <code class="highlighter-rouge">string</code> and <code class="highlighter-rouge">symbol</code> types.
</p>
<p>
A value of Object Data Type owns Object data that is a sort of Environment, which allows operations with side effects. Most Data Types except for what are picked up as Primitive Data Types above belong to this.
</p>
<h2><span class="caption-index-2">4.2</span><a name="anchor-4-2"></a>Primitive Data Types</h2>
<p>
Below is a list of Primitve Data Types, which also shows one of the typical ways to instantiate values of each type.
</p>
<ul>
<li><p>
<code class="highlighter-rouge">nil</code>
</p>
<p>
A value of <code class="highlighter-rouge">nil</code> type is used to indicate an invalid result or status. It is often used as a returned value of a function when it fails its expected work. A variable <code class="highlighter-rouge">nil</code> has a value of nil type.
</p>
<pre class="highlight"><code>nil
</code></pre>
<p>
Since <code class="highlighter-rouge">nil</code> is the only instance of <code class="highlighter-rouge">nil</code> type, the term <code class="highlighter-rouge">nil</code> can both mean the name of the value and its type.
</p>
</li>
<li><p>
<code class="highlighter-rouge">boolean</code>
</p>
<p>
Values of <code class="highlighter-rouge">boolean</code> type are used to determine whether something is in a true or a false state. Variables named <code class="highlighter-rouge">true</code> and <code class="highlighter-rouge">false</code> are assigned with a true value and a false value respectively.
</p>
<pre class="highlight"><code>true  false
</code></pre>
<p>
In a function like <code class="highlighter-rouge">if</code> having arguments to check true/false condition and in a logical calculation, <code class="highlighter-rouge">false</code> and <code class="highlighter-rouge">nil</code> only are determined as a false state while other values are treated as a true state. Note that a zero value of <code class="highlighter-rouge">number</code> type is recognized as a true, not a false.
</p>
</li>
<li><p>
<code class="highlighter-rouge">complex</code>
</p>
<p>
A number literal suffixed by <code class="highlighter-rouge">j</code> instantiates a value of <code class="highlighter-rouge">complex</code> type that represents a complex number.
</p>
<pre class="highlight"><code>3.14j  1000j  1e3j
</code></pre>
<p>
See chapter <a href="Mathematic-Functions.html">Mathematic Functions</a> for more detail.
</p>
</li>
<li><p>
<code class="highlighter-rouge">number</code>
</p>
<p>
A number literal without any suffix instantiates a value of <code class="highlighter-rouge">number</code> type.
</p>
<pre class="highlight"><code>3.14  1000  1e3  0xaabb
</code></pre>
</li>
<li><p>
<code class="highlighter-rouge">rational</code>
</p>
<p>
A number literal suffixed by <code class="highlighter-rouge">r</code> instantiates a value of <code class="highlighter-rouge">rational</code> type that represents a rational number.
</p>
<pre class="highlight"><code>3r  123r
</code></pre>
<p>
See chapter <a href="Mathematic-Functions.html">Mathematic Functions</a> for more detail.
</p>
</li>
<li><p>
<code class="highlighter-rouge">string</code>
</p>
<p>
A string literal without any suffix instantiates a value of <code class="highlighter-rouge">string</code> type.
</p>
<pre class="highlight"><code>'hello world'

R'''
message text
'''
</code></pre>
</li>
<li><p>
<code class="highlighter-rouge">symbol</code>
</p>
<p>
An identifier preceded by a back quote instantiates a value of <code class="highlighter-rouge">symbol</code> type.
</p>
<pre class="highlight"><code>`foo  `bar
</code></pre>
</li>
</ul>
<h2><span class="caption-index-2">4.3</span><a name="anchor-4-3"></a>Object Data Types Frequently Used</h2>
<h3><span class="caption-index-3">4.3.1</span><a name="anchor-4-3-1"></a>List</h3>
<p>
If one or more elements are surrounced by a pair of square brackets, it would instantiate a value of <code class="highlighter-rouge">list</code> type. Any type of value can be an element of lists.
</p>
<pre class="highlight"><code>[3, 1, 4, 1, 5, 9]
['hello', 'world', 3, 4, 5]
</code></pre>
<h3><span class="caption-index-3">4.3.2</span><a name="anchor-4-3-2"></a>Iterator</h3>
<p>
If one or more elements are surrounced by a pair of parentheses, it would instantiate a value of <code class="highlighter-rouge">iterator</code> type. Any type of value can be an element of iterators.
</p>
<pre class="highlight"><code>(3, 1, 4, 1, 5, 9)
('hello', 'world', 3, 4, 5)
</code></pre>
<p>
To create an iterator that contains only one element, be sure to put a comma afther the element like following:
</p>
<pre class="highlight"><code>(3,)
</code></pre>
<p>
An expression <code class="highlighter-rouge">(3)</code> is recognized as an ordinary value of number <code class="highlighter-rouge">3</code>.
</p>
<p>
Operator <code class="highlighter-rouge">..</code> creates an iterator that generates a sequence of numbers. An expression <code class="highlighter-rouge">x..y</code> creates an iterator that generates a sequence starting from <code class="highlighter-rouge">x</code> and being increased by one until <code class="highlighter-rouge">y</code>.
</p>
<pre class="highlight"><code>1..10
</code></pre>
<p>
An expression <code class="highlighter-rouge">x..</code> creates an iterator that generates a sequence starting from <code class="highlighter-rouge">x</code> and being increased by one indefinitely.
</p>
<pre class="highlight"><code>1..
</code></pre>
<p>
Lists and iterators are convertible to each other. For instance, a list can be converted to an iterator by using <code class="highlighter-rouge">list#each</code> method like following.
</p>
<pre class="highlight"><code>[3, 1, 4, 1, 5, 9].each()
</code></pre>
<p>
An iterator can be converted to an list by surrounding it with square brackets.
</p>
<pre class="highlight"><code>[1..10]
</code></pre>
<p>
In many cases, an iterator is generated as a value returned from a function, which represents a series of multiple results. The most commonly used function may be <code class="highlighter-rouge">readlines</code>, which creates an iterator that reads a stream and returns strings splitted by line.
</p>
<h3><span class="caption-index-3">4.3.3</span><a name="anchor-4-3-3"></a>Dictionary</h3>
<p>
<code class="highlighter-rouge">dict</code> is a dictionary that contains key-value pairs as its elements where a key is one of <code class="highlighter-rouge">number</code>, <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">symbol</code> and a value is of any type.
</p>
<p>
You can create a dictionary by surrounding key-value pairs by <code class="highlighter-rouge">%{</code> and <code class="highlighter-rouge">}</code>.
</p>
<p>
There are several ways to describe the pairs. The most recommended way is to use <code class="highlighter-rouge">=&gt;</code> operator between each key and value like following.
</p>
<pre class="highlight"><code>%{
    `symbol1 =&gt; 'value 1'
    `symbol2 =&gt; 'value 2'
    `symbol3 =&gt; 'value 3'
}
</code></pre>
<p>
A pair can also be described as a list containing a key and a value.
</p>
<pre class="highlight"><code>%{
    [`symbol1, 'value 1']
    [`symbol2, 'value 2']
    [`symbol3, 'value 3']
}
</code></pre>
<p>
You can also describe keys and values alternately in one-dimentional format.
</p>
<pre class="highlight"><code>%{
    `symbol1, 'value 1'
    `symbol2, 'value 2'
    `symbol3, 'value 3'
}
</code></pre>
<h3><span class="caption-index-3">4.3.4</span><a name="anchor-4-3-4"></a>Expression</h3>
<p>
Any expression preceded by a back quote instantiates a value of <code class="highlighter-rouge">expr</code> type.
</p>
<pre class="highlight"><code>`(x + y)  `func(x)  `{ println('hello'), x += 1 }
</code></pre>
<h3><span class="caption-index-3">4.3.5</span><a name="anchor-4-3-5"></a>Binary</h3>
<p>
A string literal preceded by <code class="highlighter-rouge">b</code> instantiates a value of <code class="highlighter-rouge">binary</code> type.
</p>
<pre class="highlight"><code>b'\x00\x01\0x02\0x03'
</code></pre>
{% endraw %}
