---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">8</span><a name="anchor-8"></a>bmp Module</h1>
<h2><span class="caption-index-2">8.1</span><a name="anchor-8-1"></a>Overview</h2>
<p>
The <code>bmp</code> module provides measures to read/write image data in Microsoft BMP format. To utilize it, import the <code>bmp</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a BMP file:
</p>
<pre><code>import(bmp)
img = image('foo.bmp')
</code></pre>
<h2><span class="caption-index-2">8.2</span><a name="anchor-8-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write BMP files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a BMP file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.bmp</code>".</li>
<li>The stream data begins with a byte sequence "<code>BM</code>".</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in BMP format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.bmp</code>".</li>
</ul>
<h2><span class="caption-index-2">8.3</span><a name="anchor-8-3"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
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
<p />

{% endraw %}
