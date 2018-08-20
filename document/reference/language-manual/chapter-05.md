---
layout: doc-widenavi
lang: en
title: Gura Language Manual
prevpage: chapter-04.html#naviitem-selected
nextpage: chapter-06.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">5</span>Operator</h1>
<h2><span class="caption-index-2">5.1</span><a name="anchor-5-1"></a>Overview</h2>
<p>
There are three types of Operators.
</p>
<ul>
<li><strong>Prefixed Unary Operator</strong> takes an input value specified after it.</li>
<li><strong>Suffixed Unary Operator</strong> takes an input value specified before it.</li>
<li><strong>Binary Operator</strong> takes two input values specified on both sides of them.</li>
</ul>
<p>
An Operator has a table of procedures that are indexed by Data Types of given values, one Data Type indexing for Unary Operators and two Data Types for Binary Operators. For instance, operator <code class="highlighter-rouge">+</code> has a procedure to calculate between values of <code class="highlighter-rouge">number</code> and <code class="highlighter-rouge">number</code> and also a procecure beween values of <code class="highlighter-rouge">string</code> and <code class="highlighter-rouge">string</code>. These procedures are isolated each other as long as combination of the given Data Types is different.
</p>
<p>
Users can overload operators' procedures through <code class="highlighter-rouge">operator</code> instance. If combination of Data Types of the overloading procedure is the same as that of existing one, it would override the registered procedure. Otherwise, it would add a new procedure to the operator.
</p>
<h2><span class="caption-index-2">5.2</span><a name="anchor-5-2"></a>Precedence</h2>
<p>
The following table shows operators' precedence order from the lowest to the highest.
</p>
<table class="table">
<tr>
<th>
Precedence</th>
<th>
Operators</th>
</tr>
<tr>
<td>
Lower</td>
<td>
<code class="highlighter-rouge">=&gt;</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">||</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">&amp;&amp;</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">!</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">in</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">&lt;   &gt;   &lt;=   &gt;=   &lt;=&gt;   ==   !=</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">..</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">|</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">^</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">&amp;</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">&lt;&lt;   &gt;&gt;</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">+   -</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">*   /   %  ?</code></td>
</tr>
<tr>
<td>
</td>
<td>
<code class="highlighter-rouge">~</code></td>
</tr>
<tr>
<td>
Higher</td>
<td>
<code class="highlighter-rouge">**</code></td>
</tr>
</table>
<h2><span class="caption-index-2">5.3</span><a name="anchor-5-3"></a>Calculation Operators</h2>
<p>
Basically, Operators are used for mathematical and logical calculation. This subsection explains such functions of operators.
</p>
<h3><span class="caption-index-3">5.3.1</span><a name="anchor-5-3-1"></a>Prefixed Unary Operators</h3>
<p>
Operation <code class="highlighter-rouge">+x</code> returns the value of <code class="highlighter-rouge">x</code> itself.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>+number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>+complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>+rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>+array</code></td>
<td>
<code>array</code></td>
</tr>

<tr>
<td>
<code>+timedelta</code></td>
<td>
<code>timedelta</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">-x</code> returns a negaive value of <code class="highlighter-rouge">x</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>-number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>-complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>-rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>-array</code></td>
<td>
<code>array</code></td>
</tr>

<tr>
<td>
<code>-timedelta</code></td>
<td>
<code>timedelta</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">~x</code> returns a bit-inverted value of <code class="highlighter-rouge">x</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>~number</code></td>
<td>
<code>number</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">!x</code> returns a logically inverted value of <code class="highlighter-rouge">x</code> after evaluating it as a boolean value.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>!any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<h3><span class="caption-index-3">5.3.2</span><a name="anchor-5-3-2"></a>Suffixed Unary Operators</h3>
<p>
Operation <code class="highlighter-rouge">x..</code> returns an infinite iterator that starts from <code class="highlighter-rouge">x</code> and is increased by one.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number..</code></td>
<td>
<code>iterator</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x?</code> returns <code class="highlighter-rouge">false</code> if <code class="highlighter-rouge">x</code> is <code class="highlighter-rouge">false</code> or <code class="highlighter-rouge">nil</code>, and <code class="highlighter-rouge">true</code> otherwise. This operator is not affected by Implicit Mapping and returns <code class="highlighter-rouge">true</code> if <code class="highlighter-rouge">x</code> is of <code class="highlighter-rouge">list</code> or <code class="highlighter-rouge">iterator</code> type.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any?</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<h3><span class="caption-index-3">5.3.3</span><a name="anchor-5-3-3"></a>Binary Operators</h3>
<p>
Operation <code class="highlighter-rouge">x + y</code> returns an added result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number + number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>number + complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>number + rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>complex + number</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex + complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex + rational</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational + number</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>rational + complex</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational + rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>array + array</code></td>
<td>
<code>array</code></td>
</tr>

