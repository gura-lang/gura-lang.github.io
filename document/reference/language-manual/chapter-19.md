---
layout: doc-widenavi
lang: en
title: Gura Language Manual
prevpage: chapter-18.html#naviitem-selected
nextpage: chapter-20.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">19</span>Mathematic Functions</h1>
<p>
This section summarizes mathematic functions.
</p>
<h2><span class="caption-index-2">19.1</span><a name="anchor-19-1"></a>Complex Number</h2>
<p>
A number literal followed by suffix <code class="highlighter-rouge">j</code> becomes an imaginary part of a <code class="highlighter-rouge">complex</code> value.
</p>
<pre class="highlight"><code>&gt;&gt;&gt; (1 - 2j) * (3 + 1j)
5 - 5j
</code></pre>
<h2><span class="caption-index-2">19.2</span><a name="anchor-19-2"></a>Rational Number</h2>
<p>
A number literal followed by suffix <code class="highlighter-rouge">r</code> becomes a <code class="highlighter-rouge">rational</code> value with which you can do faction calculations.
</p>
<pre class="highlight"><code>&gt;&gt;&gt; 2 / 3r + 1 / 2r
7/6r
</code></pre>
<h2><span class="caption-index-2">19.3</span><a name="anchor-19-3"></a>Big Number</h2>
<p>
Importing <code class="highlighter-rouge">gmp</code> module would add following suffixes:
</p>
<ul>
<li>Suffix <code class="highlighter-rouge">L</code> creates a <code class="highlighter-rouge">gmp.mpz</code> or <code class="highlighter-rouge">gmp.mpf</code> instances that can calculate numbers with variable-length digits.</li>
<li>Suffix <code class="highlighter-rouge">Lr</code> creates a <code class="highlighter-rouge">gmp.mpq</code> instance that can calculate rational value with variable-length digits.</li>
</ul>
<h2><span class="caption-index-2">19.4</span><a name="anchor-19-4"></a>Differentiation Formula</h2>
<p>
When a function is declared with a body that contains math calculation, you can get a differentiation formula from it using <code class="highlighter-rouge">function#mathdiff()</code> method. Assumes that you have the following function:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; f(x) = math.sin(x ** 2)
</code></pre>
<p>
Then, you can call <code class="highlighter-rouge">function#mathdiff()</code> method for it like following:
</p>
<pre class="highlight"><code>&gt;&gt;&gt; g = f.mathdiff()
</code></pre>
<p>
The newly created function <code class="highlighter-rouge">g(x)</code> is one that does differential calculation of <code class="highlighter-rouge">f(x)</code>. You can examine what body it has by seeing <code class="highlighter-rouge">function#expr</code> property.
</p>
<pre class="highlight"><code>&gt;&gt;&gt; g.expr
`(math.cos(x ** 2) * (2 * x))
</code></pre>
<p>
The table below shows what differentiation formulas are obtained from original math functions:
</p>
<p>
<table class="table">
<tr>
<th>
Original</th>
<th>
Differentiation Forumula</th>
</tr>

<tr>
<td>
<code>x ** 2</code></td>
<td>
<code>2 * x</code></td>
</tr>

<tr>
<td>
<code>x ** 3</code></td>
<td>
<code>3 * x ** 2</code></td>
</tr>

<tr>
<td>
<code>x ** 4</code></td>
<td>
<code>4 * x ** 3</code></td>
</tr>

<tr>
<td>
<code>a ** x</code></td>
<td>
<code>math.log(a) * a ** x</code></td>
</tr>

<tr>
<td>
<code>math.sin(x)</code></td>
<td>
<code>math.cos(x)</code></td>
</tr>

<tr>
<td>
<code>math.cos(x)</code></td>
<td>
<code>-math.sin(x)</code></td>
</tr>

<tr>
<td>
<code>math.tan(x)</code></td>
<td>
<code>1 / math.cos(x) ** 2</code></td>
</tr>

<tr>
<td>
<code>math.exp(x)</code></td>
<td>
<code>math.exp(x)</code></td>
</tr>

<tr>
<td>
<code>math.log(x)</code></td>
<td>
<code>1 / x</code></td>
</tr>

<tr>
<td>
<code>math.log10(x)</code></td>
<td>
<code>1 / (x * math.log(10))</code></td>
</tr>

<tr>
<td>
<code>math.asin(x)</code></td>
<td>
<code>1 / math.sqrt(1 - x ** 2)</code></td>
</tr>

<tr>
<td>
<code>math.acos(x)</code></td>
<td>
<code>(-1) / math.sqrt(1 - x ** 2)</code></td>
</tr>

<tr>
<td>
<code>math.atan(x)</code></td>
<td>
<code>1 / (1 + x ** 2)</code></td>
</tr>

<tr>
<td>
<code>math.sqrt(x)</code></td>
<td>
<code>1 / (2 * math.sqrt(x))</code></td>
</tr>

<tr>
<td>
<code>math.sin(x) ** 2</code></td>
<td>
<code>math.cos(x) * 2 * math.sin(x)</code></td>
</tr>

<tr>
<td>
<code>math.sin(x ** 2)</code></td>
<td>
<code>math.cos(x ** 2) * (2 * x) </code></td>
</tr>

<tr>
<td>
<code>math.log(math.sin(x))</code></td>
<td>
<code>math.cos(x) / math.sin(x)</code></td>
</tr>

<tr>
<td>
<code>x ** 2 * math.sin(x)</code></td>
<td>
<code>2 * x * math.sin(x) + x ** 2 * math.cos(x)</code></td>
</tr>

<tr>
<td>
<code>math.sin(x) / (x ** 2)</code></td>
<td>
<code>(math.cos(x) * x ** 2 - math.sin(x) * (2 * x)) / (x ** 4)</code></td>
</tr>

<tr>
<td>
<code>3 ** (2 * x)</code></td>
<td>
<code>2 * math.log(3) * 3 ** (2 * x)</code></td>
</tr>

<tr>
<td>
<code>math.log(x ** 2 + 1)</code></td>
<td>
<code>2 * x / (x ** 2 + 1)</code></td>
</tr>

<tr>
<td>
<code>((x - 1) ** 2 * (x - 2) ** 3) / ((x - 5) ** 2)</code></td>
<td>
<code>(((2 * (x - 1) * (x - 2) ** 3 + (x - 1) ** 2 * (3 * (x - 2) ** 2)) * (x - 5) ** 2 - (x - 1) ** 2 * (x - 2) ** 3 * (2 * (x - 5))) / (x - 5) ** 4)</code></td>
</tr>

<tr>
<td>
<code>math.sin(2 * x - 3)</code></td>
<td>
<code>math.cos(2 * x - 3) * 2</code></td>
</tr>

<tr>
<td>
<code>math.cos(x) ** 2</code></td>
<td>
<code>-(math.sin(x) * 2 * math.cos(x))</code></td>
</tr>

<tr>
<td>
<code>(2 * x - 1) ** 3</code></td>
<td>
<code>6 * (2 * x - 1) ** 2</code></td>
</tr>

<tr>
<td>
<code>math.sqrt(x ** 2 + 2 * x + 3)</code></td>
<td>
<code>(2 * x + 2) / (2 * math.sqrt(x ** 2 + 2 * x + 3))</code></td>
</tr>

<tr>
<td>
<code>1 / x</code></td>
<td>
<code>(-1) / x ** 2</code></td>
</tr>

<tr>
<td>
<code>math.exp(x) + math.exp(-x)</code></td>
<td>
<code>math.exp(x) - math.exp(-x)</code></td>
</tr>

<tr>
<td>
<code>math.exp(x) - math.exp(-x)</code></td>
<td>
<code>math.exp(x) + math.exp(-x)</code></td>
</tr>

<tr>
<td>
<code>(math.sin(x + 2) + x + 2) * (math.sin(x + 3) + x + 3)</code></td>
<td>
<code>(math.cos(x + 2) + 1) * (math.sin(x + 3) + x + 3) + (math.sin(x + 2) + x + 2) * (math.cos(x + 3) + 1)</code></td>
</tr>

<tr>
<td>
<code>math.sin(math.sin(x ** 2 / 3))</code></td>
<td>
<code>math.cos(math.sin(x ** 2 / 3)) * (math.cos(x ** 2 / 3) * (2 * x * 3 / 9))</code></td>
</tr>

<tr>
<td>
<code>(2 * x - 1) / x ** 2</code></td>
<td>
<code>(2 * x ** 2 - (2 * x - 1) * (2 * x)) / x ** 4</code></td>
</tr>

</table>

</p>
{% endraw %}
