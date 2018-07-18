---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">46</span><a name="anchor-46"></a>png Module</h1>
<h2><span class="caption-index-2">46.1</span><a name="anchor-46-1"></a>Overview</h2>
<p>
The <code>png</code> module provides measures to read/write image data in PNG format. To utilize it, import the <code>png</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a PNG file:
</p>
<pre><code>import(png)
img = image('foo.png')
</code></pre>
<h2><span class="caption-index-2">46.2</span><a name="anchor-46-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write PNG files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a PNG file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.png</code>".</li>
<li>The stream data begins with a byte sequence "<code>\x89\x50\x4e\x47\x0d\x0a\x1a\x0a</code>".</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in PNG format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.png</code>".</li>
</ul>
<h2><span class="caption-index-2">46.3</span><a name="anchor-46-3"></a>Module Function</h2>
<h2><span class="caption-index-2">46.4</span><a name="anchor-46-4"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#read@png</strong></div>
<div style="margin-bottom:1em"><code>image#read@png(stream:stream:r):reduce</code></div>
Reads a PNG image from a stream.
</p>
<p>
<div><strong style="text-decoration:underline">image#write@png</strong></div>
<div style="margin-bottom:1em"><code>image#write@png(stream:stream:w):reduce</code></div>
Writes a PNG image to a stream.
</p>
<h2><span class="caption-index-2">46.5</span><a name="anchor-46-5"></a>Thanks</h2>
<p>
This module uses libpng library which is distributed in the following site:
</p>
<p>
<a href="http://www.libpng.org/pub/png/libpng.html">http://www.libpng.org/pub/png/libpng.html</a>
</p>
<p />

{% endraw %}