<tr>
<td>
<code>datetime + timedelta</code></td>
<td>
<code>datetime</code></td>
</tr>

<tr>
<td>
<code>timedelta + datetime</code></td>
<td>
<code>datetime</code></td>
</tr>

<tr>
<td>
<code>timedelta + timedelta</code></td>
<td>
<code>timedelta</code></td>
</tr>

</table>

</p>
<p>
If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">string</code> or <code class="highlighter-rouge">binary</code> type, Operation <code class="highlighter-rouge">x + y</code> returns concatenated result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>string + string</code></td>
<td>
<code>string</code></td>
</tr>

<tr>
<td>
<code>binary + binary</code></td>
<td>
<code>binary</code></td>
</tr>

<tr>
<td>
<code>string + binary</code></td>
<td>
<code>binary</code></td>
</tr>

<tr>
<td>
<code>binary + string</code></td>
<td>
<code>binary</code></td>
</tr>

<tr>
<td>
<code>string + any</code></td>
<td>
<code>string</code> (`any` will be converted to `string` before concatenation)</td>
</tr>

<tr>
<td>
<code>any + string</code></td>
<td>
<code>string</code> (`any` will be converted to `string` before concatenation)</td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x - y</code> returns a subtracted result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number - number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>number - complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>number - rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>complex - number</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex - complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex - rational</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational - number</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>rational - complex</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational - rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>array - array</code></td>
<td>
<code>array</code></td>
</tr>

<tr>
<td>
<code>datetime - timedelta</code></td>
<td>
<code>datetime</code></td>
</tr>

<tr>
<td>
<code>datetime - datetime</code></td>
<td>
<code>timedelta</code></td>
</tr>

<tr>
<td>
<code>timedelta - timedelta</code></td>
<td>
<code>timedelta</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x * y</code> returns a multiplied result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number * number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>number * complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>number * rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>complex * number</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex * complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex * rational</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational * number</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>rational * complex</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational * rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>array * array</code></td>
<td>
<code>array</code></td>
</tr>

<tr>
<td>
<code>timedelta * number</code></td>
<td>
<code>timedelta</code></td>
</tr>

<tr>
<td>
<code>number * timedelta</code></td>
<td>
<code>timedelta</code></td>
</tr>

</table>

</p>
<p>
Applying <code class="highlighter-rouge">*</code> operator between <code class="highlighter-rouge">string</code>/<code class="highlighter-rouge">binary</code> and <code class="highlighter-rouge">number</code> will join the <code class="highlighter-rouge">string</code>/<code class="highlighter-rouge">binary</code> for <code class="highlighter-rouge">number</code> times.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>string * number</code></td>
<td>
<code>string</code></td>
</tr>

<tr>
<td>
<code>number * string</code></td>
<td>
<code>string</code></td>
</tr>

<tr>
<td>
<code>binary * number</code></td>
<td>
<code>binary</code></td>
</tr>

<tr>
<td>
<code>number * binary</code></td>
<td>
<code>binary</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x / y</code> returns a divided result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number / number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>number / complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>number / rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>complex / number</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex / complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex / rational</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational / number</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>rational / complex</code></td>
<td>
(error)</td>
</tr>

