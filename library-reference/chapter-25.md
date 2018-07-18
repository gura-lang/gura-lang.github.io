---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">25</span><a name="anchor-25"></a>gmp Module</h1>
<h2><span class="caption-index-2">25.1</span><a name="anchor-25-1"></a>Overview</h2>
<p>
The <code>gmp</code> module provides measures to calculate numbers with multiple precision using GMP library. To utilize it, import the <code>gmp</code> module using <code>import</code> function.
</p>
<p>
It expands features of operators like addition and multiplier so that they can calculate such numbers.
</p>
<h2><span class="caption-index-2">25.2</span><a name="anchor-25-2"></a>Operator</h2>
<p>
Following tables show values types of operands and returned value for each operator:
</p>
<p>
<table>
<tr>
<td>
<code>+x</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>
</tr>

<tr>
<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>-x</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>
</tr>

<tr>
<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>~x</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>
</tr>

<tr>
<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x + y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code>gmp.mpz</code></td>

	<td>
<code>gmp.mpq</code></td>

	<td>
<code>gmp.mpf</code></td>

    <td>
<code>gmp.mpf</code></td>

	<td>
<code>gmp.mpq</code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code>gmp.mpz</code></td>

	<td>
<code>gmp.mpq</code></td>

	<td>
<code>gmp.mpf</code></td>

    <td>
<code>gmp.mpf</code></td>

	<td>
<code>gmp.mpq</code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code>gmp.mpz</code></td>

	<td>
<code>gmp.mpq</code></td>

	<td>
<code>gmp.mpf</code></td>

    <td>
<code>gmp.mpf</code></td>

	<td>
<code>gmp.mpq</code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code>gmp.mpz</code></td>

	<td>
<code>gmp.mpq</code></td>

	<td>
<code>gmp.mpf</code></td>

    <td>
<code>number</code></td>

	<td>
<code>rational</code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code>gmp.mpz</code></td>

	<td>
<code>gmp.mpq</code></td>

	<td>
<code>gmp.mpf</code></td>

    <td>
<code>rational</code></td>

	<td>
<code>rational</code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x - y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x * y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x / y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x % y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<code>x == y; x != y; x &gt; y; x &lt; y; x &gt;= y; x &lt;= y; x &lt;=&gt; y</code>
</p>
<p>
<table>
<tr>
<td>
<code>comparator</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x &amp; y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x | y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x ^ y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x &lt;&lt; y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<table>
<tr>
<td>
<code>x &gt;&gt; y</code></td>

    <td>
<code><b>gmp.mpz</b></code></td>

	<td>
<code><b>gmp.mpq</b></code></td>

	<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code><b>number</b></code></td>

	<td>
<code><b>rational</b></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpz</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpq</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>gmp.mpf</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>number</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

<tr>
<td>
<code><b>rational</b></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>

	<td>
<code></code></td>

    <td>
<code></code></td>

	<td>
<code></code></td>
</tr>

</table>

