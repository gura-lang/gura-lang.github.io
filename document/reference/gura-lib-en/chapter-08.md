---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-07.html#naviitem-selected
nextpage: chapter-09.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">8</span>bmp Module</h1>
<h2><span class="caption-index-2">8.1</span><a name="anchor-8-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">bmp</code> module provides measures to read/write image data in Microsoft BMP format. To utilize it, import the <code class="highlighter-rouge">bmp</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read a BMP file:
</p>
<pre class="highlight"><code>import(bmp)
img = image('foo.bmp')
</code></pre>
<h2><span class="caption-index-2">8.2</span><a name="anchor-8-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code class="highlighter-rouge">image()</code> and instance method <code class="highlighter-rouge">image#write()</code> so that they can read/write BMP files.
</p>
<p>
When function <code class="highlighter-rouge">image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a BMP file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.bmp</code>".</li>
<li>The stream data begins with a byte sequence "<code class="highlighter-rouge">BM</code>".</li>
</ul>
<p>
When instance method <code class="highlighter-rouge">image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in BMP format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.bmp</code>".</li>
</ul>
<h2><span class="caption-index-2">8.3</span><a name="anchor-8-3"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#read@bmp</strong></div>
<div style="margin-bottom:1em"><code>image#read@bmp(stream:stream:r):reduce</code></div>
Reads an BMP image from a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#write@bmp</strong></div>
<div style="margin-bottom:1em"><code>image#write@bmp(stream:stream:w):reduce</code></div>
Writes a BMP image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
{% endraw %}