<tr>
<td>
<code>rational / rational</code></td>
<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code>array / array</code></td>
<td>
<code>array</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x % y</code> returns a remainder after dividing <code class="highlighter-rouge">x</code> by <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number % number</code></td>
<td>
<code>number</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x ** y</code> returns a powered result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number ** number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>number ** complex</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex ** number</code></td>
<td>
<code>complex</code></td>
</tr>

<tr>
<td>
<code>complex ** complex</code></td>
<td>
<code>complex</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x == y</code> returns <code class="highlighter-rouge">true</code> when <code class="highlighter-rouge">x</code> equals to <code class="highlighter-rouge">y</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any == any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &lt; y</code> returns <code class="highlighter-rouge">true</code> when <code class="highlighter-rouge">x</code> is less than <code class="highlighter-rouge">y</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any &lt; any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &gt; y</code> returns <code class="highlighter-rouge">true</code> when <code class="highlighter-rouge">x</code> is greater than <code class="highlighter-rouge">y</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any &gt; any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &lt;= y</code> returns <code class="highlighter-rouge">true</code> when <code class="highlighter-rouge">x</code> is less than or equal to <code class="highlighter-rouge">y</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any &lt;= any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &gt;= y</code> returns <code class="highlighter-rouge">true</code> when <code class="highlighter-rouge">x</code> is greater than or equal to <code class="highlighter-rouge">y</code>, and <code class="highlighter-rouge">false</code> otherwise.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any &gt;= any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &lt;=&gt; y</code> returns <code class="highlighter-rouge">0</code> when <code class="highlighter-rouge">x</code> is equal to <code class="highlighter-rouge">y</code>, <code class="highlighter-rouge">-1</code> when <code class="highlighter-rouge">x</code> is less than <code class="highlighter-rouge">y</code> and <code class="highlighter-rouge">1</code> when <code class="highlighter-rouge">x</code> is greater than <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any &lt;=&gt; any</code></td>
<td>
<code>number</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x in y</code> checks if <code class="highlighter-rouge">x</code> is contained in <code class="highlighter-rouge">y</code>.
</p>
<p>
When Operator <code class="highlighter-rouge">in</code> takes a value of any type other than <code class="highlighter-rouge">list</code> and <code class="highlighter-rouge">iterator</code> at its left, it will check if the value is contained in the container specified at its right. If the right value is not of <code class="highlighter-rouge">list</code> or <code class="highlighter-rouge">iterator</code>, it would act in the same way as Operator <code class="highlighter-rouge">==</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any in list</code></td>
<td>
<code>boolean</code></td>
</tr>

<tr>
<td>
<code>any in iterator</code></td>
<td>
<code>boolean</code></td>
</tr>

<tr>
<td>
<code>any in any</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
When Operator <code class="highlighter-rouge">in</code> takes a value of <code class="highlighter-rouge">list</code> or <code class="highlighter-rouge">iterator</code> type at its left, it will check if each value of the container's element is contained in the container specified at its right, and return a list of <code class="highlighter-rouge">boolean</code> indicating the result of each containing check.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>list in list</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>list in iterator</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>list in any</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>iterator in list</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>iterator in iterator</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>iterator in any</code></td>
<td>
<code>list</code></td>
</tr>

</table>

</p>
<p>
When Operator <code class="highlighter-rouge">in</code> is used in an argument of <code class="highlighter-rouge">for()</code> and <code class="highlighter-rouge">cross()</code> function, it would work as an iterable assignment. See <a href="Flow-Control.html">Chapter.8. Flow Control</a> for detail.
</p>
<p>
Operation <code class="highlighter-rouge">x &amp; y</code> returns an AND calculation result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<ul>
<li>If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">number</code> type, it calculates bitwise AND between them.</li>
<li>If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">boolean</code> type, it calculates logical AND between them.</li>
<li>If either <code class="highlighter-rouge">x</code> or <code class="highlighter-rouge">y</code> is <code class="highlighter-rouge">nil, it returns</code>nil<code class="highlighter-rouge">.</code></li>
</ul>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number &amp; number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>boolean &amp; boolean</code></td>
<td>
<code>boolean</code></td>
</tr>

