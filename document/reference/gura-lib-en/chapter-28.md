---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-27.html#naviitem-selected
nextpage: chapter-29.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">28</span>hash Module</h1>
<h2><span class="caption-index-2">28.1</span><a name="anchor-28-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">hash</code> module provides measures to calculate hash values of a data sequence in a stream. To utilize it, import the <code class="highlighter-rouge">hash</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to calculate MD5, SHA-1 and CRC32 hash values of a file named <code class="highlighter-rouge">foo.txt</code>.
</p>
<pre class="highlight"><code>import(hash)

fileName = 'foo.txt'
println('MD5: ', hash.md5(fileName).hexdigest)
println('SHA-1: ', hash.sha1(fileName).hexdigest)
println('CRC32: ', hash.crc32(fileName).hexdigest)
</code></pre>
<h2><span class="caption-index-2">28.2</span><a name="anchor-28-2"></a>hash.accumulator Class</h2>
<p>
The <code class="highlighter-rouge">hash.accumulator</code> class provides measures to calculate hashed numbers including MD5, SHA-1 and CRC32.
</p>
<p>
As the class inhefits from <code class="highlighter-rouge">stream</code>, you can call methods of <code class="highlighter-rouge">stream</code> class with <code class="highlighter-rouge">hash.accumulator</code> instances.
</p>
<h3><span class="caption-index-3">28.2.1</span><a name="anchor-28-2-1"></a>Property</h3>
<div class="mb-2"><code>stream#codec</code> &hellip; <code>codec</code> [read-only]</div>
<div class="mb-2 ml-4">
A <code class="highlighter-rouge">codec</code> instance associated with the stream.
</div>
<div class="mb-2"><code>hash.accumulator#digest</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>hash.accumulator#hexdigest</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>stream#identifier</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Identifier of the stream.
</div>
<div class="mb-2"><code>stream#name</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Name of the stream.
</div>
<div class="mb-2"><code>hash.accumulator#number</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

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
<h3><span class="caption-index-3">28.2.2</span><a name="anchor-28-2-2"></a>Constructor</h3>
<div class="mb-2"><code>hash.md5(stream?:stream:r) {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">hash.accumulator</code> instance that calculates MD5 hashed value from the content of <code class="highlighter-rouge">stream</code>.
</div>
<div class="mb-2"><code>hash.sha1(stream?:stream:r) {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">hash.accumulator</code> instance that calculates SHA1 hashed value from the content of <code class="highlighter-rouge">stream</code>.
</div>
<div class="mb-2"><code>hash.crc32(stream?:stream:r) {block?}</code></div>
<div class="mb-2 ml-4">
Creates an <code class="highlighter-rouge">hash.accumulator</code> instance that calculates CRC32 hashed value from the content of <code class="highlighter-rouge">stream</code>.
</div>
<h3><span class="caption-index-3">28.2.3</span><a name="anchor-28-2-3"></a>Method</h3>
<div class="mb-2"><code>hash.accumulator#init():reduce</code></div>
<div class="mb-2 ml-4">
Initializes the state of the accumulator.
</div>
<div class="mb-2"><code>hash.accumulator#update(stream:stream:r):reduce</code></div>
<div class="mb-2 ml-4">
Updates the accumulator with the content of <code class="highlighter-rouge">stream</code>.
</div>
{% endraw %}