</p>
<p>
<code>x..; x .. y</code>
</p>
<h2><span class="caption-index-2">25.3</span><a name="anchor-25-3"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">gmp.gcd</strong></div>
<div style="margin-bottom:1em"><code>gmp.gcd(num1:gmp.mpz, num2:gmp.mpz):map</code></div>
Calculates the greatest common divisor, GCD, between <code>num1</code> and <code>num2</code> and returns the result as <code>gmp.mpz</code>.
</p>
<p>
<div><strong style="text-decoration:underline">gmp.lcm</strong></div>
<div style="margin-bottom:1em"><code>gmp.lcm(num1:gmp.mpz, num2:gmp.mpz):map</code></div>
Calculates the least common multiple, LCM, between <code>num1</code> and <code>num2</code> and returns the result as <code>gmp.mpz</code>.
</p>
<p>
<div><strong style="text-decoration:underline">gmp.sqrt</strong></div>
<div style="margin-bottom:1em"><code>gmp.sqrt(num):map</code></div>
Calculates the square root of <code>num</code>.
</p>
<p>
The type of the argument <code>num</code> must be <code>gmp.mpz</code>, <code>gmp.mpq</code>, <code>gmp.mpf</code> or <code>number</code>.
</p>
<h2><span class="caption-index-2">25.4</span><a name="anchor-25-4"></a>gmp.mpf Class</h2>
<h3><span class="caption-index-3">25.4.1</span><a name="anchor-25-4-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gmp.mpf</strong></div>
<div style="margin-bottom:1em"><code>gmp.mpf(value?, prec?:number):map {block?}</code></div>
Creates a <code>gmp.mpf</code> instance.
</p>
<p>
If the argument <code>value</code> is specified, it would be casted to <code>gmp.mpf</code>. Acceptable types for <code>value</code> are: <code>number</code>, <code>string</code>, <code>gmp.mpf</code>, <code>gmp.mpz</code> and <code>gmp.mpq</code>.
</p>
<p>
You can specify the precision of the number by the argument <code>prec</code>. If it's omitted, a default precision would be applied.
</p>
<h3><span class="caption-index-3">25.4.2</span><a name="anchor-25-4-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">gmp.mpf.get_default_prec</strong></div>
<div style="margin-bottom:1em"><code>gmp.mpf.get_default_prec():static</code></div>
Gets the default precision for <code>gmp.mpf</code>.
</p>
<p>
<div><strong style="text-decoration:underline">gmp.mpf.set_default_prec</strong></div>
<div style="margin-bottom:1em"><code>gmp.mpf.set_default_prec(prec:number):static:void</code></div>
Sets the default precision for <code>gmp.mpf</code>.
</p>
<h2><span class="caption-index-2">25.5</span><a name="anchor-25-5"></a>gmp.mpq Class</h2>
<h3><span class="caption-index-3">25.5.1</span><a name="anchor-25-5-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gmp.mpq</strong></div>
<div style="margin-bottom:1em"><code>gmp.mpq(numer?, denom?:number):map {block?}</code></div>
Creates a <code>gmp.mpq</code> instance.
</p>
<p>
You can call this function with one of the following form.
</p>
<ul>
<li><code>gmp.mpq(numer:number)</code></li>
<li><code>gmp.mpq(numer:number, denom:number)</code></li>
<li><code>gmp.mpq(str:string)</code></li>
<li><code>gmp.mpq(num:gmp.mpq)</code></li>
</ul>
<h3><span class="caption-index-3">25.5.2</span><a name="anchor-25-5-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">gmp.mpq#cast@mpf</strong></div>
<div style="margin-bottom:1em"><code>gmp.mpq#cast@mpf() {block?}</code></div>
Casts the value to <code>gmp.mpf</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|num:gmp.mpf|</code>, where <code>num</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">25.6</span><a name="anchor-25-6"></a>gmp.mpz Class</h2>
<h3><span class="caption-index-3">25.6.1</span><a name="anchor-25-6-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gmp.mpz</strong></div>
<div style="margin-bottom:1em"><code>gmp.mpz(value?):map {block?}</code></div>
Creates a <code>gmp.mpz</code> instance.
</p>
<p>
If the argument <code>value</code> is specified, it would be casted to <code>gmp.mpz</code>. Acceptable types for <code>value</code> are: <code>number</code>, <code>string</code>, <code>gmp.mpf</code> and <code>gmp.mpz</code>.
</p>
<h2><span class="caption-index-2">25.7</span><a name="anchor-25-7"></a>Extention to string Class</h2>
<p>
This module extends the <code>string</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">string#cast@mpf</strong></div>
<div style="margin-bottom:1em"><code>string#cast@mpf(prec?:number):map</code></div>
Casts the string to <code>gmp.mpf</code>.
</p>
<p>
You can specify the precision of the number by the argument <code>prec</code>. If it's omitted, a default precision would be applied.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|num:gmp.mpf|</code>, where <code>num</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#cast@mpq</strong></div>
<div style="margin-bottom:1em"><code>string#cast@mpq():map {block?}</code></div>
Casts the string to <code>gmp.mpq</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|num:gmp.mpq|</code>, where <code>num</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">string#cast@mpz</strong></div>
<div style="margin-bottom:1em"><code>string#cast@mpz(base?:number):map</code></div>
Casts the string to <code>gmp.mpz</code>.
</p>
<p>
You can specify the basement of the number format by the argument <code>base</code>. If it's omitted, the basement would be decided by the prefix described in the string such as "<code>0</code>" and "<code>0x</code>".
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|num:gmp.mpz|</code>, where <code>num</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">25.8</span><a name="anchor-25-8"></a>Thanks</h2>
<p>
This module uses GMP and its forked project MPIR which are distributed in the following sites:
</p>
<ul>
<li><a href="https://gmplib.org">https://gmplib.org</a></li>
<li><a href="http://www.mpir.org/">http://www.mpir.org/</a></li>
</ul>
<p />

{% endraw %}