<tr>
<td>
<code>nil &amp; any</code></td>
<td>
<code>nil</code></td>
</tr>

<tr>
<td>
<code>any &amp; nil</code></td>
<td>
<code>nil</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x | y</code> returns an OR calculation result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<ul>
<li>If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">number</code> type, it calculates bitwise OR between them.</li>
<li>If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">boolean</code> type, it calculates logical OR between them.</li>
<li>If either <code class="highlighter-rouge">x</code> or <code class="highlighter-rouge">y</code> is <code class="highlighter-rouge">nil, it returns one of their values that is not</code>nil<code class="highlighter-rouge">.</code></li>
</ul>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number | number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>boolean | boolean</code></td>
<td>
<code>boolean</code></td>
</tr>

<tr>
<td>
<code>nil | any</code></td>
<td>
<code>nil</code></td>
</tr>

<tr>
<td>
<code>any | nil</code></td>
<td>
<code>nil</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x ^ y</code> returns a XOR calculation result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code>.
</p>
<ul>
<li>If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">number</code> type, it calculates bitwise XOR between them.</li>
<li>If <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> are of <code class="highlighter-rouge">boolean</code> type, it calculates logical XOR between them.</li>
</ul>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number ^ number</code></td>
<td>
<code>number</code></td>
</tr>

<tr>
<td>
<code>boolean ^ boolean</code></td>
<td>
<code>boolean</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &lt;&lt; y</code> returns a value of <code class="highlighter-rouge">x</code> shifted left by <code class="highlighter-rouge">y</code> bits.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number &lt;&lt; number</code></td>
<td>
<code>number</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &gt;&gt; y</code> returns a value of <code class="highlighter-rouge">x</code> shifted right by <code class="highlighter-rouge">y</code> bits.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number &gt;&gt; number</code></td>
<td>
<code>number</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x &amp;&amp; y</code> returns a conditional AND result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> as described below:
</p>
<ul>
<li>If <code class="highlighter-rouge">x</code> is not of <code class="highlighter-rouge">list</code> nor <code class="highlighter-rouge">iterator</code> type, it would return the value of <code class="highlighter-rouge">x</code> when <code class="highlighter-rouge">x</code> is determined as <code class="highlighter-rouge">false</code>, and return the value of <code class="highlighter-rouge">y</code> otherwise. It won't evaluate <code class="highlighter-rouge">y</code> when <code class="highlighter-rouge">x</code> comes out to be in <code class="highlighter-rouge">false</code> state.</li>
<li>If <code class="highlighter-rouge">x</code> is of <code class="highlighter-rouge">list</code> type, it applies the above operation on each value of the list's elements and returns a list containing the results.</li>
<li>If <code class="highlighter-rouge">x</code> is of <code class="highlighter-rouge">iterator</code> type, it returns an iterator that is to apply the above operation on each value of the iterator's elements.</li>
</ul>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any &amp;&amp; any</code></td>
<td>
<code>any</code></td>
</tr>

<tr>
<td>
<code>list &amp;&amp; any</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>iterator &amp;&amp; any</code></td>
<td>
<code>iterator</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x || y</code> returns a conditional OR result of <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> as described below:
</p>
<ul>
<li>If <code class="highlighter-rouge">x</code> is not of <code class="highlighter-rouge">list</code> nor <code class="highlighter-rouge">iterator</code> type, it would return the value of <code class="highlighter-rouge">x</code> when <code class="highlighter-rouge">x</code> is determined as <code class="highlighter-rouge">true</code>, and return the value of <code class="highlighter-rouge">y</code> otherwise. It won't evaluate <code class="highlighter-rouge">y</code> when <code class="highlighter-rouge">x</code> comes out to be in <code class="highlighter-rouge">true</code> state.</li>
<li>If <code class="highlighter-rouge">x</code> is of <code class="highlighter-rouge">list</code> type, it applies the above operation on each value of the list's elements and returns a list containing the results.</li>
<li>If <code class="highlighter-rouge">x</code> is of <code class="highlighter-rouge">iterator</code> type, it returns an iterator that is to apply the above operation on each value of the iterator's elements.</li>
</ul>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>any || any</code></td>
<td>
<code>any</code></td>
</tr>

