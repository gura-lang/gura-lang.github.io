---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">5</span><a name="anchor-5"></a>Built-in Operator</h1>
<p>
<table>
<tr>
<th>
Operation</th>
<th>
Explanation</th>
</tr>

<tr>
<td>
<code>+number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+complex</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+rational</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+matrix</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+timedelta</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@char</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@uchar</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@short</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@ushort</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@long</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@ulong</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@int</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@uint</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@float</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>+array@double</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-complex</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-rational</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-matrix</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-timedelta</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@char</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@uchar</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@short</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@ushort</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-prray@long</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@ulong</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@int</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@uint</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@float</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>-array@double</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>~number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>!any</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number..</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>any?</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>any*</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number + number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number + complex</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number + rational</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>complex + number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>complex + complex</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>rational + number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>rational + rational</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>matrix + matrix</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>datetime + timedelta</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>timedelta + datetime</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>string + string</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>binary + binary</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>binary + string</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>string + binary</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>pointer + number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>string + any</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>any + string</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number - number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number - complex</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>number - rational</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>complex - number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>complex - complex</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>rational - number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>rational - rational</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>matrix - matrix</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>datetime - timedelta</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>datetime - datetime</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>timedelta - timedelta</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>color - color</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>pointer - number</code></td>
<td>
</td>
</tr>

<tr>
<td>
<code>pointer - pointer</code></td>
<td>
</td>
</tr>

</table>

</p>
<p />

{% endraw %}
