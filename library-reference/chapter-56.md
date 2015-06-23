---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">56</span><a name="anchor-56"></a>zip Module</h1>
<p>
The <code>zip</code> module provides measures to read/write ZIP files.
</p>
<p>
Below is an example to reads entries from an archive file:
</p>
<pre><code>import(zip)
zip.reader('foo.zip') {|r|
    println(r.entries():*stat:*filename)
}
</code></pre>
<p>
Below is an exapmple to create a ZIP archive file:
</p>
<pre><code>import(zip)
zip.writer('foo.zip') {|w|
    w.add('file1.txt')
    w.add('file2.txt')
    w.add('file3.txt')
    w.close()
}		
</code></pre>
<h2><span class="caption-index-2">56.1</span><a name="anchor-56-1"></a>zip.reader Class</h2>
<h3><span class="caption-index-3">56.1.1</span><a name="anchor-56-1-1"></a>Constructor</h3>
<p>
<strong>zip.reader</strong>
</p>
<p>
<code>zip.reader(stream:stream:r) {block?}</code>
</p>
<p>
Creates <code>zip.reader</code> instance from the stream.
</p>
<h3><span class="caption-index-3">56.1.2</span><a name="anchor-56-1-2"></a>Method</h3>
<p>
<strong>zip.reader#entry</strong>
</p>
<p>
<code>zip.reader#entry(name:string) {block?}</code>
</p>
<p>
Seeks entry in the zip file that matches the specified name and returns the stream instance.
</p>
<p>
<strong>zip.reader#entries</strong>
</p>
<p>
<code>zip.reader#entries() {block?}</code>
</p>
<p>
Creates an iterator that returns stream instances for each entry in the zip file.
</p>
<h2><span class="caption-index-2">56.2</span><a name="anchor-56-2"></a>zip.writer Class</h2>
<h3><span class="caption-index-3">56.2.1</span><a name="anchor-56-2-1"></a>Constructor</h3>
<p>
<strong>zip.writer</strong>
</p>
<p>
<code>zip.writer(stream:stream:w, compression?:symbol) {block?}</code>
</p>
<p>
Creates <code>zip.writer</code> instance from the stream.
</p>
<p>
Argument <code>compression</code> specifies the compression method and takes one of the following symbol.
</p>
<ul>
<li><code>`store</code></li>
<li><code>`deflate</code></li>
<li><code>`bzip2</code></li>
</ul>
<h3><span class="caption-index-3">56.2.2</span><a name="anchor-56-2-2"></a>Method</h3>
<p>
<strong>zip.writer#add</strong>
</p>
<p>
<code>zip.writer#add(stream:stream:r, filename?:string, compression?:symbol):map:reduce</code>
</p>
<p>
Reads data from <code>stream</code> and adds it to the zip file. Entry name is decided by the file name associated with the stream unless it's specified by argument <code>filename</code>.
</p>
<p>
Argument <code>compression</code> specifies the compression method and takes one of the following symbol.
</p>
<ul>
<li><code>`store</code></li>
<li><code>`deflate</code></li>
<li><code>`bzip2</code></li>
</ul>
<p>
<strong>zip.writer#close</strong>
</p>
<p>
<code>zip.writer#close():void</code>
</p>
<p>
Closes the zip file after flushing cached data.
</p>
<h2><span class="caption-index-2">56.3</span><a name="anchor-56-3"></a>Thanks</h2>
<p>
This module uses zlib and bzip2 library which are distributed in the following sites:
</p>
<ul>
<li><a href="http://zlib.net/">http://zlib.net/</a></li>
<li><a href="http://www.bzip.org/">http://www.bzip.org/</a></li>
</ul>
<p />

{% endraw %}
