---
layout: page
lang: en
title: Gura Language Manual
---

{% raw %}
<h1><span class="caption-index-1">19</span><a name="anchor-19"></a>Mathematic Functions</h1>
<h2><span class="caption-index-2">19.1</span><a name="anchor-19-1"></a>Complex Number</h2>
<p>
suffix <code>j</code>
</p>
<h2><span class="caption-index-2">19.2</span><a name="anchor-19-2"></a>Rational Number</h2>
<p>
suffix <code>r</code>
</p>
<pre><code>4 / 7r + 3 / 10r
3 / 5r + 3 / 10r
2 / 3r - 3 / 5r
6 / 7r - 1 / 3r
</code></pre>
<h2><span class="caption-index-2">19.3</span><a name="anchor-19-3"></a>Big Number</h2>
<p>
<code>gmp</code> module
</p>
<p>
suffix <code>q</code>
</p>
<p>
suffix <code>L</code>
</p>
<h2><span class="caption-index-2">19.4</span><a name="anchor-19-4"></a>Differential</h2>
<p>
<code>function#mathdiff</code>
</p>
<pre><code>&gt;&gt;&gt; f(x) = math.sin(x ** 2)
&gt;&gt;&gt; g = f.mathdiff()
&gt;&gt;&gt; g.expr
`(math.cos(x ** 2) * (2 * x))
</code></pre>
<p>
<table>
<tr>
<th>
Function</th>
<th>
Derivative</th>
</tr>

<tr>
<td>
<pre>
x ** 2</pre>
</td>
<td>
<pre>
2 * x</pre>
</td>
</tr>

<tr>
<td>
<pre>
x ** 3</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
x ** 4</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
a ** x</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sin(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.cos(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.tan(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.exp(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.log(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.log10(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.asin(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.acos(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.atan(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sqrt(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sin(x) ** 2</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sin(x ** 2)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.log(math.sin(x))</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
x ** 2 * math.sin(x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sin(x) / (x ** 2)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
3 ** (2 * x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.log(x ** 2 + 1)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
((x - 1) ** 2 * (x - 2) ** 3) / ((x - 5) ** 2)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sin(2 * x - 3)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.cos(x) ** 2</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
(2 * x - 1) ** 3</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sqrt(x ** 2 + 2 * x + 3)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
1 / x</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.exp(x) + math.exp(-x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.exp(x) - math.exp(-x)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
(math.sin(x + 2) + x + 2) * (math.sin(x + 3) + x + 3)</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
math.sin(math.sin(x ** 2 / 3))</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

<tr>
<td>
<pre>
(2 * x - 1) / x ** 2</pre>
</td>
<td>
<pre>
</pre>
</td>
</tr>

</table>

</p>
<p />

{% endraw %}
