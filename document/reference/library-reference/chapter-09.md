---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-08.html#naviitem-selected
nextpage: chapter-10.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">9</span>bzip2 Module</h1>
<h2><span class="caption-index-2">9.1</span><a name="anchor-9-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">bzip2</code> module provices measures to read/write BZIP2 files. To utilize it, import the <code class="highlighter-rouge">bzip2</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read data from a BZIP2 file and write its uncompressed data to another file.
</p>
<pre class="highlight"><code>import(bzip2)
bzip2.reader('foo.dat.bz2').copyto('foo.dat')
</code></pre>
<p>
Below is an example to read data from a file and write its compressed data to a BZIP2 file.
</p>
<pre class="highlight"><code>import(bzip2)
bzip2.writer('foo.dat.bz2').copyfrom('foo.dat')
</code></pre>
<h2><span class="caption-index-2">9.2</span><a name="anchor-9-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">bzip2.reader</strong></div>
<div style="margin-bottom:1em"><code>bzip2.reader(stream:stream:r) {block?}</code></div>
Creates a stream instance that decompresses bzip2 data from the specified <code class="highlighter-rouge">stream</code> that has readable attribute.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|st:stream|</code>, where <code class="highlighter-rouge">st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">bzip2.writer</strong></div>
<div style="margin-bottom:1em"><code>bzip2.writer(stream:stream:w, blockSize100k?:number) {block?}</code></div>
Creates a stream instance that compresses data into bzip2 format and writes it to the specified <code class="highlighter-rouge">stream</code> that has writable attribute.
</p>
<p>
The argument <code class="highlighter-rouge">blockSize100k</code> takes a number between 1 and 9 that specifies the block size to be used for compression. The actual block size is 100000 times of this value. Nine gives the best compression but takes most memory.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|st:stream|</code>, where <code class="highlighter-rouge">st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">9.3</span><a name="anchor-9-3"></a>Extension to stream Class</h2>
<p>
This module extends the <code class="highlighter-rouge">stream</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">stream#reader@bzip2</strong></div>
<div style="margin-bottom:1em"><code>stream#reader@bzip2() {block?}</code></div>
Creates a stream instance that decompresses bzip2 data from the specified <code class="highlighter-rouge">stream</code> that has readable attribute.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|st:stream|</code>, where <code class="highlighter-rouge">st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">stream#writer@bzip2</strong></div>
<div style="margin-bottom:1em"><code>stream#writer@bzip2(blockSize100k?:number) {block?}</code></div>
Creates a stream instance that compresses data into bzip2 format and writes it to the specified <code class="highlighter-rouge">stream</code> that has writable attribute.
</p>
<p>
The argument <code class="highlighter-rouge">blockSize100k</code> takes a number between 1 and 9 that specifies the block size to be used for compression. The actual block size is 100000 times of this value. Nine gives the best compression but takes most memory.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|st:stream|</code>, where <code class="highlighter-rouge">st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">9.4</span><a name="anchor-9-4"></a>Thanks</h2>
<p>
This module uses libbzip2 which is distributed in the following site:
</p>
<p>
<a href="http://www.bzip.org/">http://www.bzip.org/</a>
</p>
{% endraw %}
