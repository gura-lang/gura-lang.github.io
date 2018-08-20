---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-26.html#naviitem-selected
nextpage: chapter-28.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">27</span>gzip Module</h1>
<h2><span class="caption-index-2">27.1</span><a name="anchor-27-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">gzip</code> module provides measures to read/write GZIP files. To utilize it, import the <code class="highlighter-rouge">gzip</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read data from a GZIP file and write its uncompressed data to another file.
</p>
<pre class="highlight"><code>import(gzip)
gzip.reader('foo.dat.gz').copyto('foo.dat')
</code></pre>
<p>
Below is an example to read data from a file and write its compressed data to a GZIP file.
</p>
<pre class="highlight"><code>import(gzip)
gzip.writer('foo.dat.gz').copyfrom('foo.dat')
</code></pre>
<h2><span class="caption-index-2">27.2</span><a name="anchor-27-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">gzip.reader</strong></div>
<div style="margin-bottom:1em"><code>gzip.reader(stream:stream:r) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">gzip.writer</strong></div>
<div style="margin-bottom:1em"><code>gzip.writer(stream:stream:w, level?:number) {block?}</code></div>

</p>
<h2><span class="caption-index-2">27.3</span><a name="anchor-27-3"></a>Extension to stream Class</h2>
<p>
This module extends the <code class="highlighter-rouge">stream</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">stream#reader@gzip</strong></div>
<div style="margin-bottom:1em"><code>stream#reader@gzip() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">stream#writer@gzip</strong></div>
<div style="margin-bottom:1em"><code>stream#writer@gzip(level?:number) {block?}</code></div>

</p>
<h2><span class="caption-index-2">27.4</span><a name="anchor-27-4"></a>Thanks</h2>
<p>
This module uses zlib which official site is:
</p>
<p>
<a href="http://zlib.net/">http://zlib.net/</a>
</p>
{% endraw %}
