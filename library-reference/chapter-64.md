---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">64</span><a name="anchor-64"></a>zip Module</h1>
<h2><span class="caption-index-2">64.1</span><a name="anchor-64-1"></a>Overview</h2>
<p>
The <code>zip</code> module provides measures to read/write ZIP files.
</p>
<h2><span class="caption-index-2">64.2</span><a name="anchor-64-2"></a>zip.reader Class</h2>
<p>
The <code>zip.reader</code> class provides methods to read contents and to get information in a ZIP file through <code>stream</code> instance. An instance of <code>stream</code> class created by the methods includes a property named <code>stat</code>, a <code>zip.stat</code> instance, which provides information such as filename and created time stamp that are contained in the ZIP file.
</p>
<p>
Below is an example to list filenames in a ZIP file:
</p>
<pre><code>import(zip)
zip.reader('foo.zip') {|r|
    println(r.entries():*stat:*filename)
}
</code></pre>
<p>
Below is an example to print a content of a text file that is stored in a ZIP file:
</p>
<pre><code>import(zip)
zip.reader('foo.zip') {|r|
    print(r.entry('README.txt').readlines())
}
</code></pre>
<h3><span class="caption-index-3">64.2.1</span><a name="anchor-64-2-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">zip.reader</strong></div>
<div style="margin-bottom:1em"><code>zip.reader(stream:stream:r) {block?}</code></div>
Creates <code>zip.reader</code> instance from the specified stream.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|reader:zip.reader|</code>, where <code>reader</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">64.2.2</span><a name="anchor-64-2-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">zip.reader#entry</strong></div>
<div style="margin-bottom:1em"><code>zip.reader#entry(name:string) {block?}</code></div>
Seeks entry in the zip file that matches the specified name and returns a <code>stream</code> instance associated with the entry.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">zip.reader#entries</strong></div>
<div style="margin-bottom:1em"><code>zip.reader#entries() {block?}</code></div>
Creates an <code>iterator</code> instance that returns <code>stream</code> instances associated with each entry in the ZIP file.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">64.3</span><a name="anchor-64-3"></a>zip.writer Class</h2>
<p>
The <code>zip.writer</code> class provides methods to add entries to a ZIP file. When an instance of <code>zip.writer</code> is created, a new ZIP file would be created.
</p>
<p>
Below is an exapmple to create a ZIP archive file that contains three entries:
</p>
<pre><code>import(zip)
zip.writer('foo.zip') {|w|
    w.add('file1.txt')
    w.add('file2.txt')
    w.add('file3.txt')
    w.close()
}		
</code></pre>
<h3><span class="caption-index-3">64.3.1</span><a name="anchor-64-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">zip.writer</strong></div>
<div style="margin-bottom:1em"><code>zip.writer(stream:stream:w, compression?:symbol) {block?}</code></div>
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
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|writer:zip.writer|</code>, where <code>writer</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">64.3.2</span><a name="anchor-64-3-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">zip.writer#add</strong></div>
<div style="margin-bottom:1em"><code>zip.writer#add(stream:stream:r, filename?:string, compression?:symbol):map:reduce</code></div>
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
<div><strong style="text-decoration:underline">zip.writer#close</strong></div>
<div style="margin-bottom:1em"><code>zip.writer#close():void</code></div>
Closes the zip file after flushing cached data.
</p>
<h2><span class="caption-index-2">64.4</span><a name="anchor-64-4"></a>zip.stat Class</h2>
<p>
The <code>zip.stat</code> class provides information of entries in a ZIP file.
</p>
<h3><span class="caption-index-3">64.4.1</span><a name="anchor-64-4-1"></a>Property</h3>
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
<code>filename</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>comment</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>mtime</code></td>
<td>
<code>datetime</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>crc32</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>compression_method</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>compressed_size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>attributes</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">64.5</span><a name="anchor-64-5"></a>Thanks</h2>
<p>
This module uses zlib and bzip2 library which are distributed in the following sites:
</p>
<ul>
<li><a href="http://zlib.net/">http://zlib.net/</a></li>
<li><a href="http://www.bzip.org/">http://www.bzip.org/</a></li>
</ul>
<p />

{% endraw %}
