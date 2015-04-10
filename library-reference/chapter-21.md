---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">21</span><a name="anchor-21"></a>gzip Module</h1>
<p>
The <code>gzip</code> module provides measures to read/write GZIP files. To utilize it, import the <code>gzip</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read data from a GZIP file and write its uncompressed data to another file.
</p>
<pre><code>import(gzip)
gzip.reader('foo.dat.gz').copyto('foo.dat')
</code></pre>
<p>
Below is an example to read data from a file and write its compressed data to a GZIP file.
</p>
<pre><code>import(gzip)
gzip.writer('foo.dat.gz').copyfrom('foo.dat')
</code></pre>
<h2><span class="caption-index-2">21.1</span><a name="anchor-21-1"></a>Module Functions</h2>
<p>
<strong>gzip.reader</strong>
</p>
<p>
<code>gzip.reader(stream:stream:r) {block?}</code>
</p>
<p>
<strong>gzip.writer</strong>
</p>
<p>
<code>gzip.writer(stream:stream:w, level?:number) {block?}</code>
</p>
<h2><span class="caption-index-2">21.2</span><a name="anchor-21-2"></a>Extension to stream Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<strong>stream#reader@gzip</strong>
</p>
<p>
<code>stream#reader@gzip() {block?}</code>
</p>
<p>
<strong>stream#writer@gzip</strong>
</p>
<p>
<code>stream#writer@gzip(level?:number) {block?}</code>
</p>
<h2><span class="caption-index-2">21.3</span><a name="anchor-21-3"></a>Thanks</h2>
<p>
This module uses zlib which official site is:
</p>
<p>
<a href="http://zlib.net/">http://zlib.net/</a>
</p>
<p />

{% endraw %}
