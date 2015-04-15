---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">9</span><a name="anchor-9"></a>bzip2 Module</h1>
<p>
The <code>bzip2</code> module provices measures to read/write BZIP2 files. To utilize it, import the <code>bzip2</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read data from a BZIP2 file and write its uncompressed data to another file.
</p>
<pre><code>import(bzip2)
bzip2.reader('foo.dat.bz2').copyto('foo.dat')
</code></pre>
<p>
Below is an example to read data from a file and write its compressed data to a BZIP2 file.
</p>
<pre><code>import(bzip2)
bzip2.writer('foo.dat.bz2').copyfrom('foo.dat')
</code></pre>
<h2><span class="caption-index-2">9.1</span><a name="anchor-9-1"></a>Module Function</h2>
<p>
<strong>bzip2.reader</strong>
</p>
<p>
<code>bzip2.reader(stream:stream:r) {block?}</code>
</p>
<p>
Creates a stream instance that decompresses bzip2 data from the specified <code>stream</code> that has readable attribute.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|st:stream|</code>, where <code>st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>bzip2.writer</strong>
</p>
<p>
<code>bzip2.writer(stream:stream:w, blockSize100k?:number) {block?}</code>
</p>
<p>
Creates a stream instance that compresses data into bzip2 format and writes it to the specified <code>stream</code> that has writable attribute.
</p>
<p>
The argument <code>blockSize100k</code> takes a number between 1 and 9 that specifies the block size to be used for compression. The actual block size is 100000 times of this value. Nine gives the best compression but takes most memory.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|st:stream|</code>, where <code>st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">9.2</span><a name="anchor-9-2"></a>Extension to stream Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<strong>stream#reader@bzip2</strong>
</p>
<p>
<code>stream#reader@bzip2() {block?}</code>
</p>
<p>
Creates a stream instance that decompresses bzip2 data from the specified <code>stream</code> that has readable attribute.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|st:stream|</code>, where <code>st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>stream#writer@bzip2</strong>
</p>
<p>
<code>stream#writer@bzip2(blockSize100k?:number) {block?}</code>
</p>
<p>
Creates a stream instance that compresses data into bzip2 format and writes it to the specified <code>stream</code> that has writable attribute.
</p>
<p>
The argument <code>blockSize100k</code> takes a number between 1 and 9 that specifies the block size to be used for compression. The actual block size is 100000 times of this value. Nine gives the best compression but takes most memory.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|st:stream|</code>, where <code>st</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">9.3</span><a name="anchor-9-3"></a>Thanks</h2>
<p>
This module uses libbzip2 which is distributed in the following site:
</p>
<p>
<a href="http://www.bzip.org/">http://www.bzip.org/</a>
</p>
<p />

{% endraw %}