---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">39</span><a name="anchor-39"></a>tiff Module</h1>
<p>
The <code>tiff</code> module provides measures to read/write image data in TIFF format. To utilize it, import the <code>tiff</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a TIFF file:
</p>
<pre><code>import(tiff)
img = image('foo.tiff')
</code></pre>
<h2><span class="caption-index-2">39.1</span><a name="anchor-39-1"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write TIFF files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a TIFF file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.tif</code>" or "<code>.tiff</code>".</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in TIFF format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.tif</code>" or "<code>.tiff</code>".</li>
</ul>
<h2><span class="caption-index-2">39.2</span><a name="anchor-39-2"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<strong>image#read@tiff</strong>
</p>
<p>
<code>image#read@tiff(stream:stream:r):reduce</code>
</p>
<p>
Reads a TIFF image from a stream.
</p>
<h2><span class="caption-index-2">39.3</span><a name="anchor-39-3"></a>Thanks</h2>
<p>
This module uses libtiff which is distributed in the following site:
</p>
<p>
<a href="http://www.libtiff.org/">http://www.libtiff.org/</a>
</p>
<p />

{% endraw %}
