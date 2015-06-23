---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">27</span><a name="anchor-27"></a>hash Module</h1>
<p>
The <code>hash</code> module provides measures to calculate hash values of a data sequence in a stream. To utilize it, import the <code>hash</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">27.1</span><a name="anchor-27-1"></a>hash.accumulator Class</h2>
<p>
The <code>hash.accumulator</code> class provides measures to calculate hashed numbers including MD5, SHA-1 and CRC32.
</p>
<p>
As the class inhefits from <code>stream</code>, you can call methods of <code>stream</code> class with <code>hash.accumulator</code> instances.
</p>
<h3><span class="caption-index-3">27.1.1</span><a name="anchor-27-1-1"></a>Property</h3>
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
Explanation</th>
</tr>


<tr>
<td>
<code>hash.accumulator#digest</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
Returns the hashed result as <code>binary</code>.</td>
</tr>


<tr>
<td>
<code>hash.accumulator#hexdigest</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Returns the hashed result as <code>string</code> in hexadecimal format.</td>
</tr>


<tr>
<td>
<code>hash.accumulator#number</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Returns the hashed result as <code>number</code>.
This field is valid only for CRC32 and returns `nil` for other hashes.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">27.1.2</span><a name="anchor-27-1-2"></a>Constructor</h3>
<p>
<strong>hash.md5</strong>
</p>
<p>
<code>hash.md5(stream?:stream:r) {block?}</code>
</p>
<p>
Creates an <code>hash.accumulator</code> instance that calculates MD5 hashed value from the content of <code>stream</code>.
</p>
<p>
<strong>hash.sha1</strong>
</p>
<p>
<code>hash.sha1(stream?:stream:r) {block?}</code>
</p>
<p>
Creates an <code>hash.accumulator</code> instance that calculates SHA1 hashed value from the content of <code>stream</code>.
</p>
<p>
<strong>hash.crc32</strong>
</p>
<p>
<code>hash.crc32(stream?:stream:r) {block?}</code>
</p>
<p>
Creates an <code>hash.accumulator</code> instance that calculates CRC32 hashed value from the content of <code>stream</code>.
</p>
<h3><span class="caption-index-3">27.1.3</span><a name="anchor-27-1-3"></a>Method</h3>
<p>
<strong>hash.accumulator#init</strong>
</p>
<p>
<code>hash.accumulator#init():reduce</code>
</p>
<p>
Initializes the state of the accumulator.
</p>
<p>
<strong>hash.accumulator#update</strong>
</p>
<p>
<code>hash.accumulator#update(stream:stream:r):reduce</code>
</p>
<p>
Updates the accumulator with the content of <code>stream</code>.
</p>
<p />

{% endraw %}