<tr>
<td>
<code>list || any</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>iterator || any</code></td>
<td>
<code>iterator</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x..y</code> creates an iterator that returns <code class="highlighter-rouge">number</code> value that starts from <code class="highlighter-rouge">x</code> and is increased by one until <code class="highlighter-rouge">y</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number..number</code></td>
<td>
<code>iterator</code></td>
</tr>

</table>

</p>
<p>
Operation <code class="highlighter-rouge">x =&gt; y</code> returns a list <code class="highlighter-rouge">[x, y]</code>.
</p>
<p>
<table class="table">
<tr>
<th>
Operation</th>
<th>
Result Data Type</th>
</tr>

<tr>
<td>
<code>number =&gt; any</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>string =&gt; any</code></td>
<td>
<code>list</code></td>
</tr>

<tr>
<td>
<code>symbol =&gt; any</code></td>
<td>
<code>list</code></td>
</tr>

</table>

</p>
<p>
When Operator <code class="highlighter-rouge">=&gt;</code> is used in an argument declaration of any function definition, it would work as an assignment for a default value. And, when it is used in an argument list of any function call, it would work as a named argument. See <a href="Function.html">Chapter.7. Function</a> for their detail.
</p>
<h2><span class="caption-index-2">5.4</span><a name="anchor-5-4"></a>Other Operators</h2>
<p>
Operation <code class="highlighter-rouge">string % any</code> returns a result formatted by the string containing specifiers of <code class="highlighter-rouge">printf</code> format. The value of <code class="highlighter-rouge">any</code> must be a list if more than one argument are necessary.
</p>
<pre class="highlight"><code>'Name: %s, Age: %d' % [name, age]
</code></pre>
<p>
The code above has the same result as the following.
</p>
<pre class="highlight"><code>format('Name: %s, Age: %d', name, age)
</code></pre>
<p>
Operation <code class="highlighter-rouge">function * any</code> applies the function on <code class="highlighter-rouge">any</code>.
</p>
<p>
Operation <code class="highlighter-rouge">stream &lt;&lt; any</code> outputs <code class="highlighter-rouge">any</code> to the <code class="highlighter-rouge">stream</code>.
</p>
<pre class="highlight"><code>sys.stdout &lt;&lt; 'Hello World\n'
</code></pre>
<h2><span class="caption-index-2">5.5</span><a name="anchor-5-5"></a>Operator Overload</h2>
<p>
You can assign your own functions to operators through <code class="highlighter-rouge">operator</code> instance. The example below assings <code class="highlighter-rouge">string - string</code> operation by using <code class="highlighter-rouge">operator#assign()</code> method.
</p>
<pre class="highlight"><code>op = operator(`-)
op.assign(`string, `string) {|x, y|
    x.replace(y, '')
}
</code></pre>
<p>
After this assignment, the following code results in <code class="highlighter-rouge">'Hello, world'</code>.
</p>
<pre class="highlight"><code>'Hello, 1234world' - '1234'
</code></pre>
<p>
If you want to assign a function of a unary operator, specify one argument in <code class="highlighter-rouge">operator#assign()</code> method like below.
</p>
<pre class="highlight"><code>op = operator(`-)
op.assign(`string) {|x|
    x.each().reverse().join()
}
</code></pre>
<p>
Then, the code below has a result <code class="highlighter-rouge">'987654321'</code>.
</p>
<pre class="highlight"><code>-'123456789'
</code></pre>
<p>
You can also override existing operators.
</p>
<p>
You can use <code class="highlighter-rouge">operator#entries()</code> method to get all of the functions registered in the operator.
</p>
<pre class="highlight"><code>op = operator(`-)
println(op.entries())
</code></pre>
<p>
The method returns entries registered as binary operators. Specifying a symbol <code class="highlighter-rouge">`unary</code> as its argument would return a list of unary operators.
</p>
<pre class="highlight"><code>op = operator(`-)
println(op.entries(`unary))
</code></pre>
{% endraw %}
